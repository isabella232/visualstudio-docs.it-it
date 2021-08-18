---
description: Restituisce i GUID per tutti i possibili motori di debug che possono eseguire il debug di questo programma.
title: IDebugProgramEngines2::EnumPossibleEngines | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3bbcd034c2d0a9cd6314281a6bdd47e24983b5e5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122132613"
---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
Restituisce i GUID per tutti i possibili motori di debug che possono eseguire il debug di questo programma.

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
[in] Numero di GUID DE da restituire. Specifica anche le dimensioni massime della `rgguidEngines` matrice.

`rgguidEngines`\
[in, out] Matrice di GUID DE da riempire.

`pceltEngines`\
[out] Restituisce il numero effettivo di GUID DE restituiti.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. Restituisce [C++] `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` o [C#] 0x8007007A se le dimensioni del buffer non sono sufficienti.

## <a name="remarks"></a>Commenti
 Per determinare il numero di motori disponibili, chiamare questo metodo una volta con il parametro impostato su 0 e il parametro `celtBuffer` impostato su un valore `rgguidEngines` Null. Restituisce `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` (0x8007007A per C#) e il `pceltEngines` parametro restituisce le dimensioni necessarie del buffer.

## <a name="see-also"></a>Vedi anche
- [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)
