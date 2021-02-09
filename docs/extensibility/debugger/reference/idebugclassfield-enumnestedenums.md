---
title: 'IDebugClassField:: EnumNestedEnums | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedEnums
helpviewer_keywords:
- IDebugClassField::EnumNestedEnums method
ms.assetid: 90fd0cef-9145-4de6-91d4-6c881df39d6e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b9c283d4b07458368a4ea5f143dc83bf13453302
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912012"
---
# <a name="idebugclassfieldenumnestedenums"></a>IDebugClassField::EnumNestedEnums
Crea un enumeratore per gli enumeratori annidati di questa classe.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT EnumNestedEnums(
    IEnumDebugFields** ppEnum
);
```

```csharp
int EnumNestedEnums(
    out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parametri
`ppEnum`\
out Restituisce un oggetto [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) che rappresenta l'elenco di enumerazioni annidate. Restituisce un valore null se non sono presenti enumerazioni annidate.

## <a name="return-value"></a>Valore restituito
Se ha esito positivo, restituisce S_OK o restituisce S_FALSE se non sono presenti enumeratori annidati. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Commenti
Ogni elemento dell'enumerazione è un oggetto [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) che descrive un'enumerazione annidata.

Un'enumerazione dichiarata all'interno di una classe è considerata un'enumerazione annidata. Si consideri ad esempio di avere una situazione simile alla seguente:

```
class RootClass {
    enum NestedEnum { EnumValue = 0 }
};
```

Il `EnumNestedEnums` metodo restituisce un oggetto [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) che contiene un oggetto [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) che rappresenta l' `NestedEnum` enumerazione.

## <a name="see-also"></a>Vedi anche
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
