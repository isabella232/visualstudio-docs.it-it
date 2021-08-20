---
description: Questo metodo ottiene il contesto di memoria o l'oggetto che contiene il valore corrente del simbolo.
title: Interfaccia IDebugBinder::Bind | Microsoft Docs
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
ms.openlocfilehash: de3cbb35245fad317014136177a4a410edfb25b5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122104391"
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
