---
description: Questo metodo ottiene il contesto di memoria o l'oggetto che contiene il valore corrente del simbolo.
title: 'IDebugBinder:: bind | Microsoft Docs'
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
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 859ee8d474b25533d990c92e4c4f038d2a62f987
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067432"
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
in [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) che contiene l'elemento figlio a cui fa riferimento `pField` .

`pField`\
in [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) che rappresenta il simbolo.

`ppObject`\
out Restituisce l'oggetto `IDebugObject` che rappresenta l'istanza del simbolo.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
