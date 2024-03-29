---
title: Modalità operative | Microsoft Docs
description: Informazioni sulle tre modalità di funzionamento dell'IDE, ovvero modalità progettazione, modalità di esecuzione e modalità di interruzione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debug engines, modes
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 0af5f083c54fbb587bcbed52bc59968ee0477e5f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710327"
---
# <a name="operational-modes"></a>Modalità operative
Esistono tre modalità in cui l'IDE può funzionare, come indicato di seguito:

- [Modalità progettazione](#vsconoperationalmodesanchor1)

- [Modalità di esecuzione](#vsconoperationalmodesanchor2)

- [Modalità di interruzione](#vsconoperationalmodesanchor3)

  La modalità di transizione del motore di debug personalizzato tra queste modalità è una decisione di implementazione che richiede una certa familiarità con i meccanismi di transizione. De può implementare o meno direttamente queste modalità. Queste modalità sono effettivamente modalità di debug del pacchetto che passano in base all'azione dell'utente o agli eventi da DE. Ad esempio, la transizione dalla modalità di esecuzione alla modalità di interruzione viene attivata da un evento di arresto da DE. La transizione dalla modalità di interruzione alla modalità di esecuzione o passaggio viene attivata dall'utente che esegue operazioni come Step o Execute. Per altre informazioni sulle transizioni DE, vedere [Controllo dell'esecuzione.](../../extensibility/debugger/control-of-execution.md)

## <a name="design-mode"></a><a name="vsconoperationalmodesanchor1"></a> Modalità progettazione
 La modalità progettazione è lo stato non di esecuzione Visual Studio debug, durante il quale è possibile impostare le funzionalità di debug nell'applicazione.

 Durante la modalità progettazione vengono usate solo alcune funzionalità di debug. Uno sviluppatore può scegliere di impostare punti di interruzione o creare espressioni di controllo. De non viene mai caricato o chiamato mentre l'IDE è in modalità progettazione. L'interazione con DE avviene solo durante le modalità di esecuzione e interruzione.

## <a name="run-mode"></a><a name="vsconoperationalmodesanchor2"></a> Modalità di esecuzione
 La modalità di esecuzione si verifica quando un programma viene eseguito in una sessione di debug nell'IDE. L'applicazione viene eseguita fino alla chiusura, fino a quando non viene raggiunto un punto di interruzione o fino a quando non viene generata un'eccezione. Quando l'applicazione viene eseguita fino alla chiusura, de passa alla modalità progettazione. Quando viene raggiunto un punto di interruzione o viene generata un'eccezione, de passa alla modalità di interruzione.

## <a name="break-mode"></a><a name="vsconoperationalmodesanchor3"></a> Modalità di interruzione
 La modalità di interruzione si verifica quando l'esecuzione del programma di debug viene sospesa. La modalità di interruzione offre allo sviluppatore uno snapshot dell'applicazione al momento dell'interruzione e consente allo sviluppatore di analizzare lo stato dell'applicazione e modificare la modalità di esecuzione dell'applicazione. Lo sviluppatore può visualizzare e modificare il codice, esaminare o modificare i dati, riavviare l'applicazione, terminare l'esecuzione o continuare l'esecuzione dallo stesso punto.

 La modalità di interruzione viene attivata quando DE invia un evento di arresto sincrono. Gli eventi di arresto sincroni, detti anche eventi di arresto, notificano a Gestione debug sessione (SDM) e all'IDE che l'applicazione in fase di debug ha interrotto l'esecuzione del codice. Le [interfacce IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) e [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) sono esempi di eventi di arresto.

 Gli eventi di arresto vengono continuati da una chiamata a uno dei metodi seguenti, che esegue la transizione del debugger dalla modalità di interruzione alla modalità di esecuzione o di esecuzione:

- [Eseguire](../../extensibility/debugger/reference/idebugprocess3-execute.md)

- [Step](../../extensibility/debugger/reference/idebugprocess3-step.md)

- [Continua](../../extensibility/debugger/reference/idebugprocess3-continue.md)

### <a name="step-mode"></a><a name="vsconoperationalmodesanchor4"></a> Modalità passaggio
 La modalità passaggio si verifica quando il programma esegue il passaggio alla riga di codice successiva o all'interno, all'over o all'uscita da una funzione. Un passaggio viene eseguito chiamando il metodo [Step](../../extensibility/debugger/reference/idebugprocess3-step.md). Questo metodo richiede `DWORD` che gli oggetti che specificano le [enumerazioni STEPUNIT](../../extensibility/debugger/reference/stepunit.md) e [STEPKIND](../../extensibility/debugger/reference/stepkind.md) come parametri di input.

 Quando il programma passa correttamente alla riga di codice successiva o a una funzione oppure viene eseguito fino al cursore o a un punto di interruzione impostato, de passa automaticamente alla modalità di interruzione.

## <a name="see-also"></a>Vedi anche
- [Controllo dell'esecuzione](../../extensibility/debugger/control-of-execution.md)
