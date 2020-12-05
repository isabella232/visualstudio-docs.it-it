---
title: Avvio di un programma | Microsoft Docs
description: Informazioni sulle serie di eventi che si verificano quando si esegue il debug di un programma con F5 per eseguire il debugger dall'IDE.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 0dce13e49eeadf4dc02fec07707bebcfe164ed9c
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606697"
---
# <a name="launch-a-program"></a>Avviare un programma
Gli utenti che desiderano eseguire il debug di un programma possono premere **F5** per eseguire il debugger dall'IDE. Viene avviata una serie di eventi che in definitiva comportano la connessione dell'IDE a un motore di debug (DE), che a sua volta è connesso o collegato al programma, come indicato di seguito:

1. L'IDE chiama prima il pacchetto del progetto per ottenere le impostazioni di debug del progetto attive della soluzione. Le impostazioni includono la directory iniziale, le variabili di ambiente, la porta in cui il programma viene eseguito e la DE da usare per creare il programma, se specificato. Queste impostazioni vengono passate al pacchetto di debug.

2. Se viene specificato un valore DE, il DE chiama il sistema operativo per avviare il programma. Come conseguenza dell'avvio del programma, viene caricato l'ambiente di runtime del programma. Se, ad esempio, un programma è scritto in MSIL, il Common Language Runtime verrà richiamato per eseguire il programma.

    -oppure-

    Se non si specifica un valore di, la porta chiama il sistema operativo per avviare il programma, causando il caricamento dell'ambiente di runtime del programma.

   > [!NOTE]
   > Se viene usato un DE per avviare un programma, è probabile che lo stesso DE venga allegato al programma.

3. A seconda del fatto che la DE o la porta abbia avviato il programma, il DE o l'ambiente di runtime crea una descrizione o un nodo del programma e notifica alla porta che il programma è in esecuzione.

   > [!NOTE]
   > È consigliabile che l'ambiente di runtime crei il nodo del programma, poiché il nodo del programma è una rappresentazione semplificata di un programma di cui è possibile eseguire il debug. Non è necessario caricare un intero DE solo per creare e registrare un nodo del programma. Se la DE è progettata per essere eseguita nel processo dell'IDE, ma nessun IDE è effettivamente in esecuzione, deve essere presente un componente che può aggiungere un nodo di programma alla porta.

   Il programma appena creato, insieme ad altri programmi, correlati o non correlati, avviato o collegato dallo stesso IDE, compongono una sessione di debug.

   A livello di codice, quando l'utente preme prima **F5**, il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pacchetto di debug chiama il pacchetto del progetto (associato al tipo di programma avviato) tramite il <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> metodo, che a sua volta compila una <xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2> struttura con le impostazioni di debug del progetto attive della soluzione. Questa struttura viene passata di nuovo al pacchetto di debug tramite una chiamata al <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A> metodo. Il pacchetto di debug crea quindi un'istanza di Session Debug Manager (SDM), che avvia il programma di cui è in corso il debug e tutti i motori di debug associati.

   Uno degli argomenti passati a SDM è il GUID della DE da usare per avviare il programma.

   Se il GUID DE non è `GUID_NULL` , l'SDM crea la co, quindi chiama il metodo [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) per avviare il programma. Se, ad esempio, un programma è scritto in codice nativo, chiamerà `IDebugEngineLaunch2::LaunchSuspended` probabilmente `CreateProcess` e `ResumeThread` (funzioni Win32) per eseguire il programma.

   Come conseguenza dell'avvio del programma, viene caricato l'ambiente di runtime del programma. Il DE o l'ambiente di runtime crea quindi un'interfaccia [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) per descrivere il programma e passa questa interfaccia a [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) per notificare alla porta che il programma è in esecuzione.

   Se `GUID_NULL` viene passato, la porta avvia il programma. Quando il programma è in esecuzione, l'ambiente di runtime crea un' `IDebugProgramNode2` interfaccia per descrivere il programma e lo passa a `IDebugPortNotify2::AddProgramNode` . Questa operazione informa la porta che il programma è in esecuzione. Quindi, il SDM connette il motore di debug al programma in esecuzione.

## <a name="in-this-section"></a>Contenuto della sezione
 [Notifica della porta](../../extensibility/debugger/notifying-the-port.md) Spiega cosa accade dopo l'avvio di un programma e la notifica della porta.

 [Connessione dopo un avvio](../../extensibility/debugger/attaching-after-a-launch.md) Documenti quando la sessione di debug è pronta per alleghire il DE al programma.

## <a name="related-sections"></a>Sezioni correlate
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md) Contiene collegamenti a diverse attività di debug, ad esempio l'avvio di un programma e la valutazione delle espressioni.
