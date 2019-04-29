---
title: IDebugClassField::EnumInterfacesImplemented | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumInterfacesImplemented
helpviewer_keywords:
- IDebugClassField::EnumInterfacesImplemented method
ms.assetid: e5523e45-d350-491e-a92c-fe0ca97d2052
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bffae40f1e5212132c89b6b71b7fc83cca6ebb42
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62877025"
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

#### <a name="parameters"></a>Parametri
 `ppEnum`

 [out] Restituisce un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) oggetto che rappresenta l'elenco di interfacce implementate. Restituisce un valore null se non sono presenti interfacce.

## <a name="return-value"></a>Valore restituito
 Se l'operazione riesce, restituisce S_OK o restituisce S_FALSE se non sono presenti interfacce implementate sulla classe. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Note
 Ogni elemento dell'enumerazione è un [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) oggetto che descrive un'interfaccia. Si noti che non gestiti [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] codice non usa le interfacce come entità distinta in modo che questo metodo restituisce sempre un valore null per non gestito [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] codice.

## <a name="see-also"></a>Vedere anche
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)