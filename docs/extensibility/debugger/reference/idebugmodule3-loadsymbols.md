---
description: Carica i simboli per il modulo corrente.
title: IDebugModule3::LoadSymbols | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::LoadSymbols
helpviewer_keywords:
- IDebugModule3::LoadSymbols
ms.assetid: 7548c8c1-cbc6-48aa-a845-19058d4a85bb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2b332182574f9801f1a1ef6eb139d46958851d725191bc1355f800c8161b1183
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121307297"
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
 Se il metodo ha esito positivo, viene restituito `S_OK`. Se ha esito negativo, viene restituito un codice di errore.

## <a name="remarks"></a>Commenti
 Questo metodo carica i simboli dal percorso di ricerca corrente (che può essere modificato chiamando il [metodo SetSymbolPath).](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)

 Questo metodo è preferibile rispetto [ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md) metodo .

## <a name="see-also"></a>Vedi anche
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
- [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)
