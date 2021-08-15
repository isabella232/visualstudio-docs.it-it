---
description: Restituisce un'interfaccia che rappresenta l'oggetto gestito.
title: Oggetto IDebugManagedObject::GetManagedObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject::GetManagedObject
helpviewer_keywords:
- IDebugManagedObject::GetManagedObject method
ms.assetid: 6abe1402-6aad-41e6-8ec1-ae12d5945992
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d4692d2f639d0f9feb0f47248ffaa3b7209594e97fc767136b32b422de5912a7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121238827"
---
# <a name="idebugmanagedobjectgetmanagedobject"></a>IDebugManagedObject::GetManagedObject
Restituisce un'interfaccia che rappresenta l'oggetto gestito.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetManagedObject( 
   IUnknown** ppManagedObject
);
```

```cpp
int GetManagedObject(
   out object ppManagedObject
);
```

## <a name="parameters"></a>Parametri
`ppManagedObject`\
[out] Restituisce un'interfaccia che rappresenta l'oggetto gestito.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; In caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 È possibile eseguire query sull'interfaccia restituita da questo metodo per qualsiasi interfaccia implementata dalla classe gestita, consentendo la chiamata dei relativi metodi.

## <a name="see-also"></a>Vedi anche
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
