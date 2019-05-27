---
title: IDebugProgramEngines2::EnumPossibleEngines | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d226650592881e9e7f87a5fbf5c700dfd7d817cb
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2019
ms.locfileid: "66211143"
---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
Restituisce il GUID per tutti i possibili motori di debug (DE) che è possono eseguire il debug di questo programma.

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
[in] Il numero di GUID DE da restituire. Specifica anche la dimensione massima del `rgguidEngines` matrice.

`rgguidEngines`\
[in, out] Una matrice di GUID DE da compilare.

`pceltEngines`\
[out] Restituisce il numero effettivo di GUID DE restituiti.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Restituisce [C++] `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` o [C#] 0x8007007A se il buffer non è sufficientemente grande.

## <a name="remarks"></a>Note
 Per determinare il numero di motori, chiamare questo metodo una volta con il `celtBuffer` parametro è impostato su 0 e il `rgguidEngines` parametro impostato su un valore null. Verranno restituite `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` (0x8007007A per c#) e il `pceltEngines` parametro restituisce la dimensione del buffer necessaria.

## <a name="see-also"></a>Vedere anche
- [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)