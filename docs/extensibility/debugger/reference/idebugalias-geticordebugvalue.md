---
title: 'IDebugAlias:: GetICorDebugValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias::GetICorDebugValue
helpviewer_keywords:
- IDebugAlias::GetICorDebugValue method
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2ba5456ba3beabb1d5418d739be2aa74838daa41
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947177"
---
# <a name="idebugaliasgeticordebugvalue"></a>IDebugAlias::GetICorDebugValue
Recupera un'interfaccia di codice gestito che rappresenta il valore associato a questo alias.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetICorDebugValue(
   IUnknown** ppUnk
);
```

```csharp
int GetICorDebugValue(
   out object ppUnk
);
```

## <a name="parameters"></a>Parametri
`ppUnk`\
[out] `IUnknown` interfaccia che rappresenta il valore associato a questo alias. È possibile eseguire query su questa interfaccia per l' `ICorDebugValue` interfaccia.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 Questo metodo si applica solo ai valori gestiti ( `ICorDebugValue` è un'interfaccia disponibile nel .NET Framework e viene definito in .NET Framework SDK nel file CorDebug. idl).

## <a name="see-also"></a>Vedi anche
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
