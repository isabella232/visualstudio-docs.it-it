---
title: IDebugReference2::GetReferenceInfo | Microsoft Docs
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
- IDebugReference2::GetReferenceInfo
helpviewer_keywords:
- IDebugReference2::GetReferenceInfo
ms.assetid: ae611714-f114-4cf2-b5bb-37461e6ff289
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 99e4870ae987a19bc1bd1140934873cce39c93dc
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49216827"
---
# <a name="idebugreference2getreferenceinfo"></a>IDebugReference2::GetReferenceInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ottiene il [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) struttura che descrive un riferimento. Riservato per utilizzi futuri.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetReferenceInfo (   
   DEBUGREF_INFO_FLAGS   dwFields,  
   DWORD                 nRadix,  
   DWORD                 dwTimeout,  
   IDebugReference2**    rgpArgs,  
   DWORD                 dwArgCount,  
   DEBUG_REFERENCE_INFO* pReferenceInfo  
);  
```  
  
```csharp  
int GetReferenceInfo (   
   enum_DEBUGREF_INFO_FLAGS  dwFields,  
   uint                      nRadix,  
   uint                      dwTimeout,  
   IDebugReference2[]        rgpArgs,  
   uint                      dwArgCount,  
   DEBUG_REFERENCE_INFO[]    pReferenceInfo  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwFields`  
 [in] Una combinazione di flag dal [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) enumerazione che determina i campi da compilare [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) struttura.  
  
 `nRadix`  
 [in] La radice da utilizzare nella formattazione qualsiasi informazioni numeriche.  
  
 `dwTimeout`  
 [in] Tempo massimo, espresso in millisecondi, di attesa prima della restituzione da questo metodo. Usare `INFINITE` per un'attesa indefinita.  
  
 `rgpArgs`  
 [in] Matrice di [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) oggetti. Riservato per utilizzi futuri; Impostare su un valore null.  
  
 `dwArgCount`  
 [in] Il numero di argomenti di riferimento nel `rgpArgs` matrice. Riservato per utilizzi futuri; Impostare su 0.  
  
 `pReferenceInfo`  
 [out] Oggetto [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) struttura compilata con una descrizione della proprietà.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce sempre `E_NOTIMPL`.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)

