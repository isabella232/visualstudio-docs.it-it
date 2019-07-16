---
title: IDebugDocumentContext2::Compare | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::Compare
helpviewer_keywords:
- IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7f09684c5e9587c6e3bb631674e009d0b36f4fc5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68189408"
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Confronta questo contesto di documento in una matrice specificata di contesti di documento.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
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
