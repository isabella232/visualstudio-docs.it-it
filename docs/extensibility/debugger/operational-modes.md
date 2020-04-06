---
title: Modalità operative Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, modes
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 027152b2b2fc18b509a687220e5d963ea1b7e721
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738288"
---
# <a name="operational-modes"></a>Modalità operative
Esistono tre modalità in cui l'IDE può funzionare, come indicato di seguito:There are three modes in which the IDE can operate, as follows:

- [Modalità di progettazione](#vsconoperationalmodesanchor1)

- [Modalità di esecuzione](#vsconoperationalmodesanchor2)

- [Modalità di interruzione](#vsconoperationalmodesanchor3)

  Il modo in cui il motore di debug personalizzato (DE) esegue la transizione tra queste modalità è una decisione di implementazione che richiede di avere familiarità con i meccanismi di transizione. Il DE può o non può implementare direttamente queste modalità. Queste modalità sono davvero le modalità di pacchetto di debug che passano in base all'azione dell'utente o eventi dal DE. Ad esempio, la transizione dalla modalità di esecuzione alla modalità di interruzione viene avviata da un evento di arresto dal DE. La transizione dalla modalità di interruzione alla modalità di esecuzione o alla modalità di passaggio viene avviata dall'utente che esegue operazioni quali Step o Execute.The transition from break to either run mode or step mode is stigated by the user performing operations such as Step or Execute. Per ulteriori informazioni sulle transizioni DE, vedere [Controllo dell'esecuzione](../../extensibility/debugger/control-of-execution.md).

## <a name="design-mode"></a><a name="vsconoperationalmodesanchor1"></a>Modalità di progettazione
 La modalità di progettazione è lo stato non in esecuzione del debug di Visual Studio, durante il quale è possibile impostare le funzionalità di debug nell'applicazione.

 Durante la modalità progettazione vengono utilizzate solo alcune funzionalità di debug. Uno sviluppatore può scegliere di impostare punti di interruzione o creare espressioni di controllo. Il DE non viene mai caricato o chiamato mentre l'IDE è in modalità progettazione. L'interazione con il DE avviene solo durante le modalità di esecuzione e interruzione.

## <a name="run-mode"></a><a name="vsconoperationalmodesanchor2"></a>Modalità di esecuzione
 La modalità di esecuzione si verifica quando un programma viene eseguito in una sessione di debug nell'IDE. L'applicazione viene eseguita fino alla terminazione, fino a quando non viene raggiunto un punto di interruzione o fino a quando non viene generata un'eccezione. Quando l'applicazione viene eseguita alla terminazione, il DE passa alla modalità di progettazione. Quando viene raggiunto un punto di interruzione o viene generata un'eccezione, il DE passa alla modalità di interruzione.

## <a name="break-mode"></a><a name="vsconoperationalmodesanchor3"></a>Modalità di interruzione
 La modalità di interruzione si verifica quando l'esecuzione del programma di debug viene sospesa. La modalità di interruzione offre allo sviluppatore uno snapshot dell'applicazione al momento dell'interruzione e consente allo sviluppatore di analizzare lo stato dell'applicazione e modificare la modalità di esecuzione dell'applicazione. Lo sviluppatore può visualizzare e modificare il codice, esaminare o modificare i dati, riavviare l'applicazione, terminare l'esecuzione o continuare l'esecuzione dallo stesso punto.

 La modalità di interruzione viene immessa quando il DE invia un evento di arresto sincrono. Gli eventi di arresto sincrono, denominati anche eventi di arresto, notificano al gestore di debug della sessione (SDM) e all'IDE che l'applicazione sottoposta a debug ha interrotto l'esecuzione del codice. Le interfacce [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) e [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) sono esempi di interruzione degli eventi.

 L'arresto degli eventi continua da una chiamata a uno dei metodi seguenti, che consentono al debugger di eseguire la modalità di interruzione alla modalità di interruzione o alla modalità istruzione/passaggio:

- [Eseguire](../../extensibility/debugger/reference/idebugprocess3-execute.md)

- [Passaggio](../../extensibility/debugger/reference/idebugprocess3-step.md)

- [Continuare](../../extensibility/debugger/reference/idebugprocess3-continue.md)

### <a name="step-mode"></a><a name="vsconoperationalmodesanchor4"></a>Modalità passo
 La modalità passo a passo si verifica quando il programma passare alla riga di codice successiva, o in, sopra o fuori da una funzione. Un passaggio viene eseguito chiamando il metodo [Step](../../extensibility/debugger/reference/idebugprocess3-step.md). Questo metodo `DWORD`richiede s che specificano le enumerazioni [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) e [STEPKIND](../../extensibility/debugger/reference/stepkind.md) come parametri di input.

 Quando il programma passa correttamente alla riga di codice successiva o in una funzione o viene eseguito al cursore o a un punto di interruzione impostato, il DE passa automaticamente alla modalità di interruzione.

## <a name="see-also"></a>Vedere anche
- [Controllo dell'esecuzione](../../extensibility/debugger/control-of-execution.md)
