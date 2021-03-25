---
title: Esposizione di eventi in Visual Studio SDK | Microsoft Docs
description: Informazioni sui metodi e le voci del registro di sistema di Visual Studio SDK che espongono eventi per progetti ed elementi di progetto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- events [Visual Studio], exposing
- automation [Visual Studio SDK], exposing events
ms.assetid: 70bbc258-c221-44f8-b0d7-94087d83b8fe
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 019efb11d7a31af875425888a1f70423bca76ca9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069803"
---
# <a name="expose-events-in-the-visual-studio-sdk"></a>Esporre eventi in Visual Studio SDK
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] consente di usare l'automazione per gli eventi di origine. Si consiglia di usare eventi di origine per progetti ed elementi di progetto.

 Gli eventi vengono recuperati dai consumer di automazione dall' <xref:EnvDTE.DTEClass.Events%2A> oggetto o <xref:EnvDTE.DTEClass.GetObject%2A> (ad esempio, `GetObject("EventObjectName")` ). L'ambiente chiama `IDispatch::Invoke` usando i `DISPATCH_METHOD` flag o `DISPATCH_PROPERTYGET` per restituire un evento.

 Il processo seguente illustra come vengono restituiti gli eventi specifici di VSPackage.

1. Viene avviato l'ambiente.

2. Esegue la lettura dal registro di sistema di tutti i nomi dei valori nelle chiavi **Automation**, **AutomationEvents** e **AutomationProperties** di tutti i pacchetti VSPackage, quindi archivia tali nomi in una tabella.

3. Un consumer di automazione chiama, in questo esempio, `DTE.Events.AutomationProjectsEvents` o `DTE.Events.AutomationProjectItemsEvents` .

4. L'ambiente trova il parametro di stringa nella tabella e carica il pacchetto VSPackage corrispondente.

5. L'ambiente chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> metodo utilizzando il nome passato nella chiamata, in questo esempio `AutomationProjectsEvents` o `AutomationProjectItemsEvents` .

6. Il pacchetto VSPackage crea un oggetto radice con metodi quali `get_AutomationProjectsEvents` e `get_AutomationProjectItemEvents` e quindi restituisce un puntatore IDispatch all'oggetto.

7. L'ambiente chiama il metodo appropriato in base al nome passato nella chiamata di automazione.

8. Il `get_` metodo crea un altro oggetto evento basato su IDispatch che implementa l' `IConnectionPointContainer` interfaccia e l' `IConnectionPoint` interfaccia e restituisce un oggetto `IDispatchpointer` all'oggetto.

   Per esporre un evento tramite l'automazione, è necessario rispondere <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> e controllare le stringhe aggiunte al registro di sistema. Nell'esempio di progetto di base le stringhe sono *BscProjectsEvents* e *BscProjectItemsEvents*.

## <a name="registry-entries-from-the-basic-project-sample"></a>Voci del registro di sistema dell'esempio di progetto di base
 Questa sezione illustra come aggiungere i valori degli eventi di automazione al registro di sistema.

 **[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Packages\\<PkgGUID \> \AutomationEvents]**

 **AutomationProjectEvents** = restituisce l' `AutomationProjectEvents` oggetto.

 **AutomationProjectItemEvents** = restituisce l' `AutomationProjectItemsEvents` oggetto.

|Nome|Tipo|Range|Descrizione|
|----------|----------|-----------|-----------------|
|Impostazione predefinita (@)|REG_SZ|Non utilizzato|Non utilizzato. È possibile usare il campo dati per la documentazione.|
|*AutomationProjectsEvents*|REG_SZ|Nome dell'oggetto evento.|Solo il nome della chiave è pertinente. È possibile usare il campo dati per la documentazione.<br /><br /> Questo esempio deriva dall'esempio di progetto di base.|
|*AutomationProjectItemEvents*|REG_SZ|Nome dell'oggetto evento|Solo il nome della chiave è pertinente. È possibile usare il campo dati per la documentazione.<br /><br /> Questo esempio deriva dall'esempio di progetto di base.|

 Quando uno degli oggetti evento viene richiesto da un consumer di automazione, creare un oggetto radice che disponga di metodi per qualsiasi evento supportato dal pacchetto VSPackage. L'ambiente chiama il `get_` metodo appropriato per questo oggetto. Se, ad esempio, `DTE.Events.AutomationProjectsEvents` viene chiamato, viene `get_AutomationProjectsEvents` richiamato il metodo sull'oggetto radice.

 ![Eventi del progetto di Visual Studio](../../extensibility/internals/media/projectevents.gif "ProjectEvents") Modello di automazione per gli eventi

 La classe `CProjectEventsContainer` rappresenta l'oggetto di origine per *BscProjectsEvents* e `CProjectItemsEventsContainer` rappresenta l'oggetto di origine per *BscProjectItemsEvents*.

 Nella maggior parte dei casi, è necessario restituire un nuovo oggetto per ogni richiesta di evento perché la maggior parte degli oggetti evento accetta un oggetto Filter. Quando si genera l'evento, controllare questo filtro per verificare che il gestore eventi venga chiamato.

 *AutomationEvents. h* e *AutomationEvents. cpp* contengono le dichiarazioni e le implementazioni delle classi nella tabella seguente.

|Classe|Descrizione|
|-----------|-----------------|
|`CAutomationEvents`|Implementa un oggetto radice evento, recuperato dall' `DTE.Events` oggetto.|
|`CProjectsEventsContainer` e `CProjectItemsEventsContainer`|Implementare gli oggetti origine evento che generano gli eventi corrispondenti.|

 Nell'esempio di codice riportato di seguito viene illustrato come rispondere a una richiesta per un oggetto evento.

```cpp
STDMETHODIMP CVsPackage::GetAutomationObject(
    /* [in]  */ LPCOLESTR       pszPropName,
    /* [out] */ IDispatch **    ppIDispatch)
{
    ExpectedPtrRet(ppIDispatch);
    *ppIDispatch = NULL;

    if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0)
        //Is the requested name our Projects object?
    {
        return GetAutomationProjects(ppIDispatch);
        // Gets our Projects object.
    }
    else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0)
        //Is the requested name our ProjectsEvents object?
    {
        return CAutomationEvents::GetAutomationEvents(ppIDispatch);
          // Gets our ProjectEvents object.
    }
    else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0)  //Is the requested name our ProjectsItemsEvents object?
    {
        return CAutomationEvents::GetAutomationEvents(ppIDispatch);
          // Gets our ProjectItemsEvents object.
    }
    return E_INVALIDARG;
}
```

 Nel codice precedente `g_wszAutomationProjects` è il nome della raccolta di progetti (*FigProjects*), `g_wszAutomationProjectsEvents` (*FigProjectsEvents*) e `g_wszAutomationProjectItemsEvents` (*FigProjectItemEvents*) sono i nomi degli eventi del progetto e degli elementi di progetto originati dall'implementazione di VSPackage.

 Gli oggetti evento vengono recuperati dalla stessa posizione centrale, ovvero l' `DTE.Events` oggetto. In questo modo, tutti gli oggetti evento vengono raggruppati in modo che un utente finale non debba esplorare l'intero modello a oggetti per trovare un evento specifico. Questo consente anche di fornire oggetti VSPackage specifici, anziché richiedere di implementare il proprio codice per gli eventi a livello di sistema. Tuttavia, per l'utente finale, che deve trovare un evento per l' `ProjectItem` interfaccia, non è immediatamente chiaro dal punto in cui viene recuperato l'oggetto evento.

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
