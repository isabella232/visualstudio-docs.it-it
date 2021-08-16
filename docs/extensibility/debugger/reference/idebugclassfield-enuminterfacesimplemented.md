---
description: Crea un enumeratore per le interfacce implementate da questa classe.
title: IDebugClassField::EnumInterfacesImplemented | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a3a94c5df7281227f1bb31767258c2fd11de38e68496d940a3df972605dcc0c9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121452251"
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
[out] Restituisce un [oggetto IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) che rappresenta l'elenco di interfacce implementate. Restituisce un valore Null se non sono presenti interfacce.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, S_OK restituisce S_FALSE se non sono presenti interfacce implementate in questa classe. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Commenti
 Ogni elemento dell'enumerazione è un oggetto [IDebugClassField che](../../../extensibility/debugger/reference/idebugclassfield.md) descrive un'interfaccia. Si noti che il codice non gestito non usa le interfacce come entità discreta, quindi questo metodo restituisce sempre un valore [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] Null per il codice non [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] gestito.

## <a name="see-also"></a>Vedi anche
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
