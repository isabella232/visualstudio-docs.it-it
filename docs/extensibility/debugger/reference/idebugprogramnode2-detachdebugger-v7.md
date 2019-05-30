---
title: IDebugProgramNode2::DetachDebugger_V7 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 241db5db55897932120b3253ff5185cb852ea77b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351213"
---
# <a name="idebugprogramnode2detachdebuggerv7"></a>IDebugProgramNode2::DetachDebugger_V7

> [!Note]
> DEPRECATO. NON USARE.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT DetachDebugger_V7 (
   void 
);
```

```csharp
int DetachDebugger_V7 ();
```

## <a name="return-value"></a>Valore restituito

Un'implementazione deve sempre restituire `E_NOTIMPL`.

## <a name="remarks"></a>Note

> [!WARNING]
> A partire da Visual Studio 2005, questo metodo non viene più usato e deve sempre restituire `E_NOTIMPL`.

Questo metodo viene chiamato quando il debugger viene chiuso in modo imprevisto. Quando questo metodo viene chiamato, la Germania deve essere ripreso il programma come se l'utente disconnesso da quest'ultimo. Nessun altro evento di debug deve essere inviato. Il programma deve essere in uno stato in cui è associabile da un'altra istanza del debugger.

## <a name="see-also"></a>Vedere anche

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)