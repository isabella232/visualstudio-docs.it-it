---
title: IDebugDocumentText2::GetSize | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDocumentText2::GetSize
helpviewer_keywords:
- IDebugDocumentText2::GetSize
ms.assetid: bf515a8f-dcee-4004-8f81-543d547ceaae
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b22ed5f7f99e8a0e7a5f3a2d55b98de7dcd781bc
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54932987"
---
# <a name="idebugdocumenttext2getsize"></a>IDebugDocumentText2::GetSize
Recupera la dimensione del testo nella posizione specificata nel documento.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetSize(   
   ULONG* pcNumLines,  
   ULONG* pcNumChars  
);  
```  
  
```csharp  
int GetSize(   
   ref uint pcNumLines,  
   ref uint pcNumChars  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pcNumLines`  
 [out] Restituisce il numero di righe di testo.  
  
 `pcNumChars`  
 [out] Restituisce il numero di caratteri del testo.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 [Solo C++] Se non si desidera un valore specifico, passare un valore NULL per il parametro.  
  
 [C# solo] Specificare entrambi i parametri.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)