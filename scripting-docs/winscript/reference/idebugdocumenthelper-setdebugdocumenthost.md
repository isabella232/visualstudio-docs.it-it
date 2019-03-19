---
title: 'Idebugdocumenthelper:: Setdebugdocumenthost | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.SetDebugDocumentHost
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::SetDebugDocumentHost
ms.assetid: b26a03c3-8a3f-47b0-b916-4c65d5500f10
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 47c003657518edae0e8ffed13ffef9f6f072d296
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58148034"
---
# <a name="idebugdocumenthelpersetdebugdocumenthost"></a>IDebugDocumentHelper::SetDebugDocumentHost
Imposta il `IDebugDocumentHost` per questo documento.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT SetDebugDocumentHost(  
   IDebugDocumentHost*  pddh  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pddh`  
 [in] L'host di documenti di debug.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Il `IDebugDocumentHost` interfaccia viene utilizzata per la colorazione della sintassi smart host, il recupero posticipato testo e la restituzione di oggetti di controllo per appena creata contesti del documento.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [Interfaccia IDebugDocumentHost](../../winscript/reference/idebugdocumenthost-interface.md)