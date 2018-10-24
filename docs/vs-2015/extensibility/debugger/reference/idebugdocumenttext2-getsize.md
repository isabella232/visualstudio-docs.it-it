---
title: IDebugDocumentText2::GetSize | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugDocumentText2::GetSize
helpviewer_keywords:
- IDebugDocumentText2::GetSize
ms.assetid: bf515a8f-dcee-4004-8f81-543d547ceaae
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 570ec02c2e4df7d2af9b175e6fa1c41dcd82ac8e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49906364"
---
# <a name="idebugdocumenttext2getsize"></a>IDebugDocumentText2::GetSize
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Recupera la dimensione del testo nella posizione specificata nel documento.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
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
  
 [Solo in c#] Specificare entrambi i parametri.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)

