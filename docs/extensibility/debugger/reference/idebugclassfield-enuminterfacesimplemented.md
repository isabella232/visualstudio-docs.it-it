---
title: IDebugClassField::EnumInterfacesImplemented | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumInterfacesImplemented
helpviewer_keywords:
- IDebugClassField::EnumInterfacesImplemented method
ms.assetid: e5523e45-d350-491e-a92c-fe0ca97d2052
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a5c951ac4f6f33495dad4136a1a09c11e639e029
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335361"
---
# <a name="idebugclassfieldenuminterfacesimplemented"></a>IDebugClassField::EnumInterfacesImplemented
Crea un enumeratore per le interfacce implementate da questa classe.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT EnumInterfacesImplemented( 
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumInterfacesImplemented(
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parametri
`ppEnum`\
[out] Restituisce un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) oggetto che rappresenta l'elenco di interfacce implementate. Restituisce un valore null se non sono presenti interfacce.

## <a name="return-value"></a>Valore restituito
 Se l'operazione riesce, restituisce S_OK o restituisce S_FALSE se non sono presenti interfacce implementate sulla classe. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Note
 Ogni elemento dell'enumerazione è un [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) oggetto che descrive un'interfaccia. Si noti che non gestiti [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] codice non usa le interfacce come entità distinta in modo che questo metodo restituisce sempre un valore null per non gestito [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] codice.

## <a name="see-also"></a>Vedere anche
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)