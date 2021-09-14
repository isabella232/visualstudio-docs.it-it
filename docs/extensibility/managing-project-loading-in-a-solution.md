---
title: Gestione Project caricamento in una soluzione | Microsoft Docs
description: Informazioni su come gli sviluppatori possono ridurre i tempi di caricamento della soluzione e gestire il comportamento di caricamento dei progetti creando un gestore del carico della soluzione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: eb240a99b486d7faeb481d78052e66fc6fd40024
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709462"
---
# <a name="manage-project-loading-in-a-solution"></a>Gestire il caricamento del progetto in una soluzione
Visual Studio soluzioni possono contenere un numero elevato di progetti. Il comportamento Visual Studio predefinito consiste nel caricare tutti i progetti in una soluzione al momento dell'apertura della soluzione e non consentire all'utente di accedere ai progetti fino al termine del caricamento. Quando il processo di caricamento del progetto dura più di due minuti, viene visualizzato un indicatore di stato che mostra il numero di progetti caricati e il numero totale di progetti. L'utente può scaricare i progetti mentre lavora in una soluzione con più progetti, ma questa procedura presenta alcuni svantaggi: i progetti scaricati non vengono compilati come parte di un comando Ricompila soluzione e le descrizioni IntelliSense di tipi e membri di progetti chiusi non vengono visualizzate.

 Gli sviluppatori possono ridurre i tempi di caricamento della soluzione e gestire il comportamento di caricamento dei progetti creando un gestore del carico della soluzione. Il gestore del carico della soluzione può assicurarsi che i progetti siano caricati prima di avviare una compilazione in background, ritardare il caricamento in background fino al completamento di altre attività in background ed eseguire altre attività di gestione del carico del progetto.

## <a name="create-a-solution-load-manager"></a>Creare un gestore del carico della soluzione
 Gli sviluppatori possono creare un gestore del carico della soluzione implementando e consigliando Visual Studio che il gestore del carico della soluzione <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> sia attivo.

### <a name="activate-a-solution-load-manager"></a>Attivare un gestore del carico della soluzione
 Visual Studio consente un solo gestore del carico della soluzione in un determinato momento, pertanto è necessario Visual Studio quando si vuole attivare il gestore del carico della soluzione. Se un secondo gestore del carico della soluzione viene attivato in un secondo momento, il gestore del carico della soluzione verrà disconnesso.

 È necessario ottenere il <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> servizio e impostare il [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) proprietà:

```csharp
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;
object objLoadMgr = this;   //the class that implements IVsSolutionManager
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);
```

 Il metodo viene chiamato quando Visual Studio viene arrestato o quando un pacchetto diverso ha assunto il controllo come gestore del carico della soluzione attiva chiamando con il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) proprietà.

#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Strategie per diversi tipi di gestione del carico della soluzione
 È possibile implementare i gestori del carico delle soluzioni in modi diversi, a seconda dei tipi di soluzioni che devono gestire.

 Se lo strumento di gestione del carico della soluzione è destinato a gestire il caricamento della soluzione in generale, può essere implementato come parte di un vspackage. Il pacchetto deve essere impostato per il caricamento automatico aggiungendo <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> nel pacchetto VSPackage il valore <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid> . Il gestore del carico della soluzione può quindi essere attivato nel <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metodo .

> [!NOTE]
> Per altre informazioni sul caricamento automatico dei pacchetti, vedere [Caricamento di VSPackage.](../extensibility/loading-vspackages.md)

 Poiché Visual Studio riconosce solo l'ultimo gestore del carico della soluzione da attivare, i gestori del carico di soluzioni generali devono sempre rilevare se è presente un gestore di carico esistente prima di attivarsi. Se si `GetProperty()` chiama sul servizio della soluzione per [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) restituisce `null` , non è presente alcun gestore del carico della soluzione attivo. Se non restituisce null, verificare se l'oggetto è uguale al gestore del carico della soluzione.

 Se lo strumento di gestione del carico della soluzione deve gestire solo alcuni tipi di soluzione, il pacchetto VSPackage può sottoscrivere gli eventi di caricamento della soluzione (chiamando ) e usare il gestore eventi per per attivare il gestore del carico della <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> soluzione.

 Se il gestore del carico della soluzione è destinato a gestire solo soluzioni specifiche, le informazioni di attivazione possono essere rese persistenti come parte del file di soluzione chiamando per la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> sezione pre-soluzione.

 I gestori del carico di soluzioni specifici devono disattivarsi nel gestore eventi, in modo da non creare conflitti con altri gestori <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> del carico della soluzione.

 Se è necessario un gestore del carico della soluzione solo per rendere persistenti le proprietà di caricamento globali del progetto (ad esempio, le proprietà impostate in una pagina Opzioni), è possibile attivare gestione carico soluzione nel gestore eventi, rendere persistente l'impostazione nelle proprietà della soluzione, quindi disattivare il gestore del carico della <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> soluzione.

## <a name="handle-solution-load-events"></a>Gestire gli eventi di caricamento della soluzione
 Per sottoscrivere gli eventi di caricamento della soluzione, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> chiamare quando si attiva il gestore del carico della soluzione. Se si implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents> , è possibile rispondere agli eventi correlati a diverse proprietà di caricamento del progetto.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: questo evento viene generato prima dell'apertura di una soluzione.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: questo evento viene generato dopo il caricamento completo della soluzione, ma prima che il caricamento del progetto in background inizi di nuovo.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: questo evento viene generato dopo che una soluzione è stata inizialmente caricata completamente, indipendentemente dal fatto che sia presente o meno un gestore del carico della soluzione. Viene attivato anche dopo il carico in background o il carico su richiesta ogni volta che la soluzione diventa completamente caricata. Allo stesso tempo, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> viene riattivato.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: questo evento viene generato prima del caricamento di un progetto (o di progetti). Per assicurarsi che altri processi in background siano completati prima del caricamento dei progetti, impostare `pfShouldDelayLoadToNextIdle` su **true**.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: questo evento viene generato quando un batch di progetti sta per essere caricato. Se è true, i progetti devono essere caricati in background; se è false, i progetti devono essere caricati in modo sincrono in seguito a una richiesta dell'utente, ad esempio se l'utente espande un progetto in sospeso `fIsBackgroundIdleBatch` `fIsBackgroundIdleBatch` in Esplora soluzioni. È possibile gestire questo evento per eseguire operazioni costose che altrimenti avrebbero bisogno di essere eseguite in <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> .

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: questo evento viene generato dopo il caricamento di un batch di progetti.

## <a name="detect-and-manage-solution-and-project-loading"></a>Rilevare e gestire il caricamento di soluzioni e progetti
 Per rilevare lo stato di caricamento di progetti e soluzioni, chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> con i valori seguenti:

- [__VSPROPID4. VSPROPID_IsSolutionFullyLoaded](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsSolutionFullyLoaded>): `var` restituisce se la soluzione e tutti i relativi progetti vengono `true` caricati, in caso contrario `false` .

- [__VSPROPID4. VSPROPID_IsInBackgroundIdleLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInBackgroundIdleLoadProjectBatch>): restituisce se un batch di progetti è attualmente `var` caricato in `true` background, in caso contrario `false` .

- [__VSPROPID4. VSPROPID_IsInSyncDemandLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInSyncDemandLoadProjectBatch>): restituisce se un batch di progetti è attualmente caricato in modo sincrono come risultato di un comando utente o di un altro caricamento `var` `true` esplicito, in caso contrario `false` .

- [__VSPROPID2. VSPROPID_IsSolutionClosing](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2.VSPROPID_IsSolutionClosing>): `var` restituisce se la soluzione è attualmente `true` chiusa, in caso contrario `false` .

- [__VSPROPID. VSPROPID_IsSolutionOpening](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID.VSPROPID_IsSolutionOpening>): `var` restituisce `true` se una soluzione è attualmente aperta, in caso contrario `false` .

È anche possibile assicurarsi che i progetti e le soluzioni siano caricati chiamando uno dei metodi seguenti:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: la chiamata a questo metodo forza il caricamento dei progetti in una soluzione prima che il metodo venga restituito.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: la chiamata a questo metodo forza il caricamento dei progetti in `guidProject` prima che il metodo venga restituito.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: la chiamata a questo metodo forza il caricamento del progetto in `guidProjectID` prima che il metodo venga restituito.
