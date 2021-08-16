---
description: Questa interfaccia consente al gestore di debug di sessione (SDM) di connettersi a un programma e di ottenere il nodo del programma associato a un programma.
title: Interfaccia IDebugProgramEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2
helpviewer_keywords:
- IDebugProgramEx2 interface
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 1c1cff5e18dfca2838595848c2ae4f18c076441ec51ed78e93e467bdbbca9f8b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121276399"
---
# <a name="idebugprogramex2"></a>IDebugProgramEx2
Questa interfaccia consente al gestore di debug di sessione (SDM) di connettersi a un programma e di ottenere il nodo del programma associato a un programma.

## <a name="syntax"></a>Sintassi

```
IDebugProgramEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un fornitore di porte personalizzato implementa questa interfaccia sullo stesso oggetto dell'interfaccia [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) per consentire a SDM di connettersi a un programma consentendo al fornitore della porta di tenere traccia di tutte le sessioni collegate al programma. Il fornitore di porte personalizzato può implementare questa interfaccia, se lo desidera.

## <a name="notes-for-callers"></a>Note per i chiamanti
 SDM chiama [QueryInterface](/cpp/atl/queryinterface) su un'interfaccia per ottenere questa interfaccia per tenere traccia delle sessioni `IDebugProgram2` collegate ai programmi.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IDebugProgramEx2` .

|Metodo|Descrizione|
|------------|-----------------|
|[Attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|Collega un programma a una sessione.|
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|Ottiene il nodo del programma associato a un programma.|

## <a name="remarks"></a>Commenti
 Questa interfaccia è privata tra SDM e il programma.

## <a name="requirements"></a>Requisiti
 Intestazione: Portpriv.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
