---
title: Gestione del caricamento di progetti in una soluzione | Microsoft Docs
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
ms.openlocfilehash: a6598e2f1a178845b3ad2017716576439185379e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839383"
---
# <a name="managing-project-loading-in-a-solution"></a>Gestione del caricamento di progetti in una soluzione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le soluzioni di Visual Studio possono contenere un numero elevato di progetti. Il comportamento predefinito di Visual Studio prevede il caricamento di tutti i progetti in una soluzione nel momento in cui la soluzione viene aperta e non consente all'utente di accedere a nessuno dei progetti fino al completamento del caricamento. Quando il processo di caricamento del progetto durerà più di due minuti, viene visualizzato un indicatore di stato che mostra il numero di progetti caricati e il numero totale di progetti. L'utente può scaricare i progetti mentre lavora in una soluzione con più progetti, ma questa procedura presenta alcuni svantaggi: i progetti scaricati non vengono compilati come parte di un comando Ricompila soluzione e le descrizioni IntelliSense dei tipi e dei membri dei progetti chiusi non vengono visualizzate.  
  
 Gli sviluppatori possono ridurre i tempi di caricamento della soluzione e gestire il comportamento di caricamento dei progetti creando un gestore di caricamento della soluzione. Gestione caricamento soluzioni può impostare diverse priorità di caricamento del progetto per progetti specifici o tipi di progetto, assicurarsi che i progetti vengano caricati prima di avviare una compilazione in background, ritardare il caricamento in background fino al completamento di altre attività in background ed eseguire altre attività di gestione del caricamento del progetto.  
  
## <a name="project-loading-priorities"></a>Priorità di caricamento del progetto  
 Visual Studio definisce quattro diverse priorità di caricamento del progetto:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority> (impostazione predefinita): quando viene aperta una soluzione, i progetti vengono caricati in modo asincrono. Se questa priorità è impostata su un progetto scaricato dopo che la soluzione è già aperta, il progetto verrà caricato al punto di inattività successivo.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: quando viene aperta una soluzione, i progetti vengono caricati in background, consentendo all'utente di accedere ai progetti man mano che vengono caricati senza dover attendere fino al caricamento di tutti i progetti.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: i progetti vengono caricati quando vi si accede. Si accede a un progetto quando l'utente espande il nodo del progetto nella Esplora soluzioni, quando un file appartenente al progetto viene aperto all'apertura della soluzione perché si trova nell'elenco Apri documento (reso permanente nel file delle opzioni utente della soluzione) o quando un altro progetto da caricare presenta una dipendenza dal progetto. Questo tipo di progetto non viene caricato automaticamente prima di avviare un processo di compilazione; il gestore del caricamento della soluzione è responsabile di garantire che tutti i progetti necessari vengano caricati. Questi progetti devono essere caricati anche prima di avviare una ricerca/sostituzione nei file all'interno dell'intera soluzione.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: i progetti non devono essere caricati a meno che l'utente non lo richieda esplicitamente. Questa situazione si verifica quando i progetti vengono scaricati in modo esplicito.  
  
## <a name="creating-a-solution-load-manager"></a>Creazione di un gestore di caricamento della soluzione  
 Gli sviluppatori possono creare un gestore di caricamento della soluzione implementando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> e indicando a Visual Studio che la gestione del caricamento della soluzione è attiva.  
  
#### <a name="activating-a-solution-load-manager"></a>Attivazione di un gestore di caricamento della soluzione  
 Visual Studio consente solo un gestore di caricamento della soluzione in un determinato momento, pertanto è necessario consigliare Visual Studio quando si desidera attivare gestione caricamento soluzioni. Se un secondo gestore di caricamento della soluzione viene attivato in un secondo momento, la gestione del caricamento della soluzione verrà disconnessa.  
  
 È necessario ottenere il <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> servizio e impostare la <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> proprietà:  
  
```csharp  
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;  
object objLoadMgr = this;   //the class that implements IVsSolutionManager  
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);  
```  
  
#### <a name="implementing-ivssolutionloadmanager"></a>Implementazione di IVsSolutionLoadManager  
 Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnBeforeOpenProject%2A> metodo viene chiamato durante il processo di apertura della soluzione. Per implementare questo metodo, utilizzare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManagerSupport> servizio per impostare la priorità di caricamento per il tipo di progetto che si desidera gestire. Il codice seguente, ad esempio, imposta i tipi di progetto C# da caricare in background:  
  
```csharp  
Guid guidCSProjectType = new Guid("{FAE04EC0-301F-11d3-BF4B-00C04F79EFBC}");  
pSLMgrSupport.SetProjectLoadPriority(guidProjectID, (uint)_VSProjectLoadPriority.PLP_BackgroundLoad);  
```  
  
 Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> metodo viene chiamato quando Visual Studio viene arrestato o quando un altro pacchetto viene considerato come gestione del caricamento della soluzione attiva chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> con la <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> Proprietà.  
  
#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Strategie per diversi tipi di gestione caricamento soluzioni  
 È possibile implementare i gestori di caricamento delle soluzioni in modi diversi, a seconda dei tipi di soluzioni che devono gestire.  
  
 Se il gestore di caricamento della soluzione è progettato per gestire il caricamento di soluzioni in generale, può essere implementato come parte di un pacchetto VSPackage. Il pacchetto deve essere impostato su autoload aggiungendo l'oggetto <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> in Vspackage con un valore di <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid> . Il gestore di caricamento della soluzione può quindi essere attivato nel <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metodo.  
  
> [!NOTE]
> Per ulteriori informazioni sul caricamento di pacchetti, vedere Caricamento di pacchetti [VSPackage](../extensibility/loading-vspackages.md).  
  
 Poiché Visual Studio riconosce l'attivazione solo dell'ultimo gestore del caricamento della soluzione, i gestori di caricamento delle soluzioni generali devono sempre rilevare se è presente un gestore di carico esistente prima di attivarsi. Se la chiamata a GetProperty () nel servizio di soluzione per <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> restituisce `null` , non è presente alcun gestore di caricamento della soluzione attivo. Se non restituisce null, controllare se l'oggetto è uguale al gestore di caricamento della soluzione.  
  
 Se il gestore di caricamento della soluzione è progettato per gestire solo alcuni tipi di soluzione, il pacchetto VSPackage può sottoscrivere gli eventi di caricamento della soluzione (chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> ) e usare il gestore eventi per <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> per attivare il gestore di caricamento della soluzione.  
  
 Se il gestore di caricamento della soluzione è progettato per gestire solo soluzioni specifiche, le informazioni sull'attivazione possono essere rese permanente come parte del file di soluzione. A tale scopo, chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> per la sezione pre-soluzione.  
  
 I gestori di caricamento della soluzione specifici devono disattivare se stessi nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> gestore eventi, in modo da non essere in conflitto con altri responsabili del caricamento della soluzione.  
  
 Se è necessario un gestore di caricamento della soluzione solo per rendere permanente le priorità di caricamento globale del progetto (ad esempio, le proprietà impostate in una pagina di opzioni), è possibile attivare gestione caricamento soluzioni nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents2.OnAfterOpenProject%2A> gestore eventi, rendere permanente l'impostazione nelle proprietà della soluzione, quindi disattivare Gestione caricamento soluzioni.  
  
## <a name="handling-solution-load-events"></a>Gestione degli eventi di caricamento della soluzione  
 Per sottoscrivere gli eventi di caricamento della soluzione, chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> quando si attiva gestione caricamento soluzioni. Se si implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents> , è possibile rispondere a eventi correlati a diverse priorità di caricamento del progetto.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Viene generato prima dell'apertura di una soluzione. È possibile usarlo per modificare la priorità di caricamento del progetto per i progetti nella soluzione.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Questa operazione viene generata dopo che la soluzione è stata completamente caricata, ma prima che il caricamento del progetto in background venga nuovamente avviato. Ad esempio, è possibile che un utente abbia eseguito l'accesso a un progetto la cui priorità di caricamento sia LoadIfNeeded o che il gestore di caricamento della soluzione abbia modificato la priorità di caricamento del progetto in BackgroundLoad, avviando così un caricamento in background del progetto.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Questa operazione viene attivata dopo il caricamento iniziale di una soluzione, indipendentemente dal fatto che sia presente o meno un gestore di caricamento della soluzione. Viene generato anche dopo il caricamento in background o la richiesta di carico ogni volta che la soluzione diventa completamente caricata. Allo stesso tempo, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> viene riattivato.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Viene generato prima del caricamento di un progetto (o di progetti). Per assicurarsi che gli altri processi in background vengano completati prima del caricamento dei progetti, impostare `pfShouldDelayLoadToNextIdle` su **true**.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Viene generato quando un batch di progetti sta per essere caricato. Se `fIsBackgroundIdleBatch` è true, i progetti devono essere caricati in background; se `fIsBackgroundIdleBatch` è false, i progetti devono essere caricati in modo sincrono in seguito a una richiesta dell'utente, ad esempio se l'utente espande un progetto in sospeso in Esplora soluzioni. È possibile implementare questa operazione per eseguire un lavoro costoso che altrimenti sarebbe necessario eseguire in <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Viene generato dopo il caricamento di un batch di progetti.  
  
## <a name="detecting-and-managing-solution-and-project-loading"></a>Rilevamento e gestione del caricamento di soluzioni e progetti  
 Per rilevare lo stato di caricamento dei progetti e delle soluzioni, chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> con i valori seguenti:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` restituisce `true` se la soluzione e tutti i relativi progetti vengono caricati; in caso contrario, `false` .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` restituisce `true` se un batch di progetti è attualmente in fase di caricamento in background; in caso contrario, `false` .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` restituisce `true` se un batch di progetti viene attualmente caricato in modo sincrono a seguito di un comando utente o di un altro carico esplicito; in caso contrario, `false` .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>: `var` restituisce `true` se la soluzione è attualmente in fase di chiusura; in caso contrario, `false` .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>: `var` restituisce `true` se è in corso l'apertura di una soluzione; in caso contrario, `false` .  
  
  È anche possibile assicurarsi che i progetti e le soluzioni siano caricati (indipendentemente dalle priorità di caricamento del progetto) chiamando uno dei metodi seguenti:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: la chiamata a questo metodo impone il caricamento dei progetti in una soluzione prima che il metodo venga restituito.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: la chiamata a questo metodo impone il `guidProject` caricamento dei progetti prima che il metodo venga restituito.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: la chiamata a questo metodo impone il caricamento del progetto in `guidProjectID` prima che il metodo venga restituito.  
  
> [!NOTE]
> . Per impostazione predefinita, vengono caricati solo i progetti che hanno le priorità di caricamento della richiesta e di caricamento in background, ma se il <xref:Microsoft.VisualStudio.Shell.Interop.__VSBSLFLAGS> flag viene passato al metodo, verranno caricati tutti i progetti tranne quelli contrassegnati per il caricamento in modo esplicito.
