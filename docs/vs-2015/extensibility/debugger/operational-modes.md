---
title: Modalità operative | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, modes
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c4009ab6268140117c8fd1294adcc52ac347b799
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153725"
---
# <a name="operational-modes"></a>Modalità operative
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Sono disponibili tre modalità in cui l'IDE può funzionare, come indicato di seguito:  
  
- [Modalità progettazione](#vsconoperationalmodesanchor1)  
  
- [Modalità di esecuzione](#vsconoperationalmodesanchor2)  
  
- [Modalità di interruzione](#vsconoperationalmodesanchor3)  
  
  Il modo in cui il motore di debug personalizzato (DE) esegue la transizione tra queste modalità è una decisione di implementazione che richiede di acquisire familiarità con i meccanismi di transizione. Il DE può o non può implementare direttamente queste modalità. Queste modalità sono realmente modalità di debug del pacchetto che passano in base all'azione dell'utente o agli eventi del DE. Ad esempio, la transizione dalla modalità di esecuzione alla modalità di interruzione è stata istigata da un evento di arresto dal DE. La transizione da Interrompi a modalità di esecuzione o passaggio è stata istigata dall'utente che esegue operazioni come step o Execute. Per ulteriori informazioni sulle transizioni DE, vedere [controllo dell'esecuzione](../../extensibility/debugger/control-of-execution.md).  
  
## <a name="design-mode"></a><a name="vsconoperationalmodesanchor1"></a> Modalità progettazione  
 La modalità progettazione è lo stato di non esecuzione del debug di Visual Studio, nel qual caso è possibile impostare le funzionalità di debug nell'applicazione.  
  
 In modalità progettazione vengono utilizzate solo alcune funzionalità di debug. Uno sviluppatore può scegliere di impostare i punti di interruzione o creare espressioni di controllo. Il DE non viene mai caricato o chiamato mentre l'IDE è in modalità progettazione. L'interazione con il DE si verifica solo in modalità di esecuzione e di interruzioni.  
  
## <a name="run-mode"></a><a name="vsconoperationalmodesanchor2"></a> Modalità di esecuzione  
 La modalità di esecuzione si verifica quando un programma viene eseguito in una sessione di debug nell'IDE. L'applicazione viene eseguita fino alla chiusura, fino a quando non viene raggiunto un punto di interruzione o fino a quando non viene generata un'eccezione. Quando l'applicazione viene eseguita fino alla chiusura, il passaggio della transizione alla modalità di progettazione. Quando viene raggiunto un punto di interruzione o viene generata un'eccezione, la funzione DE passa alla modalità di interruzione.  
  
## <a name="break-mode"></a><a name="vsconoperationalmodesanchor3"></a> Modalità di interruzioni  
 La modalità di interruzioni si verifica quando l'esecuzione del programma di debug viene sospesa. La modalità di interruzioni consente allo sviluppatore di creare uno snapshot dell'applicazione al momento dell'esecuzione del break e consente allo sviluppatore di analizzare lo stato dell'applicazione e modificare il modo in cui l'applicazione viene eseguita. Lo sviluppatore può visualizzare e modificare il codice, esaminare o modificare i dati, riavviare l'applicazione, terminare l'esecuzione o continuare l'esecuzione dallo stesso punto.  
  
 La modalità di interruzione viene immessa quando il DE Invia un evento di arresto sincrono. Gli eventi di arresto sincrono, detti anche eventi di arresto, notificano alla gestione del debug della sessione (SDM) e all'IDE che l'applicazione di cui è in corso il debug ha interrotto l'esecuzione del codice. Le interfacce [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) e [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) sono esempi di arresto degli eventi.  
  
 L'arresto degli eventi continua con una chiamata a uno dei metodi seguenti, che consentono di eseguire la transizione del debugger dalla modalità di interruzione alla modalità di esecuzione o passaggio:  
  
- [Eseguire](../../extensibility/debugger/reference/idebugprocess3-execute.md)  
  
- [Step](../../extensibility/debugger/reference/idebugprocess3-step.md)  
  
- [Continua](../../extensibility/debugger/reference/idebugprocess3-continue.md)  
  
### <a name="step-mode"></a><a name="vsconoperationalmodesanchor4"></a> Modalità passaggio  
 La modalità passaggio si verifica quando il programma si avvicina alla riga di codice successiva o in, più o fuori da una funzione. Un passaggio viene eseguito chiamando il [passaggio](../../extensibility/debugger/reference/idebugprocess3-step.md)del metodo. Questo metodo richiede `DWORD` che specifichi le enumerazioni [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) e [STEPKIND](../../extensibility/debugger/reference/stepkind.md) come parametri di input.  
  
 Quando il programma passa alla riga di codice successiva o in una funzione o viene eseguito fino al cursore o a un punto di interruzione impostato, il valore di viene automaticamente reimpostato sulla modalità di interruzione.  
  
## <a name="see-also"></a>Vedere anche  
 [Controllo dell'esecuzione](../../extensibility/debugger/control-of-execution.md)
