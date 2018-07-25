---
title: Modalità operative | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, modes
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 56791d944b811ec4ca549ec51affaa74cb421909
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/24/2018
ms.locfileid: "39232912"
---
# <a name="operational-modes"></a>Modalità operative
Sono disponibili tre modalità in cui può operare nell'IDE, come indicato di seguito:  
  
-   [Modalità progettazione](#vsconoperationalmodesanchor1)  
  
-   [Modalità di esecuzione](#vsconoperationalmodesanchor2)  
  
-   [Modalità di interruzione](#vsconoperationalmodesanchor3)  
  
 Come avviene la transizione tra le modalità del motore di debug personalizzato (DE) è una decisione di implementazione che è necessario avere familiarità con i meccanismi di transizione. Il DE potrebbe o non può implementare direttamente queste modalità. Queste modalità sono davvero debug pacchetto modalità cui passare basate sulle azione dell'utente o gli eventi dal DE. Ad esempio, la transizione dalla modalità di esecuzione alla modalità di interruzione viene attivata da un evento di arresto dal DE. La transizione dall'interruzione di eseguire in modalità o in modalità di passaggio è eseguirlo è l'utente che esegue le operazioni, ad esempio Esegui o passaggio. Per altre informazioni sulle transizioni DE, vedere [controllo di esecuzione](../../extensibility/debugger/control-of-execution.md).  
  
##  <a name="vsconoperationalmodesanchor1"></a> Modalità progettazione  
 Modalità di progettazione è lo stato nonrunning del debug di Visual Studio, durante i quali è possibile impostare le funzionalità nell'applicazione di debug.  
  
 Solo debug alcune funzionalità vengono usate durante la modalità di progettazione. Uno sviluppatore può scegliere di impostare punti di interruzione o creare espressioni di controllo. Il DE viene mai caricato o chiamato mentre l'IDE è in modalità progettazione. L'interazione con il rilevamento viene eseguita durante l'interruzione e l'esecuzione solo con le modalità.  
  
##  <a name="vsconoperationalmodesanchor2"></a> Modalità di esecuzione  
 Modalità di esecuzione si verifica quando un programma viene eseguito in una sessione di debug nell'IDE. L'applicazione viene eseguita fino alla terminazione, fino a quando non viene raggiunto un punto di interruzione o fino a quando non viene generata un'eccezione. Quando l'applicazione viene eseguita al completamento, le transizioni DE in modalità progettazione. Quando viene raggiunto un punto di interruzione o viene generata un'eccezione, modalità di interruzione passa la Germania.  
  
##  <a name="vsconoperationalmodesanchor3"></a> Modalità di interruzione  
 Modalità di interruzione si verifica quando viene sospesa l'esecuzione del programma di debug. Modalità di interruzione offre allo sviluppatore dell'applicazione al momento dell'interruzione di uno snapshot e consente allo sviluppatore di analizzare lo stato dell'applicazione e modificare la modalità di esecuzione dell'applicazione. Lo sviluppatore può visualizzare e modificare il codice, esaminare o modificare i dati, riavviare l'applicazione, terminare l'esecuzione o continuare l'esecuzione dallo stesso punto.  
  
 Modalità di interruzione viene immesso quando la Germania invia un evento di arresto sincrono. Eventi di arresto sincrono, denominati anche gli eventi di arresto, inviare una notifica di gestore di sessione di debug (SDM) e l'IDE in cui l'applicazione in fase di debug ha interrotto l'esecuzione di codice. Il [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) e [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) interfacce sono esempi di eventi di arresto.  
  
 Gli eventi di arresto proseguono da una chiamata a uno dei metodi seguenti, eseguire la transizione dalla modalità di interruzione per l'esecuzione o in modalità di passaggio nel debugger:  
  
-   [Eseguire](../../extensibility/debugger/reference/idebugprocess3-execute.md)  
  
-   [Step](../../extensibility/debugger/reference/idebugprocess3-step.md)  
  
-   [Continue](../../extensibility/debugger/reference/idebugprocess3-continue.md)  
  
###  <a name="vsconoperationalmodesanchor4"></a> Modalità di passaggio  
 Modalità di passaggio si verifica quando il programma di passaggi alla riga successiva del codice, nel, in o da una funzione. Un passaggio viene eseguito chiamando il metodo [passaggio](../../extensibility/debugger/reference/idebugprocess3-step.md). Questo metodo richiede `DWORD`che specificano il [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) e [STEPKIND](../../extensibility/debugger/reference/stepkind.md) enumerazioni come parametri di input.  
  
 Quando il programma correttamente i passaggi alla riga successiva del codice o in una funzione o viene eseguito fino al cursore o a un punto di interruzione di set, la Germania sistema passa automaticamente alla modalità di interruzione.  
  
## <a name="see-also"></a>Vedere anche  
 [Controllo dell'esecuzione](../../extensibility/debugger/control-of-execution.md)