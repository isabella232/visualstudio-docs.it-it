---
title: IDebugDocumentContext::GetDocument | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentContext.GetDocument
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentContext::GetDocument
ms.assetid: 32db2fea-4938-4644-b39a-8fae05960d1d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9bfcc5b3e2d2e197619f9bc4ec19b55c9eaf1d2a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62974436"
---
# <a name="idebugdocumentcontextgetdocument"></a>IDebugDocumentContext::GetDocument
Restituisce il documento che contiene questo contesto.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetDocument(  
   IDebugDocument**  ppsd  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppsd`  
 [out] Il documento che contiene questo contesto.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Il `GetDocument` metodo restituisce il documento che contiene questo contesto.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugDocumentContext](../../winscript/reference/idebugdocumentcontext-interface.md)