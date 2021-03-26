---
title: Gestione del caricamento di progetti in una soluzione | Microsoft Docs
description: Informazioni su come gli sviluppatori possono ridurre i tempi di caricamento della soluzione e gestire il comportamento di caricamento dei progetti creando un gestore di caricamento della soluzione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 425f610e8a473460cb7d9170138521e2e7bee08a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073092"
---
# <a name="manage-project-loading-in-a-solution"></a>Gestire il caricamento di progetti in una soluzione
Le soluzioni di Visual Studio possono contenere un numero elevato di progetti. Il comportamento predefinito di Visual Studio prevede il caricamento di tutti i progetti in una soluzione nel momento in cui la soluzione viene aperta e non consente all'utente di accedere a nessuno dei progetti fino al completamento del caricamento. Quando il processo di caricamento del progetto durerà più di due minuti, viene visualizzato un indicatore di stato che mostra il numero di progetti caricati e il numero totale di progetti. L'utente può scaricare i progetti mentre lavora in una soluzione con più progetti, ma questa procedura presenta alcuni svantaggi: i progetti scaricati non vengono compilati come parte di un comando Ricompila soluzione e le descrizioni IntelliSense dei tipi e dei membri dei progetti chiusi non vengono visualizzate.

 Gli sviluppatori possono ridurre i tempi di caricamento della soluzione e gestire il comportamento di caricamento dei progetti creando un gestore di caricamento della soluzione. Gestione caricamento soluzioni può verificare che i progetti vengano caricati prima di avviare una compilazione in background, ritardare il caricamento in background fino al completamento di altre attività in background ed eseguire altre attività di gestione del caricamento del progetto.

## <a name="create-a-solution-load-manager"></a>Creazione di un gestore di caricamento della soluzione
 Gli sviluppatori possono creare un gestore di caricamento della soluzione implementando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> e indicando a Visual Studio che la gestione del caricamento della soluzione è attiva.

### <a name="activate-a-solution-load-manager"></a>Attivare un gestore di caricamento della soluzione
 Visual Studio consente solo un gestore di caricamento della soluzione in un determinato momento, pertanto è necessario consigliare Visual Studio quando si desidera attivare gestione caricamento soluzioni. Se un secondo gestore di caricamento della soluzione viene attivato in un secondo momento, la gestione del caricamento della soluzione verrà disconnessa.

 È necessario ottenere il <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> servizio e impostare il [__VSPROPID4. Proprietà VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) :

```csharp
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;
object objLoadMgr = this;   //the class that implements IVsSolutionManager
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);
```

 Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> metodo viene chiamato quando Visual Studio viene arrestato o quando un altro pacchetto viene considerato come gestione del caricamento della soluzione attiva chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> con il [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) proprietà.

#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Strategie per diversi tipi di gestione caricamento soluzioni
 È possibile implementare i gestori di caricamento delle soluzioni in modi diversi, a seconda dei tipi di soluzioni che devono gestire.

 Se il gestore di caricamento della soluzione è progettato per gestire il caricamento di soluzioni in generale, può essere implementato come parte di un pacchetto VSPackage. Il pacchetto deve essere impostato su autoload aggiungendo l'oggetto <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> in Vspackage con un valore di <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid> . Il gestore di caricamento della soluzione può quindi essere attivato nel <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metodo.

> [!NOTE]
> Per ulteriori informazioni sul caricamento di pacchetti, vedere Caricamento di pacchetti [VSPackage](../extensibility/loading-vspackages.md).

 Poiché Visual Studio riconosce l'attivazione solo dell'ultimo gestore del caricamento della soluzione, i gestori di caricamento delle soluzioni generali devono sempre rilevare se è presente un gestore di carico esistente prima di attivarsi. Se viene chiamato il `GetProperty()` servizio di soluzione per [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) restituisce `null` , non è presente alcun gestore di caricamento della soluzione attivo. Se non restituisce null, controllare se l'oggetto è uguale al gestore di caricamento della soluzione.

 Se il gestore di caricamento della soluzione è progettato per gestire solo alcuni tipi di soluzione, il pacchetto VSPackage può sottoscrivere gli eventi di caricamento della soluzione (chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> ) e usare il gestore eventi per <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> per attivare il gestore di caricamento della soluzione.

 Se il gestore di caricamento della soluzione è progettato per gestire solo soluzioni specifiche, le informazioni sull'attivazione possono essere rese permanente come parte del file di soluzione chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> per la sezione relativa alla pre-soluzione.

 I gestori di caricamento della soluzione specifici devono disattivare se stessi nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> gestore eventi, in modo da non essere in conflitto con altri responsabili del caricamento della soluzione.

 Se è necessario un gestore di caricamento della soluzione solo per rendere permanente le proprietà del caricamento globale del progetto (ad esempio, le proprietà impostate in una pagina di opzioni), è possibile attivare gestione caricamento soluzioni nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> gestore eventi, rendere permanente l'impostazione nelle proprietà della soluzione, quindi disattivare Gestione caricamento soluzioni.

## <a name="handle-solution-load-events"></a>Gestisci eventi di caricamento della soluzione
 Per sottoscrivere gli eventi di caricamento della soluzione, chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> quando si attiva gestione caricamento soluzioni. Se si implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents> , è possibile rispondere a eventi correlati a diverse proprietà di caricamento del progetto.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Questo evento viene generato prima dell'apertura di una soluzione.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Questo evento viene generato dopo che la soluzione è stata caricata completamente, ma prima che il caricamento del progetto in background venga riavviato.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Questo evento viene generato dopo che una soluzione è stata caricata inizialmente completamente, indipendentemente dal fatto che sia presente o meno un gestore di caricamento della soluzione. Viene generato anche dopo il caricamento in background o la richiesta di carico ogni volta che la soluzione diventa completamente caricata. Allo stesso tempo, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> viene riattivato.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Questo evento viene generato prima del caricamento di un progetto (o progetti). Per assicurarsi che gli altri processi in background vengano completati prima del caricamento dei progetti, impostare `pfShouldDelayLoadToNextIdle` su **true**.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Questo evento viene generato quando un batch di progetti sta per essere caricato. Se `fIsBackgroundIdleBatch` è true, i progetti devono essere caricati in background; se `fIsBackgroundIdleBatch` è false, i progetti devono essere caricati in modo sincrono in seguito a una richiesta dell'utente, ad esempio se l'utente espande un progetto in sospeso in Esplora soluzioni. È possibile gestire questo evento per eseguire un lavoro costoso che altrimenti sarebbe necessario eseguire in <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> .

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Questo evento viene generato dopo il caricamento di un batch di progetti.

## <a name="detect-and-manage-solution-and-project-loading"></a>Rilevare e gestire il caricamento di soluzioni e progetti
 Per rilevare lo stato di caricamento dei progetti e delle soluzioni, chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> con i valori seguenti:

- [__VSPROPID4. VSPROPID_IsSolutionFullyLoaded](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsSolutionFullyLoaded>): `var` restituisce `true` se la soluzione e tutti i relativi progetti vengono caricati; in caso contrario, `false` .

- [__VSPROPID4. VSPROPID_IsInBackgroundIdleLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInBackgroundIdleLoadProjectBatch>): `var` restituisce `true` se un batch di progetti è attualmente in fase di caricamento in background; in caso contrario, `false` .

- [__VSPROPID4. VSPROPID_IsInSyncDemandLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInSyncDemandLoadProjectBatch>): `var` restituisce `true` se un batch di progetti viene attualmente caricato in modo sincrono a seguito di un comando utente o di un altro carico esplicito; in caso contrario, `false` .

- [__VSPROPID2. VSPROPID_IsSolutionClosing](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2.VSPROPID_IsSolutionClosing>): `var` restituisce `true` se la soluzione è attualmente in fase di chiusura; in caso contrario, `false` .

- [__VSPROPID. VSPROPID_IsSolutionOpening](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID.VSPROPID_IsSolutionOpening>): `var` restituisce `true` se è in corso l'apertura di una soluzione; in caso contrario, `false` .

È anche possibile assicurarsi che i progetti e le soluzioni vengano caricati chiamando uno dei metodi seguenti:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: la chiamata a questo metodo impone il caricamento dei progetti in una soluzione prima che il metodo venga restituito.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: la chiamata a questo metodo impone il `guidProject` caricamento dei progetti prima che il metodo venga restituito.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: la chiamata a questo metodo impone il caricamento del progetto in `guidProjectID` prima che il metodo venga restituito.
