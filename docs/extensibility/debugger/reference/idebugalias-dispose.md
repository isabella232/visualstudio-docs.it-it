---
description: Contrassegna questo alias per la rimozione.
title: IDebugAlias::D di pose | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias::Dispose
helpviewer_keywords:
- IDebugAlias::Dispose method
ms.assetid: e84909a4-d378-4f48-bf25-2c014c77c8e3
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: efca2b2bedc531fa241d8cfe6cfe8cd3527a7b40
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143922"
---
# <a name="idebugaliasdispose"></a>IDebugAlias::Dispose
Contrassegna questo alias per la rimozione.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Dispose();
```

```csharp
int Dispose();
```

## <a name="parameters"></a>Parametri
 No.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 Quando viene chiamato questo metodo, l'alias non è più disponibile.

## <a name="see-also"></a>Vedi anche
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
