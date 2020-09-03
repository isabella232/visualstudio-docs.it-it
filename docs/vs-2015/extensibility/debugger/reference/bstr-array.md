---
title: BSTR_ARRAY | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BSTR_ARRAY
helpviewer_keywords:
- BSTR_ARRAY structure
ms.assetid: 48da37f7-a237-48a9-9ff9-389c1a00862c
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 912537eb632768b3bcb6543dab098126ce02424f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153190"
---
# <a name="bstr_array"></a>BSTR_ARRAY
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Struttura che descrive una matrice di stringhe.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
typedef struct tagBSTR_ARRAY {  
   DWORD dwCount;  
   BSTR* Members;  
} BSTR_ARRAY;  
```  
  
```csharp  
struct BSTR_ARRAY {  
   DWORD    dwCount;  
   string[] Members;  
}  
```  
  
## <a name="terms"></a>Termini  
 dwCount  
 Numero di stringhe nella `Members` matrice.  
  
 Membri  
 Matrice di stringhe.  
  
## <a name="remarks"></a>Osservazioni  
 Questa struttura viene restituita dal metodo [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) .  
  
 [Solo C++] Ogni singola stringa deve essere liberata usando `SysFreeString` e la `Members` matrice deve essere liberata con `CoTaskMemFree` .  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)
