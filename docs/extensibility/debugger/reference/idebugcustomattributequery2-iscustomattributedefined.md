---
title: IDebugCustomAttributeQuery2::IsCustomAttributeDefined | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
helpviewer_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
ms.assetid: 5c07cc52-6d2d-42df-9d76-9f1f769641db
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6695753fa1b071f8623b079dbe4e56e68e9dfad4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62876024"
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

#### <a name="parameters"></a>Parametri
 `pszCustomAttributeName`

 [in] Stringa contenente il nome dell'attributo personalizzato da trovare.

## <a name="return-value"></a>Valore restituito
 Restituisce che S_OK se l'attributo personalizzato viene definito per questo campo, in caso contrario, restituisce S_FALSE.

## <a name="remarks"></a>Note
 Per ottenere i byte di attributo associati all'attributo personalizzato, chiamare il [GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md) (metodo).

## <a name="see-also"></a>Vedere anche
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)