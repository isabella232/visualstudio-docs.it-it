---
title: IDebugDocumentContext::EnumCodeContexts | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentContext.EnumCodeContexts
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentContext::EnumCodeContexts
ms.assetid: fb0aa64e-c458-4ef1-bcd8-5cebdc972549
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ecf8b7d1ea292d0e1464825314cc92e1e903db3e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62974423"
---
# <a name="idebugdocumentcontextenumcodecontexts"></a>IDebugDocumentContext::EnumCodeContexts
Enumera i contesti di codice associati a questo contesto di documento.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT EnumCodeContexts(  
   IEnumDebugCodeContexts**  ppescc  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppescc`  
 [out] I contesti di codice associati a questo contesto di documento.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Un documento è in genere associato al contesto di un solo codice, a meno che il documento è un file di inclusione o di un modello.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugDocumentContext](../../winscript/reference/idebugdocumentcontext-interface.md)