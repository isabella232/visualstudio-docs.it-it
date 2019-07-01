---
title: IDebugField::GetExtendedInfo | Microsoft Docs
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
ms.sourcegitcommit: 0cd282a7584b9bfd4df7882f8fdf3ad8a270e219
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2019
ms.locfileid: "62547559"
---
# <a name="idebugfieldgetextendedinfo"></a>IDebugField::GetExtendedInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questo metodo ottiene estesi informazioni su un campo.  
  
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
 [in] Consente di selezionare le informazioni da restituire. I valori validi sono:  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`guidConstantValue`|Il valore come una sequenza di byte.|  
|`guidConstantType`|Il tipo come una firma di tipo.|  
  
 `prgBuffer`  
 [out] Restituisce le informazioni estese.  
  
 `pdwLen`  
 [in, out] Restituisce le dimensioni delle informazioni estese, in byte.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Attualmente, questo metodo restituisce solo il tipo o il valore di una costante. Il chiamante deve liberare il buffer restituito `prgBuffer` chiamando il metodo COM `CoTaskMemFree` funzione (C++) o <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> (c#).  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
