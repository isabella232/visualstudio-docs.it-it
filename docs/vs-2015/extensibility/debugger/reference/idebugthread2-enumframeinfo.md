---
title: IDebugThread2::EnumFrameInfo | Microsoft Docs
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
- IDebugThread2::EnumFrameInfo
helpviewer_keywords:
- IDebugThread2::EnumFrameInfo
ms.assetid: 17914a71-10ea-4b6f-8982-e364f87dca53
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 12b56f2ae1c6a284880cffc665f54750d5320dfa
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49247396"
---
# <a name="idebugthread2enumframeinfo"></a>IDebugThread2::EnumFrameInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Recupera un elenco degli stack frame per questo thread.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT EnumFrameInfo (   
   FRAMEINFO_FLAGS        dwFieldSpec,  
   UINT                   nRadix,  
   IEnumDebugFrameInfo2** ppEnum  
);  
```  
  
```csharp  
int EnumFrameInfo (   
   enum_FRAMEINFO_FLAGS     dwFieldSpec,  
   uint                     nRadix,  
   out IEnumDebugFrameInfo2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwFieldSpec`  
 [in] Una combinazione di flag dal [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) enumerazione che specifica quali campi della [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) strutture sono da compilare. Specificare il `FIF_FUNCNAME_FORMAT` flag per formattare il nome della funzione in un'unica stringa.  
  
 `nRadix`  
 [in] Radice usati nella formattazione di informazioni numeriche nell'enumeratore.  
  
 `ppEnum`  
 [out] Restituisce un [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) oggetto che contiene un elenco delle [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) strutture che descrivono lo stack frame.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Frame del thread vengono enumerati in ordine, con il fotogramma corrente enumerata prima e il meno recente enumerati ultima.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)

