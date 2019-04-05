---
title: La gestione del caricamento di progetti in una soluzione | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0ce2f80aa50c3222797d925a888e5c004b21512d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58965506"
---
# <a name="managing-project-loading-in-a-solution"></a>Gestione del caricamento di progetti in una soluzione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Soluzioni di Visual Studio possono contenere un numero elevato di progetti. Il comportamento di Visual Studio predefinito consiste nel caricare tutti i progetti in una soluzione al momento che la soluzione è aperta e per non consentire all'utente di accedere a nessuno dei progetti finché non termina il caricamento di tutti gli elementi. Quando il processo di caricamento di progetti a lungo termine più di due minuti, viene visualizzato un indicatore di stato che mostra il numero totale di progetti e il numero di progetti caricati. L'utente può scaricare i progetti mentre si lavora in una soluzione con più progetti, ma questa procedura presenta alcuni svantaggi: i progetti non caricati non vengono compilati come parte di un comando Ricompila soluzione e le descrizioni di IntelliSense dei tipi e membri di chiusi i progetti non vengono visualizzati.  
  
 Gli sviluppatori possono ridurre i tempi di caricamento delle soluzioni e gestire il caricamento di comportamento mediante la creazione di un caricamento della soluzione responsabile del progetto. Il gestore di caricamento della soluzione può impostare il caricamento delle priorità per progetti specifici o tipi di progetto del progetto diverso, assicurarsi che i progetti vengono caricati prima di avviare una compilazione in background, ritardare il caricamento in background fino al completamento di altre attività in background ed eseguire altre attività di gestione del carico di progetto.  
  
## <a name="project-loading-priorities"></a>Il caricamento delle priorità del progetto  
 Visual Studio definisce quattro livelli di priorità di progetto diverso durante il caricamento:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority> (predefinito): quando viene aperta una soluzione, i progetti vengono caricati in modo asincrono. Se questo livello di priorità è impostata su un progetto scaricato dopo che la soluzione è già aperta, il progetto verrà caricato in corrispondenza del punto di inattività successivo.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: quando viene aperta una soluzione, i progetti vengono caricati in background, consentendo all'utente di accedere ai progetti come vengono caricati senza la necessità di attendere fino a quando non vengono caricati tutti i progetti.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: i progetti vengono caricati quando vi si accede. Un progetto avviene quando l'utente espande il nodo del progetto in Esplora soluzioni, quando viene aperto un file che appartengono al progetto quando si apre la soluzione perché è incluso nell'elenco documento aperto (persistente nel file delle opzioni utente della soluzione) o quando un altro progetto vale a dire in fase di caricamento presenta una dipendenza del progetto. Questo tipo di progetto non viene caricato automaticamente prima di avviare un processo di compilazione. il gestore di caricamento della soluzione è responsabile di garantire che tutti i progetti necessari siano stati caricati. Questi progetti dovrebbero anche essere caricati prima di avviare una ricerca/sostituzione nei file attraverso l'intera soluzione.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: i progetti non devono essere caricati a meno che l'utente lo richiede in modo esplicito. Ciò avviene quando i progetti vengono scaricati in modo esplicito.  
  
## <a name="creating-a-solution-load-manager"></a>Creazione di un caricamento della soluzione gestione  
 Gli sviluppatori possono creare un caricamento della soluzione gestione implementando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> e Visual Studio che informa che il gestore di caricamento della soluzione è attivo.  
  
#### <a name="activating-a-solution-load-manager"></a>Attivazione di un gestore di caricamento della soluzione  
 Visual Studio consente un solo gestore di caricamento di soluzioni in un determinato momento, pertanto è necessario informare Visual Studio quando si desidera attivare il caricamento della soluzione gestione. Se un secondo gestore di caricamento di soluzioni viene attivato in un secondo momento, la gestione del carico di soluzione verrà disconnesso.  
  
 È necessario ottenere il <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> del servizio e impostare il <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> proprietà:  
  
```csharp  
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;  
object objLoadMgr = this;   //the class that implements IVsSolutionManager  
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);  
```  
  
#### <a name="implementing-ivssolutionloadmanager"></a>Implementazione IVsSolutionLoadManager  
 Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnBeforeOpenProject%2A> metodo viene chiamato durante il processo di apertura della soluzione. Per implementare questo metodo, utilizzare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManagerSupport> servizio impostando la priorità di caricamento per il tipo di progetto che si desidera gestire. Ad esempio, il codice seguente imposta i tipi di progetto c# per il caricamento in background:  
  
```csharp  
Guid guidCSProjectType = new Guid("{FAE04EC0-301F-11d3-BF4B-00C04F79EFBC}");  
pSLMgrSupport.SetProjectLoadPriority(guidProjectID, (uint)_VSProjectLoadPriority.PLP_BackgroundLoad);  
```  
  
 Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> viene chiamato quando Visual Studio viene arrestato o quando un altro pacchetto diventa il gestore di caricamento di soluzione attiva chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> con il <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> proprietà.  
  
#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Strategie per diversi tipi di gestore di caricamento della soluzione  
 È possibile implementare i responsabili di caricamento di soluzioni in modi diversi, a seconda dei tipi di soluzioni che sono disponibili solo per la gestione.  
  
 Se il gestore di caricamento della soluzione è destinato a gestire il caricamento in generale della soluzione, può essere implementata come parte di un pacchetto VSPackage. Il pacchetto deve essere impostato su autoload aggiungendo il <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> nel pacchetto VSPackage con un valore di <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>. Il gestore di caricamento della soluzione può quindi essere attivato nel <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> (metodo).  
  
> [!NOTE]
>  Per altre informazioni sui pacchetti di caricamento automatico, vedere [caricamento di VSPackage](../extensibility/loading-vspackages.md).  
  
 Poiché Visual Studio riconosce solo i manager di carico soluzione ultimo da attivare, sempre gestori carico soluzione generale dovrebbero rilevare se è una gestione del carico esistente prima di attivare autonomamente. Se il chiamante GetProperty() sul servizio per soluzione <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> restituisce `null`, non vi è alcun gestore di caricamento di soluzione attiva. Se non viene restituito null, controllare se l'oggetto è quello utilizzato per la gestione del carico di soluzione.  
  
 Se il gestore di caricamento della soluzione è destinato a gestire solo alcuni tipi di soluzione, il pacchetto VSPackage può sottoscrivere gli eventi di caricamento della soluzione (chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>) e usare il gestore eventi per <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> per attivare il gestore di caricamento della soluzione.  
  
 Se il gestore di caricamento della soluzione è destinato a gestire solo le soluzioni specifiche, le informazioni di attivazione possono essere resi persistenti come parte del file della soluzione. A tale scopo, chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> per la sezione della soluzione precedente.  
  
 I responsabili di carico specifica soluzione verrà disattivato se stessi nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> gestore eventi, in ordine non sarà in conflitto con altri gestori di caricamento della soluzione.  
  
 Se è necessario un gestore di caricamento della soluzione solo per rendere persistenti le priorità di caricamento di progetti globale (ad esempio, proprietà impostate in una pagina Opzioni), è possibile attivare la gestione del carico di soluzione nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents2.OnAfterOpenProject%2A> gestore eventi, mantenere l'impostazione di proprietà della soluzione, quindi disattivare il gestore di caricamento della soluzione.  
  
## <a name="handling-solution-load-events"></a>Gestione degli eventi di caricamento di soluzioni  
 Per sottoscrivere gli eventi di caricamento della soluzione, chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> quando si attiva la gestione del carico di soluzione. Se si implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>, è possibile rispondere agli eventi che riguardano il caricamento delle priorità del progetto diverso.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Questo viene generato prima dell'apertura di una soluzione. È possibile usarlo per modificare il progetto di caricamento di priorità per i progetti nella soluzione.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Questo viene generato dopo che la soluzione è stata caricata completamente, ma prima di background viene eseguito nuovamente il caricamento del progetto. Ad esempio, un utente abbia avuto accesso un progetto la cui priorità di caricamento è LoadIfNeeded oppure il gestore di caricamento della soluzione potrebbero essere state modificate una priorità di caricamento progetto per BackgroundLoad, che avvia un caricamento in background di tale progetto.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Questo viene generato dopo che una soluzione è stata caricata inizialmente completamente, presenza o meno un gestore di caricamento della soluzione. Inoltre viene generato dopo il caricamento in background o richiesta caricato ogni volta che la soluzione diventa completamente caricata. Allo stesso tempo, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> viene riattivato.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Questo viene generato prima che il caricamento di un progetto (o i progetti). Per garantire che gli altri processi in background vengano completati prima che i progetti vengono caricati, impostare `pfShouldDelayLoadToNextIdle` al **true**.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Questo viene generato quando un batch di progetti sta per essere caricato. Se `fIsBackgroundIdleBatch` è true, i progetti devono essere caricati in background; se `fIsBackgroundIdleBatch` è false, i progetti sono da caricare in modo sincrono in seguito a una richiesta dell'utente, ad esempio se l'utente espande un progetto in Esplora soluzioni in sospeso. È possibile implementare questa opzione per eseguire operazioni costose che in caso contrario, dovrà essere eseguita in <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Questo viene generato dopo il caricamento di un batch di progetti.  
  
## <a name="detecting-and-managing-solution-and-project-loading"></a>Rilevamento e la gestione del caricamento di progetti e soluzioni  
 Per rilevare lo stato di caricamento di progetti e soluzioni, chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> con i valori seguenti:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` restituisce `true` se la soluzione e tutti i relativi progetti vengono caricati, in caso contrario `false`.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` restituisce `true` se un batch di progetti vengono attualmente caricate in background, in caso contrario `false`.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` restituisce `true` se un batch di progetti attualmente vengono caricate in modo sincrono a causa di un comando dell'utente o di altro tipo di caricamento esplicito, in caso contrario `false`.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>: `var` restituisce `true` se la soluzione attualmente viene chiuso, in caso contrario `false`.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>: `var` restituisce `true` se viene aperta una soluzione attualmente in corso, in caso contrario `false`.  
  
  È inoltre possibile garantire che i progetti e soluzioni siano state caricate (indipendentemente da quali sono le priorità di caricamento progetto), chiamando uno dei metodi seguenti:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: chiamata di questo metodo forza i progetti in una soluzione per caricare prima di eseguire il metodo restituisce.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: chiamata di questo metodo forza i progetti in `guidProject` caricare prima il metodo restituisce.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: chiamata di questo metodo forza il progetto in `guidProjectID` caricare prima il metodo restituisce.  
  
> [!NOTE]
>  . Per impostazione predefinita solo i progetti che hanno la richiesta di caricamento e vengono caricate le priorità di caricamento in background, ma se il <xref:Microsoft.VisualStudio.Shell.Interop.__VSBSLFLAGS> flag viene passato al metodo, verranno caricati tutti i progetti tranne quelli che sono contrassegnati per caricare in modo esplicito.
