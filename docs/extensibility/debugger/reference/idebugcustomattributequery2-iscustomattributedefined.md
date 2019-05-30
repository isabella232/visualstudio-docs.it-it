---
title: IDebugCustomAttributeQuery2::IsCustomAttributeDefined | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
helpviewer_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
ms.assetid: 5c07cc52-6d2d-42df-9d76-9f1f769641db
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0e2ecd70eeeddb4b61d8ed8d307bd579c68ef519
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335834"
---
# <a name="idebugcustomattributequery2iscustomattributedefined"></a>IDebugCustomAttributeQuery2::IsCustomAttributeDefined
Determina l'esistenza di un attributo personalizzato in base al nome.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT IsCustomAttributeDefined( 
   LPCOLESTR pszCustomAttributeName
);
```

```csharp
int IsCustomAttributeDefined(
   [In] string pszCustomAttributeName
);
```

## <a name="parameters"></a>Parametri
`pszCustomAttributeName`\
[in] Stringa contenente il nome dell'attributo personalizzato da trovare.

## <a name="return-value"></a>Valore restituito
 Restituisce che S_OK se l'attributo personalizzato viene definito per questo campo, in caso contrario, restituisce S_FALSE.

## <a name="remarks"></a>Note
 Per ottenere i byte di attributo associati all'attributo personalizzato, chiamare il [GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md) (metodo).

## <a name="see-also"></a>Vedere anche
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)