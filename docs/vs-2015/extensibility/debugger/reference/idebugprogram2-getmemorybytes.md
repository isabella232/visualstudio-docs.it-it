---
title: 'IDebugProgram2:: GetMemoryBytes | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetMemoryBytes
helpviewer_keywords:
- IDebugProgram2::GetMemoryBytes
ms.assetid: 1cdedb47-caf8-468e-aaf4-163f16afb403
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6f4c160799a48e7c548425ed18809bbf9cb381ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148679"
---
# <a name="idebugprogram2getmemorybytes"></a>IDebugProgram2::GetMemoryBytes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Recupera i byte di memoria occupati dal programma.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetMemoryBytes(   
   IDebugMemoryBytes2** ppMemoryBytes  
);  
```  
  
```csharp  
int GetMemoryBytes(   
   out IDebugMemoryBytes2 ppMemoryBytes  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppMemoryBytes`  
 out Restituisce un oggetto [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) che rappresenta i byte di memoria del programma.  
  
## <a name="return-value"></a>Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.  
  
## <a name="remarks"></a>Osservazioni  
 I byte di memoria rappresentati dall'oggetto [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) sono per l'immagine del programma in memoria e non per la memoria allocata al momento dell'esecuzione del programma.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
