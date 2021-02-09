---
title: IDebugProcess3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3
helpviewer_keywords:
- IDebugProcess3 interface
ms.assetid: 7bd6b952-cf34-4e66-b8f6-d472dac3748f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6199c959a7186a1c10d6efdc30bb0763941c347a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99926119"
---
# <a name="idebugprocess3"></a>IDebugProcess3
Questa interfaccia rappresenta un processo in esecuzione e i relativi programmi. Questa interfaccia esiste come sostituzione di diversi metodi nell'interfaccia [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) . Fornisce il controllo su tutti i programmi nel processo.

> [!NOTE]
> I metodi [continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md), [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)e [Step](../../../extensibility/debugger/reference/idebugprogram2-step.md) sono deprecati e non devono più essere utilizzati. Usare invece i metodi corrispondenti nell' `IDebugProcess3` interfaccia.

## <a name="syntax"></a>Sintassi

```
IDebugProcess3 : IDebugProcess2
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia viene implementata da un fornitore di porte personalizzato per gestire i programmi come un gruppo. Quando i programmi vengono gestiti come un gruppo, è possibile controllarne l'esecuzione e stabilire una lingua per un analizzatore di espressioni. Questa interfaccia deve essere implementata dal fornitore della porta.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia viene chiamata principalmente da gestione debug sessione (SDM) per interagire con un gruppo di programmi identificato in questo processo.

 Chiamare [QueryInterface](/cpp/atl/queryinterface) su un'interfaccia [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) per ottenere questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Oltre ai metodi ereditati da [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md), `IDebugProcess3` implementa i metodi seguenti.

|Metodo|Descrizione|
|------------|-----------------|
|[Continua](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|Continua l'esecuzione o l'esecuzione di un processo.|
|[Eseguire](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|Inizia l'esecuzione di un processo.|
|[Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)|Segue un'istruzione o un'istruzione nel processo.|
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|Ottiene il motivo per cui il processo è stato avviato per il debug.|
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|Imposta la lingua di hosting in modo che il motore di debug possa caricare l'analizzatore di espressioni appropriato.|
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|Recupera la lingua attualmente impostata per questo processo.|
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|Disabilita la funzionalità di modifica e continuazione (ENC) per questo processo.<br /><br /> Un fornitore di porte personalizzato non implementa questo metodo (deve sempre restituire `E_NOTIMPL` ).|
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|Ottenere lo stato ENC per questo processo.<br /><br /> Un fornitore di porte personalizzato non implementa questo metodo (deve sempre restituire `E_NOTIMPL` ).|
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|Recupera una matrice di identificatori univoci per i motori di debug disponibili.|

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
