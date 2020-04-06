---
title: Avvio di un programma Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- programs, launching
ms.assetid: 6857e9c6-e44a-468a-afa4-f7c4a0b77844
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf638e0c96c7df1de2650260427a972a07efce23
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738473"
---
# <a name="launch-a-program"></a>Avviare un programma
Gli utenti che desiderano eseguire il debug di un programma possono premere **F5** per eseguire il debugger dall'IDE. Questo inizia una serie di eventi che alla fine si traducono in connessione dell'IDE a un motore di debug (DE), che è a sua volta connesso, o collegato, al programma come segue:

1. L'IDE chiama innanzitutto il pacchetto del progetto per ottenere le impostazioni di debug del progetto attive della soluzione. Le impostazioni includono la directory iniziale, le variabili di ambiente, la porta in cui verrà eseguito il programma e il DE da utilizzare per creare il programma, se specificato. Queste impostazioni vengono passate al pacchetto di debug.

2. Se viene specificato un DE, il DE chiama il sistema operativo per avviare il programma. Come conseguenza del lancio del programma, l'ambiente di runtime del programma viene caricato. Ad esempio, se un programma è scritto in MSIL, Common Language Runtime verrà richiamato per eseguire il programma.

    -oppure-

    Se non viene specificato un DE, la porta chiama il sistema operativo per avviare il programma, che causa il caricamento dell'ambiente di runtime del programma.

   > [!NOTE]
   > Se un DE viene utilizzato per avviare un programma, è probabile che lo stesso DE verrà collegato al programma.

3. A seconda che il DE o la porta ha avviato il programma, il DE o l'ambiente di runtime quindi crea una descrizione del programma, o nodo, e notifica alla porta che il programma è in esecuzione.

   > [!NOTE]
   > È consigliabile che l'ambiente di runtime crei il nodo di programma, perché il nodo di programma è una rappresentazione leggera di un programma di cui è possibile eseguire il debug. Non è necessario caricare un intero DE solo per creare e registrare un nodo di programma. Se il DE è progettato per l'esecuzione nel processo dell'IDE, ma nessun IDE è effettivamente in esecuzione, è necessario che sia presente un componente in grado di aggiungere un nodo di programma alla porta.

   Il programma appena creato, insieme a tutti gli altri programmi, correlati o non correlati, avviato o collegato dallo stesso IDE, comporre una sessione di debug.

   A livello di codice, quando l'utente preme per la prima volta **F5**, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]il pacchetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> di debug chiama il pacchetto <xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2> del progetto (associato al tipo di programma avviato) tramite il metodo , che a sua volta riempie una struttura con le impostazioni di debug del progetto attive della soluzione. Questa struttura viene passata al pacchetto di <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A> debug tramite una chiamata al metodo . Il pacchetto di debug crea quindi un'istanza del gestore di sessione di debug (SDM), che avvia il programma in fase di debug e gli eventuali motori di debug associati.

   Uno degli argomenti passati al file SDM è il GUID del DE da utilizzare per avviare il programma.

   Se il GUID `GUID_NULL`DE non è , il modello SDM crea il DE, quindi chiama il relativo metodo [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) per avviare il programma. Ad esempio, se un programma è `IDebugEngineLaunch2::LaunchSuspended` scritto `CreateProcess` in `ResumeThread` codice nativo, probabilmente chiamerà e (funzioni Win32) per eseguire il programma.

   Come conseguenza dell'avvio del programma, viene caricato l'ambiente di runtime del programma. Il DE o l'ambiente di runtime quindi crea un [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interfaccia per descrivere il programma e passa questa interfaccia a [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) per notificare la porta che il programma è in esecuzione.

   Se `GUID_NULL` viene passato, la porta avvia il programma. Una volta che il programma è in `IDebugProgramNode2` esecuzione, l'ambiente di `IDebugPortNotify2::AddProgramNode`runtime crea un'interfaccia per descrivere il programma e lo passa a . In questo modo viene notificata alla porta che il programma è in esecuzione. Quindi il file SDM collega il motore di debug al programma in esecuzione.

## <a name="in-this-section"></a>Contenuto della sezione
 [Notifica della porta](../../extensibility/debugger/notifying-the-port.md) Viene illustrato cosa accade dopo l'avvio di un programma e la notifica della porta.

 [Collegamento dopo un lancio](../../extensibility/debugger/attaching-after-a-launch.md) Documenti quando la sessione di debug è pronta per collegare il DE al programma.

## <a name="related-sections"></a>Sezioni correlate
 [Attività di debugDebugging tasks](../../extensibility/debugger/debugging-tasks.md) Contiene collegamenti a varie attività di debug, ad esempio l'avvio di un programma e la valutazione di espressioni.
