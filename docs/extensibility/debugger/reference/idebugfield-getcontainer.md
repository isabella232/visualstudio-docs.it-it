---
title: 'IDebugField:: GetContainer | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetContainer
helpviewer_keywords:
- IDebugField::GetContainer method
ms.assetid: 6d6c8213-6181-4adf-9584-3e4cac163dd8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d9d14a5666db03c9ebd701d5e1145c3f14465e37
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99915409"
---
# <a name="idebugfieldgetcontainer"></a>IDebugField::GetContainer
Questo metodo ottiene il contenitore di un campo.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetContainer( 
   IDebugContainerField** ppContainerField
);
```

```csharp
int GetContainer(
   out IDebugContainerField ppContainerField
);
```

## <a name="parameters"></a>Parametri
`ppContainerField`\
out Restituisce il contenitore come rappresentato dall'interfaccia [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) .

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Se questo campo non dispone di un contenitore, l'oggetto restituito `ppContainerField` sarà un valore null.

## <a name="see-also"></a>Vedi anche
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
