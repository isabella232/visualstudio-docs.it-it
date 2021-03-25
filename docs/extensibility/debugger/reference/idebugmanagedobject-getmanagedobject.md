---
description: Restituisce un'interfaccia che rappresenta l'oggetto gestito.
title: 'IDebugManagedObject:: GetManagedObject | Microsoft Docs'
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
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1aea4f233160f9bdcc5c18c1dda16b4e3f361540
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076940"
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
out Restituisce un'interfaccia che rappresenta l'oggetto gestito.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 L'interfaccia restituita da questo metodo può essere sottoposta a query per qualsiasi interfaccia implementata dalla classe gestita, consentendo la chiamata dei metodi.

## <a name="see-also"></a>Vedi anche
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
