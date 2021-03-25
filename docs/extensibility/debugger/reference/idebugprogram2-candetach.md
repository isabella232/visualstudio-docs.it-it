---
description: Determina se un motore di debug (DE) può scollegarsi dal programma.
title: 'IDebugProgram2:: CanDetach | Microsoft Docs'
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
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9e751429fe26060a515f94aa3d402954ff598d39
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076173"
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
 Se è possibile scollegare, restituisce `S_OK` ; in caso contrario, restituisce un codice di errore. Restituisce `S_FALSE` se non è possibile scollegare dal programma.

## <a name="see-also"></a>Vedi anche
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
