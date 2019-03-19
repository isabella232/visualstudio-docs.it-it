---
title: IDebugDocumentHelper::AddDBCSText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.AddDBCSText
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::AddDBCSText
ms.assetid: 5e5011b2-bbb4-491b-9a11-eb2846be44aa
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1d5de41ff83f3ffd5b208445830862138511ba2b
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58154793"
---
# <a name="idebugdocumenthelperadddbcstext"></a>IDebugDocumentHelper::AddDBCSText
Aggiunge una stringa DBCS alla fine di questo documento.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT AddDBCSText(  
   LPCSTR  pszText  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pszText`  
 [in] Puntatore a una stringa con terminazione null che contiene il testo.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_FAIL`|Il metodo è riuscito ad aggiungere i caratteri.|  
  
## <a name="remarks"></a>Note  
 Questo metodo genera `IDebugDocumentTextEvents` notifiche.  
  
> [!NOTE]
>  Se questo metodo viene chiamato dopo `IDebugDocumentHelper::AddDeferredText` è stato chiamato, `E_FAIL` viene restituito.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [Interfaccia IDebugDocumentTextEvents](../../winscript/reference/idebugdocumenttextevents-interface.md)