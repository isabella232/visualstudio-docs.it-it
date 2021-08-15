---
description: Disconnette il debugger da questo processo scollegando tutti i programmi nel processo.
title: IDebugProcess2::D etach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::Detach
helpviewer_keywords:
- IDebugProcess2::Detach
ms.assetid: ee2b9084-2db1-4e49-a1d9-387284b7c3f8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 957579bb2a19bffb0774ecd400218e5f8105127734969c26c43772dbea743bdc
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121276867"
---
# <a name="idebugprocess2detach"></a>IDebugProcess2::Detach
Disconnette il debugger da questo processo scollegando tutti i programmi nel processo.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Detach( 
   void 
);
```

```csharp
int Detach();
```

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Tutti i programmi e il processo continuano l'esecuzione, ma non fanno più parte della sessione di debug. Al termine dell'operazione di scollegamento, non verranno inviati altri eventi di debug per questo processo (e i relativi programmi).

## <a name="see-also"></a>Vedi anche
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
