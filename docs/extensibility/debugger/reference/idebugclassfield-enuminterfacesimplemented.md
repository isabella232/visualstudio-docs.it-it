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
ms.openlocfilehash: 8395a35a2f0e5aa7481148562dc12b66da39e257
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122064565"
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
 In caso di esito positivo, restituisce S_OK o restituisce S_FALSE se non sono presenti interfacce implementate in questa classe. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Commenti
 Ogni elemento dell'enumerazione è un [oggetto IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) che descrive un'interfaccia. Si noti che il codice non gestito non usa le interfacce come entità discreta, pertanto questo metodo restituisce sempre un valore [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] Null per il codice non [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] gestito.

## <a name="see-also"></a>Vedi anche
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
