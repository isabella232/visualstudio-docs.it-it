---
title: Esposizione di eventi in Visual Studio SDK Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- events [Visual Studio], exposing
- automation [Visual Studio SDK], exposing events
ms.assetid: 70bbc258-c221-44f8-b0d7-94087d83b8fe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 48f1e0ea0dcd07bbc26fc89d5c61a6a5941d4727
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708493"
---
# <a name="expose-events-in-the-visual-studio-sdk"></a>Esporre eventi in Visual Studio SDKExpose events in the Visual Studio SDK
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]consente di origine degli eventi tramite l'automazione. È consigliabile ottenere eventi per progetti ed elementi di progetto.

 Gli eventi vengono recuperati <xref:EnvDTE.DTEClass.Events%2A> dai <xref:EnvDTE.DTEClass.GetObject%2A> consumer di `GetObject("EventObjectName")`automazione dall'oggetto o (ad esempio, ). L'ambiente `IDispatch::Invoke` chiama `DISPATCH_METHOD` utilizzando `DISPATCH_PROPERTYGET` i flag o per restituire un evento.

 Il processo seguente viene illustrato come vengono restituiti gli eventi specifici di VSPackage.The following process explains how VSPackage-specific events are returned.

1. Viene avviato l'ambiente.

2. Legge dal Registro di sistema tutti i nomi di valore nelle chiavi **Automation**, **AutomationEvents**e **AutomationProperties** di tutti i package VS e archivia tali nomi in una tabella.

3. Un consumer di automazione `DTE.Events.AutomationProjectsEvents` chiama, in questo esempio, o `DTE.Events.AutomationProjectItemsEvents`.

4. L'ambiente trova il parametro di stringa nella tabella e carica il pacchetto VSPackage corrispondente.

5. L'ambiente <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> chiama il metodo utilizzando il nome passato nella chiamata; in questo `AutomationProjectsEvents` esempio, o `AutomationProjectItemsEvents`.

6. Il pacchetto VSPackage crea un oggetto `get_AutomationProjectsEvents` `get_AutomationProjectItemEvents` radice che dispone di metodi quali e e quindi restituisce un IDispatch puntatore all'oggetto.

7. L'ambiente chiama il metodo appropriato in base al nome passato alla chiamata di automazione.

8. Il `get_` metodo crea un altro oggetto evento `IConnectionPointContainer` basato `IConnectionPoint` su IDispatch `IDispatchpointer` che implementa sia l'interfaccia che l'interfaccia e restituisce un oggetto.

   Per esporre un evento tramite l'automazione, è necessario rispondere <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> e controllare le stringhe aggiunte al Registro di sistema. Nell'esempio di progetto di base le stringhe sono *BscProjectsEvents* e *BscProjectItemsEvents*.

## <a name="registry-entries-from-the-basic-project-sample"></a>Voci del Registro di sistema dell'esempio di progetto di baseRegistry entries from the Basic Project sample
 In questa sezione viene illustrato dove aggiungere i valori degli eventi di automazione al Registro di sistema.

 **[HKEY_LOCAL_MACHINE SOFTWARE> MicrosoftVisualStudio 8.0\\<.\>**

 **AutomationProjectEvents** - `AutomationProjectEvents` Restituisce l'oggetto.

 **AutomationProjectItemEvents** - `AutomationProjectItemsEvents` Restituisce l'oggetto.

|Nome|Type|Range|Descrizione|
|----------|----------|-----------|-----------------|
|Predefinito (Sezione )|REG_SZ|Non utilizzato|Non utilizzato. È possibile utilizzare il campo dati per la documentazione.|
|*AutomationProjectsEvents*|REG_SZ|Nome dell'oggetto evento.|Solo il nome della chiave è rilevante. È possibile utilizzare il campo dati per la documentazione.<br /><br /> Questo esempio proviene dall'esempio di progetto di base.|
|*AutomationProjectItemEvents*|REG_SZ|Nome dell'oggetto evento|Solo il nome della chiave è rilevante. È possibile utilizzare il campo dati per la documentazione.<br /><br /> Questo esempio proviene dall'esempio di progetto di base.|

 Quando uno degli oggetti evento viene richiesto da un consumer di automazione, creare un oggetto radice che dispone di metodi per qualsiasi evento supportato dal pacchetto VSPackage.When any of your event objects are requested by a automation consumer, create a root object that has methods for any event that your VSPackage supports. L'ambiente chiama `get_` il metodo appropriato su questo oggetto. Ad esempio, `DTE.Events.AutomationProjectsEvents` se viene `get_AutomationProjectsEvents` chiamato, viene richiamato il metodo sull'oggetto radice.

 ![Eventi di progetto di Visual StudioVisual Studio project events](../../extensibility/internals/media/projectevents.gif "ProjectEvents") Modello di automazione per gli eventi

 La `CProjectEventsContainer` classe rappresenta l'oggetto di origine `CProjectItemsEventsContainer` per *BscProjectsEvents*e rappresenta l'oggetto di origine per *BscProjectItemsEvents*.

 Nella maggior parte dei casi, è necessario restituire un nuovo oggetto per ogni richiesta di evento perché la maggior parte degli oggetti evento accetta un oggetto filtro. Quando si genera l'evento, controllare questo filtro per verificare che venga chiamato il gestore eventi.

 *AutomationEvents.h* e *AutomationEvents.cpp* contengono dichiarazioni e implementazioni delle classi nella tabella seguente.

|Classe|Descrizione|
|-----------|-----------------|
|`CAutomationEvents`|Implementa un oggetto radice dell'evento, recuperato dall'oggetto. `DTE.Events`|
|`CProjectsEventsContainer` e `CProjectItemsEventsContainer`|Implementare gli oggetti origine eventi che generano gli eventi corrispondenti.|

 Esempio di codice seguente viene illustrato come rispondere a una richiesta per un oggetto evento.

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

 Nel codice precedente `g_wszAutomationProjects` è il nome della raccolta `g_wszAutomationProjectsEvents` di progetti (*FigProjects*), (*FigProjectsEvents*) e `g_wszAutomationProjectItemsEvents` (*FigProjectItemEvents*) sono i nomi degli eventi di progetto e degli eventi di progetto provenienti dall'implementazione di VSPackage.

 Gli oggetti evento vengono recuperati dalla `DTE.Events` stessa posizione centrale, l'oggetto. In questo modo, tutti gli oggetti evento vengono raggruppati in modo che un utente finale non debba esplorare l'intero modello a oggetti per trovare un evento specifico. Ciò consente anche di fornire gli oggetti VSPackage specifici, anziché richiedere di implementare il proprio codice per gli eventi a livello di sistema. Tuttavia, per l'utente finale, che `ProjectItem` deve trovare un evento per l'interfaccia, non è immediatamente chiaro da dove viene recuperato l'oggetto evento.

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
