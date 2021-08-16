---
description: Questo metodo ottiene il contesto di memoria o l'oggetto che contiene il valore corrente del simbolo.
title: IDebugBinder::Bind | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::Bind
helpviewer_keywords:
- IDebugBinder::Bind method
ms.assetid: 15a11ad7-0fcc-4e80-ae34-8a7dd7bae3c3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e6efe8d946721c11a664c89aefdb21fd4c8b513dd6d99c6f8680970a80e692ea
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121403026"
---
# <a name="idebugbinderbind"></a>IDebugBinder::Bind
Questo metodo ottiene il contesto di memoria o l'oggetto che contiene il valore corrente del simbolo.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Bind( 
   IDebugObject*  pContainer,
   IDebugField*   pField,
   IDebugObject** ppObject
);
```

```csharp
int Bind(
   IDebugObject     pContainer,
   IDebugField      pField,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parametri
`pContainer`\
[in] Oggetto [IDebugObject che](../../../extensibility/debugger/reference/idebugobject.md) contiene l'elemento figlio a cui fa riferimento `pField` .

`pField`\
[in] Oggetto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) che rappresenta il simbolo.

`ppObject`\
[out] Restituisce `IDebugObject` l'oggetto che rappresenta l'istanza del simbolo.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
