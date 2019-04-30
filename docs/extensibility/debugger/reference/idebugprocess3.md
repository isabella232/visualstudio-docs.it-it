---
title: IDebugProcess3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3
helpviewer_keywords:
- IDebugProcess3 interface
ms.assetid: 7bd6b952-cf34-4e66-b8f6-d472dac3748f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ca5c9294924b99f830ed05234c68bdba0e7a61a1
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63412884"
---
# <a name="idebugprocess3"></a>IDebugProcess3
Questa interfaccia rappresenta un processo in esecuzione e i relativi programmi. Questa interfaccia è presente come una sostituzione per vari metodi di [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaccia. Fornisce controllo su tutti i programmi nel processo.

> [!NOTE]
> [Continuare](../../../extensibility/debugger/reference/idebugprogram2-continue.md), [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md), e [passaggio](../../../extensibility/debugger/reference/idebugprogram2-step.md) metodi sono deprecati e non devono più essere utilizzati. Uso dei corrispondenti metodi on il `IDebugProcess3` invece dell'interfaccia.

## <a name="syntax"></a>Sintassi

```
IDebugProcess3 : IDebugProcess2
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia viene implementata da un fornitore di porte personalizzate per i programmi sono gestiti come gruppo. Quando programmi vengono gestiti come gruppo, è possibile controllare l'esecuzione e stabilire una lingua per un analizzatore di espressioni. Questa interfaccia deve essere implementata dal fornitore della porta.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia viene chiamata principalmente dal gestore di sessione di debug (SDM) per interagire con un gruppo di programmi identificate in questo processo.

 Chiamare [QueryInterface](/cpp/atl/queryinterface) in un [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) interfaccia per ottenere questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Oltre ai metodi ereditati da [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md), `IDebugProcess3` implementa i metodi seguenti.

|Metodo|Descrizione|
|------------|-----------------|
|[Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|Continua l'esecuzione di o avanzando istruzione per un processo.|
|[Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|Inizia l'esecuzione di un processo.|
|[Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)|Passaggi di inoltrare una istruzione o istruzione nel processo.|
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|Ottiene il motivo che è stato avviato il processo per eseguire il debug.|
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|Imposta la lingua di hosting in modo che il motore di debug è possibile caricare l'analizzatore di espressioni appropriato.|
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|Recupera la lingua attualmente impostata per questo processo.|
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|Disabilita modifica e Continuazione per questo processo.<br /><br /> Un fornitore di porte personalizzato può neimplementuje metodu questo metodo (l'app deve sempre restituire `E_NOTIMPL`).|
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|Ottenere lo stato ENC per questo processo.<br /><br /> Un fornitore di porte personalizzato può neimplementuje metodu questo metodo (l'app deve sempre restituire `E_NOTIMPL`).|
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|Recupera una matrice di identificatori univoci per i motori di debug disponibili.|

## <a name="requirements"></a>Requisiti
 Intestazione: Msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)