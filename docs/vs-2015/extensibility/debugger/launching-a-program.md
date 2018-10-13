---
title: Avvio di un programma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debug engines, launching
- programs, launching
ms.assetid: 6857e9c6-e44a-468a-afa4-f7c4a0b77844
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 27b7daadd3642a4eb35d993e37b6ade3bd829972
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49242549"
---
# <a name="launching-a-program"></a>Avvio di un programma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gli utenti che desiderano eseguire il debug di un programma è possono premere F5 per eseguire il debugger dall'IDE. Questo passaggio inizia una serie di eventi che risultano dell'IDE per la connessione a un motore di debug (DE), che a sua volta connesso, o collegato, per il programma come indicato di seguito:  
  
1.  L'IDE chiama innanzitutto il pacchetto del progetto per ottenere le impostazioni di debug progetto attivo della soluzione. Le impostazioni includono la directory di avvio, le variabili di ambiente, la porta in cui verrà eseguito il programma e la Germania da utilizzare per creare il programma, se specificato. Queste impostazioni vengono passate al pacchetto di debug.  
  
2.  Se viene specificato un CRI, la Germania chiama il sistema operativo per avviare il programma. Di conseguenza l'avvio del programma, viene caricato l'ambiente del programma in fase di esecuzione. Ad esempio, se un programma viene scritto in codice MSIL, common language runtime verrà richiamato per eseguire il programma.  
  
     oppure  
  
     Se non viene specificato un CRI, la porta chiama il sistema operativo per avviare il programma, che comporta da caricare nell'ambiente in fase di esecuzione del programma.  
  
    > [!NOTE]
    >  Se un CRI viene usato per avviare un programma, è probabile che la Germania stesso verrà collegato al programma.  
  
3.  A seconda del fatto che la Germania o la porta ha avviato il programma, il DE o l'ambiente di run-time quindi crea una descrizione del programma, o un nodo e informa la porta su cui l'esecuzione del programma.  
  
    > [!NOTE]
    >  È consigliabile che l'ambiente di runtime creare il nodo di programma, perché il nodo di programma è una rappresentazione leggera di un programma che è possibile eseguire il debug. Non è necessario caricare un intero DE sufficiente per creare e registrare un nodo di programma. Se la Germania è progettato per l'esecuzione in corso l'IDE, ma nessun IDE è in esecuzione, deve essere un componente che è possibile aggiungere un nodo di programma per la porta.  
  
 Il programma appena creato, insieme a eventuali altri programmi, correlati o non correlati, avviato o collegati per dall'IDE stesso, creare una sessione di debug.  
  
 A livello di codice quando l'utente prima di tutto preme **F5**, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]del pacchetto di debug chiama il pacchetto del progetto, ovvero associato con il tipo di programma viene avviato, tramite il <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> metodo, che a sua volta compila un <xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2> struttura con impostazioni di debug della soluzione progetto attivo. Questa struttura viene passata al pacchetto di debug tramite una chiamata al <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A> (metodo). Il pacchetto di debug crea quindi un'istanza di gestione del debug sessione (SDM), che avvia il programma in fase di motori di debug in fase di debug e di eventuali oggetti associati.  
  
 Uno degli argomenti passati per il modello SDM è il GUID della DE da utilizzare per avviare il programma.  
  
 Se non è il GUID DE `GUID_NULL`, il modello SDM CO-crea il DE e quindi chiama relativi [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) metodo per avviare il programma. Ad esempio, se un programma viene scritto in codice nativo, quindi `IDebugEngineLaunch2::LaunchSuspended` probabilmente chiamerà `CreateProcess` e `ResumeThread` (funzioni Win32) per eseguire il programma.  
  
 Di conseguenza l'avvio del programma, viene caricato l'ambiente del programma in fase di esecuzione. La Germania o l'ambiente di runtime crea quindi un' [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) l'interfaccia per descrivere il programma e passa a questa interfaccia [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) per notificare la porta che il programma è è in esecuzione.  
  
 Se `GUID_NULL` viene passato, quindi la porta consente di avviare il programma. Dopo l'esecuzione del programma, l'ambiente di runtime crea un `IDebugProgramNode2` interfaccia per descrivere il programma e lo passa al `IDebugPortNotify2::AddProgramNode`. Questa notifica la porta su cui l'esecuzione del programma. Il modello SDM collega quindi il motore di debug per il programma in esecuzione.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Notifica della porta](../../extensibility/debugger/notifying-the-port.md)  
 Viene illustrato cosa accade dopo che un programma viene avviato e la porta è una notifica.  
  
 [Collegamento dopo un avvio](../../extensibility/debugger/attaching-after-a-launch.md)  
 Documenti quando la sessione di debug è pronta per collegare il DE al programma.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)  
 Contiene collegamenti alle varie attività di debug, ad esempio l'avvio di un programma e la valutazione delle espressioni.

