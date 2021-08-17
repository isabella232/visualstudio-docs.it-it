---
description: Contrassegna questo alias per la rimozione.
title: IDebugAlias::D ispose | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias::Dispose
helpviewer_keywords:
- IDebugAlias::Dispose method
ms.assetid: e84909a4-d378-4f48-bf25-2c014c77c8e3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e15d2c6f74c4872c5e55c9ce76293a1ab097d3176be33843a4deea89a692664c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121434217"
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
 Se ha esito positivo, restituisce S_OK; In caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 Una volta chiamato questo metodo, l'alias non è più disponibile.

## <a name="see-also"></a>Vedi anche
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
