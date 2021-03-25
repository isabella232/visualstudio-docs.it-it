---
description: Restituisce i GUID per tutti i possibili motori di debug (DE) in grado di eseguire il debug del programma.
title: 'IDebugProgramEngines2:: EnumPossibleEngines | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2a49a0590a1ec2f0b0e7d2be59fe2161b438154a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084207"
---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
Restituisce i GUID per tutti i possibili motori di debug (DE) in grado di eseguire il debug del programma.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT EnumPossibleEngines( 
   DWORD  celtBuffer,
   GUID*  rgguidEngines,
   DWORD* pceltEngines
);
```

```csharp
int EnumPossibleEngines( 
   uint      celtBuffer,
   GUID[]    rgguidEngines,
   ref DWORD pceltEngines
);
```

## <a name="parameters"></a>Parametri
`celtBuffer`\
in Numero di GUID DE da restituire. Consente inoltre di specificare la dimensione massima della `rgguidEngines` matrice.

`rgguidEngines`\
[in, out] Matrice di GUID da compilare.

`pceltEngines`\
out Restituisce il numero effettivo di GUID che vengono restituiti.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. Restituisce [C++] `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` o [C#] 0x8007007a se il buffer non è sufficientemente grande.

## <a name="remarks"></a>Commenti
 Per determinare il numero di motori disponibili, chiamare questo metodo una volta con il `celtBuffer` parametro impostato su 0 e il `rgguidEngines` parametro impostato su un valore null. Viene restituito `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` (0x8007007a per C#) e il `pceltEngines` parametro restituisce la dimensione necessaria del buffer.

## <a name="see-also"></a>Vedi anche
- [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)
