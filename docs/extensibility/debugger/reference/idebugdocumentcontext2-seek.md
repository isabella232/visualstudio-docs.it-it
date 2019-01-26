---
title: IDebugDocumentContext2::Seek | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDocumentContext2::Seek
helpviewer_keywords:
- IDebugDocumentContext2::Seek
ms.assetid: 71501356-8a82-4d36-b354-6625bdd2baa0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 85ab2a7d81fb2c4b0d9963c57d7c85bdb9d5515c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54974919"
---
# <a name="idebugdocumentcontext2seek"></a>IDebugDocumentContext2::Seek
Sposta il contesto del documento da un determinato numero di istruzioni o le righe.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Seek(   
   int                      nCount,  
   IDebugDocumentContext2** ppDocContext  
);  
```  
  
```cpp  
int Seek(   
   int                        nCount,  
   out IDebugDocumentContext2 ppDocContext  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `nCount`  
 [in] Il numero di istruzioni o le righe da spostare in avanti, a seconda del contesto di documento.  
  
 `ppDocContext`  
 [out] Restituisce un nuovo [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) oggetto con la nuova posizione.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)