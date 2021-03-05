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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5f90bf6efc3a34e4f6b9f60ef5bdadb0640f495b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164318"
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
