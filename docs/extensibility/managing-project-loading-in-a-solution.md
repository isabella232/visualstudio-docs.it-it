---
title: Gestione del caricamento di progetti in una soluzione Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 21cd5e7e557e795db49aea7a14e8e4cc7caa0422
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702725"
---
# <a name="manage-project-loading-in-a-solution"></a>Gestire il caricamento del progetto in una soluzioneManage project loading in a solution
Le soluzioni di Visual Studio possono contenere un numero elevato di progetti. Il comportamento predefinito di Visual Studio consiste nel caricare tutti i progetti in una soluzione al momento dell'apertura della soluzione e non consentire all'utente di accedere a uno qualsiasi dei progetti fino al termine del caricamento. Quando il processo di caricamento del progetto durerà più di due minuti, viene visualizzata una barra di avanzamento che mostra il numero di progetti caricati e il numero totale di progetti. L'utente può scaricare i progetti durante l'utilizzo di una soluzione con più progetti, ma questa procedura presenta alcuni svantaggi: i progetti scaricati non vengono compilati come parte di un comando Ricostruisci soluzione e le descrizioni IntelliSense dei tipi e dei membri dei progetti chiusi non vengono visualizzate.

 Gli sviluppatori possono ridurre i tempi di caricamento della soluzione e gestire il comportamento di caricamento del progetto creando un gestore di carico della soluzione. Il gestore di carico della soluzione può assicurarsi che i progetti vengano caricati prima di avviare una compilazione in background, ritardare il caricamento in background fino al completamento di altre attività in background ed eseguire altre attività di gestione del carico del progetto.

## <a name="create-a-solution-load-manager"></a>Creare un gestore di carico della soluzioneCreate a solution load manager
 Gli sviluppatori possono creare un <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> gestore di caricamento della soluzione implementando e consigliando a Visual Studio che il gestore di carico della soluzione è attivo.

### <a name="activate-a-solution-load-manager"></a>Attivare un gestore di carico della soluzione
 Visual Studio consente un solo gestore di caricamento della soluzione alla volta, pertanto è necessario consigliare Visual Studio quando si desidera attivare il gestore di carico della soluzione. Se in un secondo momento viene attivato un secondo gestore di carico della soluzione, il gestore di carico della soluzione verrà disconnesso.

 È necessario <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> ottenere il servizio e impostare il [__VSPROPID4. proprietà VSPROPID_ActiveSolutionLoadManager:](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>)

```csharp
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;
object objLoadMgr = this;   //the class that implements IVsSolutionManager
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);
```

 Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> metodo viene chiamato quando Visual Studio viene arrestato o quando un pacchetto diverso <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> ha assunto il nome di gestione del carico della soluzione attiva chiamando con il [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) proprietà.

#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Strategie per diversi tipi di gestore di carico della soluzione
 È possibile implementare i responsabili dei carichi della soluzione in modi diversi, a seconda dei tipi di soluzioni che devono gestire.

 Se il gestore di carico della soluzione è destinato a gestire il caricamento della soluzione in generale, può essere implementato come parte di un pacchetto VSPackage.If the solution load manager is meant to manage solution loading in general, it can be implemented as part of a VSPackage. Il pacchetto deve essere impostato per <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> il caricamento automatico aggiungendo <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>il nel pacchetto VSPackage con un valore di . Il gestore di carico della <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> soluzione può quindi essere attivato nel metodo.

> [!NOTE]
> Per ulteriori informazioni sul caricamento automatico dei pacchetti, vedere [Caricamento di pacchetti VSPackage](../extensibility/loading-vspackages.md).

 Poiché Visual Studio riconosce solo l'ultimo gestore di carico della soluzione da attivare, i gestori di carico della soluzione generale devono sempre rilevare se è presente un gestore di carico esistente prima di attivarsi. Se `GetProperty()` si chiama il servizio di soluzione per [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) `null`restituisce , non è presente alcun gestore di carico della soluzione attiva. Se non restituisce null, verificare se l'oggetto è lo stesso del gestore di carico della soluzione.

 Se il gestore di carico della soluzione è destinato a gestire solo alcuni tipi <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>di soluzione, il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> pacchetto VSPackage può sottoscrivere gli eventi di caricamento della soluzione (chiamando ) e utilizzare il gestore eventi per attivare il gestore di caricamento della soluzione.

 Se il gestore di carico della soluzione è destinato a gestire solo soluzioni <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> specifiche, le informazioni di attivazione possono essere rese persistenti come parte del file di soluzione chiamando la sezione pre-soluzione.

 I gestori di caricamento <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> specifici della soluzione devono disattivarsi nel gestore eventi, per non entrare in conflitto con altri gestori di carico della soluzione.

 Se è necessario un gestore di carico della soluzione solo per rendere persistenti le proprietà di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> caricamento del progetto globale (ad esempio, le proprietà impostate in una pagina Opzioni), è possibile attivare il gestore di carico della soluzione nel gestore eventi, rendere persistente l'impostazione nelle proprietà della soluzione, quindi disattivare il gestore di carico della soluzione.

## <a name="handle-solution-load-events"></a>Gestire gli eventi di caricamento della soluzioneHandle solution load events
 Per sottoscrivere gli eventi <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> di caricamento della soluzione, chiamare quando si attiva il gestore di carico della soluzione. Se si <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>implementa , è possibile rispondere a eventi correlati a diverse proprietà di caricamento del progetto.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: questo evento viene generato prima dell'apertura di una soluzione.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: questo evento viene generato dopo che la soluzione è stata completamente caricata, ma prima che il caricamento del progetto in background ricominci.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: questo evento viene generato dopo che una soluzione è inizialmente completamente caricata, indipendentemente dal fatto che sia presente o meno un gestore di carico della soluzione. Viene inoltre generato dopo il caricamento in background o il carico a richiesta ogni volta che la soluzione viene caricata completamente. Allo stesso tempo, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> viene riattivato.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: questo evento viene generato prima del caricamento di uno o più progetti. Per assicurarsi che altri processi in background vengano `pfShouldDelayLoadToNextIdle` completati prima del caricamento dei progetti, impostare **su true**.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: questo evento viene generato quando sta per essere caricato un batch di progetti. Se `fIsBackgroundIdleBatch` è true, i progetti devono essere caricati in background; se `fIsBackgroundIdleBatch` è false, i progetti devono essere caricati in modo sincrono come risultato di una richiesta dell'utente, ad esempio se l'utente espande un progetto in sospeso in Esplora soluzioni. È possibile gestire questo evento per eseguire operazioni costose che altrimenti dovrebbero essere eseguite in <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: questo evento viene generato dopo il caricamento di un batch di progetti.

## <a name="detect-and-manage-solution-and-project-loading"></a>Rilevare e gestire il caricamento di soluzioni e progetti
 Per rilevare lo stato di caricamento <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> di progetti e soluzioni, chiamare con i valori seguenti:

- [__VSPROPID4. VSPROPID_IsSolutionFullyLoaded](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsSolutionFullyLoaded>) `var` : `true` restituisce se la soluzione e `false`tutti i relativi progetti vengono caricati, in caso contrario .

- [__VSPROPID4. VSPROPID_IsInBackgroundIdleLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInBackgroundIdleLoadProjectBatch>) `var` : `true` restituisce se un batch di progetti `false`è attualmente in fase di caricamento in background, in caso contrario .

- [__VSPROPID4. VSPROPID_IsInSyncDemandLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInSyncDemandLoadProjectBatch>) `var` : `true` restituisce un valore che indica se un batch di progetti viene `false`attualmente caricato in modo sincrono come risultato di un comando utente o di un altro caricamento esplicito, in caso contrario .

- [__VSPROPID2. VSPROPID_IsSolutionClosing](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2.VSPROPID_IsSolutionClosing>) `var` : `true` restituisce se la soluzione `false`è attualmente in fase di chiusura, in caso contrario .

- [__VSPROPID. VSPROPID_IsSolutionOpening](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID.VSPROPID_IsSolutionOpening>) `var` : `true` restituisce se è in `false`corso l'apertura di una soluzione, in caso contrario .

È inoltre possibile assicurarsi che i progetti e le soluzioni vengano caricati chiamando uno dei seguenti metodi:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: la chiamata a questo metodo forza il caricamento dei progetti in una soluzione prima della restituzione del metodo.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: la chiamata a `guidProject` questo metodo forza il caricamento dei progetti prima della restituzione del metodo.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: la chiamata a `guidProjectID` questo metodo forza il caricamento del progetto prima della restituzione del metodo.
