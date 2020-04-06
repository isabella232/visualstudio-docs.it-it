---
title: Proprietà IDebugProgramEx2 . Documenti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722338"
---
# <a name="idebugprogramex2"></a>IDebugProgramEx2
Questa interfaccia consente al gestore di sessione di debug (SDM) di connettersi a un programma e ottenere il nodo del programma associato a un programma.

## <a name="syntax"></a>Sintassi

```
IDebugProgramEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un fornitore di porta personalizzato implementa questa interfaccia sullo stesso oggetto di [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaccia per consentire il SDM connettersi a un programma, consentendo allo stesso tempo al fornitore della porta di tenere traccia di tutte le sessioni collegate al programma. Il fornitore della porta personalizzata può implementare questa interfaccia, se lo desidera.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Il modello SDM chiama `IDebugProgram2` [QueryInterface](/cpp/atl/queryinterface) su un'interfaccia per ottenere questa interfaccia per tenere traccia delle sessioni associate ai programmi.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono `IDebugProgramEx2`illustrati i metodi di .

|Metodo|Descrizione|
|------------|-----------------|
|[Attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|Associa un programma a una sessione.|
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|Ottiene il nodo del programma associato a un programma.|

## <a name="remarks"></a>Osservazioni
 Questa interfaccia è privata tra il sistema SDM e il programma.

## <a name="requirements"></a>Requisiti
 Intestazione: Portpriv.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
