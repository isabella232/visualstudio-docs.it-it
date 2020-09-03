---
title: 'IDebugProgramEngines2:: EnumPossibleEngines | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a417fd4f0d90ffebd291179dee28a0e81f92cce9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182181"
---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Restituisce i GUID per tutti i possibili motori di debug (DE) in grado di eseguire il debug del programma.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
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
  
#### <a name="parameters"></a>Parametri  
 `celtBuffer`  
 in Numero di GUID DE da restituire. Consente inoltre di specificare la dimensione massima della `rgguidEngines` matrice.  
  
 `rgguidEngines`  
 [in, out] Matrice di GUID da compilare.  
  
 `pceltEngines`  
 out Restituisce il numero effettivo di GUID che vengono restituiti.  
  
## <a name="return-value"></a>Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. Restituisce [C++] `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` o [C#] 0x8007007a se il buffer non è sufficientemente grande.  
  
## <a name="remarks"></a>Osservazioni  
 Per determinare il numero di motori disponibili, chiamare questo metodo una volta con il `celtBuffer` parametro impostato su 0 e il `rgguidEngines` parametro impostato su un valore null. Viene restituito `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` (0x8007007a per C#) e il `pceltEngines` parametro restituisce la dimensione necessaria del buffer.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)
