---
description: Determina se un motore di debug (DE) può scollegarsi dal programma.
title: IDebugProgram2::CanDetach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::CanDetach
helpviewer_keywords:
- IDebugProgram2::CanDetach
ms.assetid: dcd9ab6c-49e5-447e-aa7c-89f571f4a052
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 45d4bef36f5b1e283d654bcee4b6eaac09becd6b7f9ffe54f969f78f6ef1f655
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121276607"
---
# <a name="idebugprogram2candetach"></a>IDebugProgram2::CanDetach
Determina se un motore di debug (DE) può scollegarsi dal programma.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT CanDetach(
   void
);
```

```csharp
int CanDetach();
```

## <a name="return-value"></a>Valore restituito
 Se è possibile scollegare, restituisce `S_OK` ; in caso contrario, restituisce un codice di errore. Restituisce `S_FALSE` se de non è in grado di disconnettersi dal programma.

## <a name="see-also"></a>Vedi anche
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
