---
title: 'IActiveScriptAuthor:: GetChars | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetChars
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetChars
ms.assetid: a73ba263-12f7-4d5f-b4c8-9ad7e2d5d3cb
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ce2b46d65c2ce92111bc4b6f44f66ce9dc4ce5f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576248"
---
# <a name="iactivescriptauthorgetchars"></a>IActiveScriptAuthor::GetChars
Restituisce il set di caratteri di completamento per un contesto di completamento richiesto.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetChars(  
   DWORD            fRequestedList,  
   BSTR             *pbstrChars  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `fRequestedList`  
 in Contesto di completamento richiesto.  
  
|Costante|Value|Descrizione|  
|--------------|-----------|-----------------|  
|SCRIPT_CMPL_ENUM_TRIGGER|0x0001|Richiede l'enumerazione del lato sinistro.|  
|SCRIPT_CMPL_MEMBER_TRIGGER|0x0002|Richiede il contesto di completamento del membro.|  
|SCRIPT_CMPL_PARAM_TRIGGER|0x0003|Richiede l'elenco di parametri.|  
|SCRIPT_CMPL_COMMIT|0x0004|Richiede il completamento dell'elenco dei parametri.|  
  
 `pbstrChars`  
 out Caratteri che corrispondono al contesto di completamento richiesto.  
  
|parametro `fRequestedList`|Caratteri restituiti|  
|--------------------------------|-------------------------|  
|SCRIPT_CMPL_ENUM_TRIGGER|"."|  
|SCRIPT_CMPL_MEMBER_TRIGGER|"="|  
|SCRIPT_CMPL_PARAM_TRIGGER|"(,"|  
|SCRIPT_CMPL_COMMIT|"()"|  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)