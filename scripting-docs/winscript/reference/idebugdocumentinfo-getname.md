---
title: IDebugDocumentInfo::GetName | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentInfo.GetName
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentInfo::GetName
ms.assetid: c25d73da-99b6-4c9f-82af-182b4853f81c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9975563c27b986190fbd2731c3f36b1e32719c0b
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58160326"
---
# <a name="idebugdocumentinfogetname"></a>IDebugDocumentInfo::GetName
Restituisce il nome del documento specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetName(  
   DOCUMENTNAMETYPE  dnt,  
   BSTR*             pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dnt`  
 [in] Tipo del nome del documento da restituire.  
  
 `pbstrName`  
 [out] Stringa contenente il nome.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_FAIL`|Il nome del documento specificato non è noto.|  
  
## <a name="remarks"></a>Note  
 Questo metodo restituisce il nome del documento specificato.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugDocumentInfo](../../winscript/reference/idebugdocumentinfo-interface.md)   
 [Enumerazione DOCUMENTNAMETYPE](../../winscript/reference/documentnametype-enumeration.md)