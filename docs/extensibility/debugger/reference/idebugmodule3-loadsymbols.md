---
title: IDebugModule3::LoadSymbols | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::LoadSymbols
helpviewer_keywords:
- IDebugModule3::LoadSymbols
ms.assetid: 7548c8c1-cbc6-48aa-a845-19058d4a85bb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e1b23e7b1ae837087db198795ffeda6a5827f045
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323849"
---
# <a name="idebugmodule3loadsymbols"></a>IDebugModule3::LoadSymbols
Carica i simboli per il modulo corrente.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT LoadSymbols(
   void
);
```

```csharp
int LoadSymbols();
```

## <a name="return-value"></a>Valore restituito
 Se il metodo ha esito positivo, restituisce `S_OK`. In caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Questo metodo carica i simboli dal percorso di ricerca corrente (che può essere modificata chiamando il [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md) (metodo)).

 Questo metodo è preferibile tramite il [ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md) (metodo).

## <a name="see-also"></a>Vedere anche
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
- [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)