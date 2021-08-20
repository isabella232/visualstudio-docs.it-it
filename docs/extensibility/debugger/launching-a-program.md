---
title: Avvio di un programma | Microsoft Docs
description: Informazioni sulla serie di eventi che si verificano quando si esegue il debug di un programma tramite F5 per eseguire il debugger dall'IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- programs, launching
ms.assetid: 6857e9c6-e44a-468a-afa4-f7c4a0b77844
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: ef92dc5b0884d0415e5b7b5245315929cf144258
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122160621"
---
# <a name="launch-a-program"></a>Avviare un programma
Gli utenti che vogliono eseguire il debug di un programma possono **premere F5** per eseguire il debugger dall'IDE. Viene avviata una serie di eventi che alla fine comportano la connessione dell'IDE a un motore di debug (DE), che a sua volta è connesso, o collegato, al programma come indicato di seguito:

1. L'IDE chiama prima il pacchetto del progetto per ottenere le impostazioni di debug del progetto attivo della soluzione. Le impostazioni includono la directory iniziale, le variabili di ambiente, la porta in cui verrà eseguito il programma e il de da usare per creare il programma, se specificato. Queste impostazioni vengono passate al pacchetto di debug.

2. Se viene specificato un de, de chiama il sistema operativo per avviare il programma. Come conseguenza dell'avvio del programma, viene caricato l'ambiente di run-time del programma. Ad esempio, se un programma è scritto in MSIL, common language runtime verrà richiamato per eseguire il programma.

    -oppure-

    Se non viene specificato un de, la porta chiama il sistema operativo per avviare il programma, causando il caricamento dell'ambiente di run-time del programma.

   > [!NOTE]
   > Se si usa un de per avviare un programma, è probabile che lo stesso DE verrà collegato al programma.

3. A seconda che de o la porta ha avviato il programma, DE o l'ambiente di run-time crea quindi una descrizione del programma, o nodo, e notifica alla porta che il programma è in esecuzione.

   > [!NOTE]
   > È consigliabile che l'ambiente di run-time crei il nodo del programma, perché il nodo di programma è una rappresentazione leggera di un programma di cui è possibile eseguire il debug. Non è necessario caricare un intero DE solo per creare e registrare un nodo di programma. Se DE è progettato per l'esecuzione nel processo dell'IDE, ma nessun IDE è effettivamente in esecuzione, è necessario un componente in grado di aggiungere un nodo di programma alla porta.

   Il programma appena creato, insieme a qualsiasi altro programma, correlato o non correlato, avviato o collegato allo stesso IDE, componi una sessione di debug.

   A livello di codice, quando l'utente preme **F5** per la prima volta, il pacchetto di debug di chiama il pacchetto di progetto (associato al tipo di programma avviato) tramite il metodo , che a sua volta compila una struttura con le impostazioni di debug del progetto attive della [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> <xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2> soluzione. Questa struttura viene passata nuovamente al pacchetto di debug tramite una chiamata al <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A> metodo . Il pacchetto di debug crea quindi un'istanza di Session Debug Manager (SDM), che avvia il programma in fase di debug ed eventuali motori di debug associati.

   Uno degli argomenti passati a SDM è il GUID di DE da usare per avviare il programma.

   Se de GUID non è , SDM co-crea de de e quindi chiama il relativo `GUID_NULL` [metodo LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) per avviare il programma. Ad esempio, se un programma è scritto in codice nativo, probabilmente chiamerà `IDebugEngineLaunch2::LaunchSuspended` `CreateProcess` e `ResumeThread` (funzioni Win32) per eseguire il programma.

   Come conseguenza dell'avvio del programma, viene caricato l'ambiente di run-time del programma. De o l'ambiente di run-time crea quindi un'interfaccia [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) per descrivere il programma e passa questa interfaccia ad [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) per notificare alla porta che il programma è in esecuzione.

   Se `GUID_NULL` viene passato , la porta avvia il programma. Quando il programma è in esecuzione, l'ambiente di run-time crea un'interfaccia `IDebugProgramNode2` per descrivere il programma e la passa a `IDebugPortNotify2::AddProgramNode` . In questo modo si notifica alla porta che il programma è in esecuzione. SDM collega quindi il motore di debug al programma in esecuzione.

## <a name="in-this-section"></a>Contenuto della sezione
 [Notifica alla porta](../../extensibility/debugger/notifying-the-port.md) Spiega cosa accade dopo l'avvio di un programma e la notifica alla porta.

 [Collegamento dopo un avvio](../../extensibility/debugger/attaching-after-a-launch.md) Documenta quando la sessione di debug è pronta per collegare de al programma.

## <a name="related-sections"></a>Sezioni correlate
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md) Contiene collegamenti a varie attività di debug, ad esempio l'avvio di un programma e la valutazione di espressioni.
