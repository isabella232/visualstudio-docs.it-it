---
title: IDebugDocumentContext2::Compare | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocumentContext2::Compare
helpviewer_keywords:
- IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: af349d8568d50e2059ab33ad54b14f499c7b6afd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49913462"
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
Confronta questo contesto di documento in una matrice specificata di contesti di documento.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Compare(   
   DOCCONTEXT_COMPARE       compare,  
   IDebugDocumentContext2** rgpDocContextSet,  
   DWORD                    dwDocContextSetLen,  
   DWORD*                   pdwDocContext  
);  
```  
  
```csharp  
int Compare(   
   enum_ DOCCONTEXT_COMPARE compare,  
   IDebugDocumentContext2[] rgpDocContextSet,  
   uint                     dwDocContextSetLen,  
   out uint                 pdwDocContext  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `compare`  
 [in] Un valore compreso il [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) enumerazione che specifica il tipo di confronto.  
  
 `rgpDocContextSet`  
 [in] Matrice di [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) gli oggetti che rappresentano i contesti di documento cui è confrontati.  
  
 `dwDocContextSetLen`  
 [in] La lunghezza della matrice di contesti di documento da confrontare.  
  
 `pdwDocContext`  
 [out] Restituisce l'indice nel `rgpDocContextSet` matrice del contesto del documento prima che soddisfa il confronto.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce `S_OK` se è stata trovata una corrispondenza. Restituisce `S_FALSE` se è stata trovata alcuna corrispondenza. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) oggetti che vengono passati nella matrice devono essere implementati dallo stesso motore di debug che implementa il `IDebugDocumentContext2` oggetto chiamato; in caso contrario, il confronto non è valido.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)