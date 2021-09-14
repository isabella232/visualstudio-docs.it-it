---
title: Esposizione di eventi nel Visual Studio SDK | Microsoft Docs
description: Informazioni sui metodi Visual Studio SDK e sulle voci del Registro di sistema che espongono eventi per progetti ed elementi di progetto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- events [Visual Studio], exposing
- automation [Visual Studio SDK], exposing events
ms.assetid: 70bbc258-c221-44f8-b0d7-94087d83b8fe
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 1b99da0c049981db441c4900a242a38066fc0ffd
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709570"
---
# <a name="expose-events-in-the-visual-studio-sdk"></a>Esporre eventi in Visual Studio SDK
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] consente di creare eventi di origine usando l'automazione. È consigliabile creare eventi di origine per progetti ed elementi di progetto.

 Gli eventi vengono recuperati dai consumer di automazione <xref:EnvDTE.DTEClass.Events%2A> dall'oggetto o <xref:EnvDTE.DTEClass.GetObject%2A> (ad esempio, `GetObject("EventObjectName")` ). L'ambiente `IDispatch::Invoke` chiama usando i flag o per restituire un `DISPATCH_METHOD` `DISPATCH_PROPERTYGET` evento.

 Il processo seguente illustra come vengono restituiti gli eventi specifici di VSPackage.

1. Viene avviato l'ambiente.

2. Legge dal Registro di sistema tutti i nomi dei valori nelle chiavi **Automation**, **AutomationEvents** e **AutomationProperties** di tutti i pacchetti VSPackage e archivia tali nomi in una tabella.

3. Un consumer di automazione chiama, in questo esempio, `DTE.Events.AutomationProjectsEvents` o `DTE.Events.AutomationProjectItemsEvents` .

4. L'ambiente trova il parametro di stringa nella tabella e carica il VSPackage corrispondente.

5. L'ambiente <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> chiama il metodo usando il nome passato nella chiamata; in questo esempio, `AutomationProjectsEvents` o `AutomationProjectItemsEvents` .

6. Il pacchetto VSPackage crea un oggetto radice che dispone di metodi come `get_AutomationProjectsEvents` e e quindi restituisce un `get_AutomationProjectItemEvents` puntatore IDispatch all'oggetto.

7. L'ambiente chiama il metodo appropriato in base al nome passato nella chiamata di automazione.

8. Il metodo crea un altro oggetto evento basato su IDispatch che implementa sia l'interfaccia che l'interfaccia e `get_` `IConnectionPointContainer` restituisce un oggetto `IConnectionPoint` `IDispatchpointer` all'oggetto .

   Per esporre un evento usando l'automazione, è necessario rispondere e <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> controllare le stringhe che si aggiungono al Registro di sistema. Nell'esempio di Project basic le stringhe sono *BscProjectsEvents* e *BscProjectItemsEvents.*

## <a name="registry-entries-from-the-basic-project-sample"></a>Voci del Registro di sistema dell'esempio basic Project
 Questa sezione illustra dove aggiungere i valori degli eventi di automazione al Registro di sistema.

 **[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Packages<\\ PkgGUID \> \AutomationEvents]**

 **AutomationProjectEvents** = restituisce `AutomationProjectEvents` l'oggetto .

 **AutomationProjectItemEvents** = restituisce `AutomationProjectItemsEvents` l'oggetto .

|Nome|Tipo|Intervallo|Descrizione|
|----------|----------|-----------|-----------------|
|Impostazione predefinita (@)|REG_SZ|Non utilizzato|Non utilizzato. È possibile usare il campo dati per la documentazione.|
|*AutomationProjectsEvents*|REG_SZ|Nome dell'oggetto evento.|È rilevante solo il nome della chiave. È possibile usare il campo dati per la documentazione.<br /><br /> Questo esempio proviene dall'esempio basic Project.|
|*AutomationProjectItemEvents*|REG_SZ|Nome dell'oggetto evento|È rilevante solo il nome della chiave. È possibile usare il campo dati per la documentazione.<br /><br /> Questo esempio proviene dall'esempio basic Project.|

 Quando uno degli oggetti evento viene richiesto da un consumer di automazione, creare un oggetto radice con metodi per qualsiasi evento che il vspackage supporta. L'ambiente chiama il `get_` metodo appropriato su questo oggetto. Ad esempio, se viene chiamato , viene richiamato il metodo `DTE.Events.AutomationProjectsEvents` `get_AutomationProjectsEvents` sull'oggetto radice.

 ![Visual Studio eventi del progetto](../../extensibility/internals/media/projectevents.gif "ProjectEvents") Modello di automazione per gli eventi

 La classe `CProjectEventsContainer` rappresenta l'oggetto di origine *per BscProjectsEvents* e `CProjectItemsEventsContainer` rappresenta l'oggetto di origine per *BscProjectItemsEvents.*

 Nella maggior parte dei casi, è necessario restituire un nuovo oggetto per ogni richiesta di evento perché la maggior parte degli oggetti evento accetta un oggetto filtro. Quando si genera l'evento, controllare questo filtro per verificare che venga chiamato il gestore eventi.

 *AutomationEvents.h* e *AutomationEvents.cpp* contengono dichiarazioni e implementazioni delle classi nella tabella seguente.

|Classe|Descrizione|
|-----------|-----------------|
|`CAutomationEvents`|Implementa un oggetto radice dell'evento, recuperato `DTE.Events` dall'oggetto .|
|`CProjectsEventsContainer` e `CProjectItemsEventsContainer`|Implementare gli oggetti origine evento che generano gli eventi corrispondenti.|

 Nell'esempio di codice seguente viene illustrato come rispondere a una richiesta per un oggetto evento.

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

 Nel codice precedente è il nome della raccolta di progetti `g_wszAutomationProjects` (*FigProjects*), `g_wszAutomationProjectsEvents` (*FigProjectsEvents*) e `g_wszAutomationProjectItemsEvents` (*FigProjectItemEvents*) sono i nomi degli eventi di progetto e degli eventi degli elementi di progetto che derivano dall'implementazione del VSPackage.

 Gli oggetti evento vengono recuperati dalla stessa posizione centrale, `DTE.Events` l'oggetto . In questo modo, tutti gli oggetti evento vengono raggruppati in modo che un utente finale non deve esplorare l'intero modello a oggetti per trovare un evento specifico. In questo modo è anche possibile fornire oggetti VSPackage specifici, anziché richiedere l'implementazione di codice personalizzato per gli eventi a livello di sistema. Tuttavia, per l'utente finale, che deve trovare un evento per l'interfaccia, non è immediatamente chiaro da dove viene recuperato `ProjectItem` l'oggetto evento.

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
