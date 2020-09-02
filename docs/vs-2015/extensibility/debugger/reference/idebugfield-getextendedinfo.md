---
title: 'IDebugField:: GetExtendedInfo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugField::GetExtendedInfo
helpviewer_keywords:
- IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3de21bc984a36db87f8ce1567f4ff7d97212c40e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547559"
---
# <a name="idebugfieldgetextendedinfo"></a>IDebugField::GetExtendedInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questo metodo ottiene le informazioni estese su un campo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetExtendedInfo(   
   REFGUID guidExtendedInfo,  
   BYTE**  prgBuffer,  
   DWORD*  pdwLen  
);  
```  
  
```csharp  
int GetExtendedInfo(  
   ref Guid guidExtendedInfo,   
   IntPtr[] prgBuffer,   
   ref uint pdwLen  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `guidExtendedInfo`  
 in Seleziona le informazioni da restituire. I valori validi sono:  
  
|valore|Descrizione|  
|-----------|-----------------|  
|`guidConstantValue`|Valore come sequenza di byte.|  
|`guidConstantType`|Tipo come firma del tipo.|  
  
 `prgBuffer`  
 out Restituisce le informazioni estese.  
  
 `pdwLen`  
 [in, out] Restituisce la dimensione, in byte, delle informazioni estese.  
  
## <a name="return-value"></a>Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.  
  
## <a name="remarks"></a>Osservazioni  
 Attualmente, questo metodo restituisce solo il tipo o il valore di una costante. Il chiamante deve liberare il buffer restituito in chiamando la `prgBuffer` funzione com `CoTaskMemFree` (C++) o <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> (C#).  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
