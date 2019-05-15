---
title: IDebugBinder::Bind | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::Bind
helpviewer_keywords:
- IDebugBinder::Bind method
ms.assetid: 15a11ad7-0fcc-4e80-ae34-8a7dd7bae3c3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e3db6a0f5977591b12cb3c77bd1791905f82a087
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/14/2019
ms.locfileid: "65615207"
---
# <a name="idebugbinderbind"></a>IDebugBinder::Bind
Questo metodo ottiene il contesto in memoria o un oggetto che contiene valore corrente del simbolo.

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
[in] Il [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) che contiene l'elemento figlio a cui fanno riferimento `pField`.

`pField`\
[in] Il [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) che rappresenta il simbolo.

`ppObject`\
[out] Restituisce il `IDebugObject` che rappresenta l'istanza del simbolo.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)