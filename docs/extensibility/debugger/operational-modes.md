---
title: Modalità operative | Microsoft Docs
description: Informazioni sulle tre modalità in cui l'IDE può operare, ovvero modalità progettazione, modalità di esecuzione e modalità di interruzione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debug engines, modes
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 559df92545f4c14eb0575e7ef758e73028349b76
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899108"
---
# <a name="operational-modes"></a>Modalità operative
Esistono tre modalità in cui l'IDE può operare, come indicato di seguito:

- [Modalità progettazione](#vsconoperationalmodesanchor1)

- [Modalità di esecuzione](#vsconoperationalmodesanchor2)

- [Modalità di interruzione](#vsconoperationalmodesanchor3)

  Il modo in cui il motore di debug personalizzato (DE) esegue la transizione tra queste modalità è una decisione di implementazione che richiede di avere familiarità con i meccanismi di transizione. Il de può o meno implementare direttamente queste modalità. Queste modalità sono in realtà modalità di debug del pacchetto che passano in base all'azione dell'utente o agli eventi dal de. Ad esempio, la transizione dalla modalità di esecuzione alla modalità di interruzione viene attivata da un evento di arresto dal de. La transizione dalla modalità di interruzione alla modalità di esecuzione o passaggio viene attivata dall'utente che esegue operazioni come Step o Execute. Per altre informazioni sulle transizioni DE, vedere [Controllo dell'esecuzione.](../../extensibility/debugger/control-of-execution.md)

## <a name="design-mode"></a><a name="vsconoperationalmodesanchor1"></a> Modalità progettazione
 La modalità progettazione è lo stato non di Visual Studio di debug, durante il quale è possibile impostare le funzionalità di debug nell'applicazione.

 In modalità progettazione vengono usate solo alcune funzionalità di debug. Uno sviluppatore può scegliere di impostare punti di interruzione o creare espressioni di controllo. Il de non viene mai caricato o chiamato mentre l'IDE è in modalità progettazione. L'interazione con de viene eseguita solo durante le modalità di esecuzione e interruzione.

## <a name="run-mode"></a><a name="vsconoperationalmodesanchor2"></a> Modalità di esecuzione
 La modalità di esecuzione si verifica quando un programma viene eseguito in una sessione di debug nell'IDE. L'applicazione viene eseguita fino alla chiusura, fino a quando non viene raggiunto un punto di interruzione o fino a quando non viene generata un'eccezione. Quando l'applicazione viene eseguita fino alla chiusura, il de passa alla modalità progettazione. Quando viene raggiunto un punto di interruzione o viene generata un'eccezione, il de passa alla modalità di interruzione.

## <a name="break-mode"></a><a name="vsconoperationalmodesanchor3"></a> Modalità di interruzione
 La modalità di interruzione si verifica quando l'esecuzione del programma di debug viene sospesa. La modalità di interruzione offre allo sviluppatore uno snapshot dell'applicazione al momento dell'interruzione e consente allo sviluppatore di analizzare lo stato dell'applicazione e modificare la modalità di esecuzione dell'applicazione. Lo sviluppatore può visualizzare e modificare il codice, esaminare o modificare i dati, riavviare l'applicazione, terminare l'esecuzione o continuare l'esecuzione dallo stesso punto.

 La modalità di interruzione viene attivata quando il DE invia un evento di arresto sincrono. Gli eventi di arresto sincroni, denominati anche eventi di arresto, notificano al gestore di debug della sessione (SDM) e all'IDE che l'applicazione in fase di debug ha interrotto l'esecuzione del codice. Le [interfacce IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) e [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) sono esempi di eventi di arresto.

 Gli eventi di arresto vengono continuati da una chiamata a uno dei metodi seguenti, che esegue la transizione del debugger dalla modalità di interruzione alla modalità di esecuzione o passaggio:

- [Eseguire](../../extensibility/debugger/reference/idebugprocess3-execute.md)

- [Step](../../extensibility/debugger/reference/idebugprocess3-step.md)

- [Continua](../../extensibility/debugger/reference/idebugprocess3-continue.md)

### <a name="step-mode"></a><a name="vsconoperationalmodesanchor4"></a> Modalità passaggio
 La modalità passaggio si verifica quando il programma esegue il passaggio alla riga di codice successiva o all'interno, all'inizio o all'uscita da una funzione. Un passaggio viene eseguito chiamando il metodo [Step](../../extensibility/debugger/reference/idebugprocess3-step.md). Questo metodo richiede `DWORD` s che specificano le [enumerazioni STEPUNIT](../../extensibility/debugger/reference/stepunit.md) e [STEPKIND](../../extensibility/debugger/reference/stepkind.md) come parametri di input.

 Quando il programma passa correttamente alla riga di codice successiva o a una funzione oppure viene eseguito fino al cursore o a un punto di interruzione impostato, la funzione de passa automaticamente alla modalità di interruzione.

## <a name="see-also"></a>Vedere anche
- [Controllo dell'esecuzione](../../extensibility/debugger/control-of-execution.md)
