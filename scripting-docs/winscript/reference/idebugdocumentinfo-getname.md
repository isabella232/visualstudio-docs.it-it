---
title: IDebugDocumentInfo::GetName | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: f3ecde4fbde1a265596a01d7f0f953763363e797
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097695"
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
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_FAIL`|Il nome del documento specificato non è noto.|  
  
## <a name="remarks"></a>Note  
 Questo metodo restituisce il nome del documento specificato.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugDocumentInfo](../../winscript/reference/idebugdocumentinfo-interface.md)   
 [Enumerazione DOCUMENTNAMETYPE](../../winscript/reference/documentnametype-enumeration.md)