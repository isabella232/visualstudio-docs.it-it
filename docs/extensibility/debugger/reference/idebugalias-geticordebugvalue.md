---
description: Recupera un'interfaccia di codice gestito che rappresenta il valore associato a questo alias.
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
ms.openlocfilehash: b809e16fefb9306da842f39d93bdb3dd0f7b404f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143935"
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
