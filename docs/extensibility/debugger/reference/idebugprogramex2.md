---
title: IDebugProgramEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2
helpviewer_keywords:
- IDebugProgramEx2 interface
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b8961ea105779674aab0b67c9ad6339ce1c282f9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722338"
---
# <a name="idebugprogramex2"></a>IDebugProgramEx2
Questa interfaccia consente al gestore di debug della sessione di connettersi a un programma e di ottenere il nodo del programma associato a un programma.

## <a name="syntax"></a>Sintassi

```
IDebugProgramEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un fornitore di porte personalizzato implementa questa interfaccia sullo stesso oggetto dell'interfaccia [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) per consentire a SDM di connettersi a un programma consentendo allo stesso tempo al fornitore della porta di tenere traccia di tutte le sessioni associate al programma. Il fornitore della porta personalizzata può implementare questa interfaccia se viene scelta.

## <a name="notes-for-callers"></a>Note per i chiamanti
 SDM chiama [QueryInterface](/cpp/atl/queryinterface) su un' `IDebugProgram2` interfaccia per ottenere questa interfaccia per tenere traccia delle sessioni associate ai programmi.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 La tabella seguente illustra i metodi di `IDebugProgramEx2` .

|Metodo|Descrizione|
|------------|-----------------|
|[Attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|Connette un programma a una sessione.|
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|Ottiene il nodo di programma associato a un programma.|

## <a name="remarks"></a>Osservazioni
 Questa interfaccia è privata tra il SDM e il programma.

## <a name="requirements"></a>Requisiti
 Intestazione: Portpriv. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
