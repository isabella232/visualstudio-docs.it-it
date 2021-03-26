---
description: Crea un enumeratore per le interfacce implementate da questa classe.
title: 'IDebugClassField:: EnumInterfacesImplemented | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumInterfacesImplemented
helpviewer_keywords:
- IDebugClassField::EnumInterfacesImplemented method
ms.assetid: e5523e45-d350-491e-a92c-fe0ca97d2052
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1763cbcd0a1c61150a054752c94a42f10127251a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088614"
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
out Restituisce un oggetto [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) che rappresenta l'elenco di interfacce implementate. Restituisce un valore null se non sono presenti interfacce.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK o restituisce S_FALSE se non sono implementate interfacce in questa classe. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Commenti
 Ogni elemento dell'enumerazione è un oggetto [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) che descrive un'interfaccia. Si noti che il codice non gestito non [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] Usa le interfacce come entità discreta, quindi questo metodo restituisce sempre un valore null per il [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] codice non gestito.

## <a name="see-also"></a>Vedi anche
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
