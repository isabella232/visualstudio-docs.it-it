---
title: 'IDebugDocumentHelper:: init | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.Init
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::Init
ms.assetid: 1dd5a01f-0779-4109-8c6c-f16f5a3835bf
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 13e6379052707aa44c0fa52f4cb30db2c4c4fa99
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576858"
---
# <a name="idebugdocumenthelperinit"></a>IDebugDocumentHelper::Init
Il metodo `Init` Inizializza un helper del documento di debug con un nome e gli attributi iniziali.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT Init(  
   IDebugApplication*  pda,  
   LPCOLESTR           pszShortName,  
   LPCOLESTR           pszLongName,  
   TEXT_DOC_ATTR       docAttr  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pda`  
 in Applicazione di debug associata al documento.  
  
 `pszShortName`  
 in Stringa con terminazione null che contiene il nome breve del documento.  
  
 `pszLongName`  
 in Stringa con terminazione null che contiene il nome lungo del documento.  
  
 `docAttr`  
 in Specifica gli attributi del documento di testo.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo inizializza un helper del documento di debug con un nome e gli attributi iniziali.  
  
 Questo documento non viene visualizzato nell'albero fino a quando non viene chiamato `IDebugDocumentHelper::Attach`.  
  
## <a name="see-also"></a>Vedere anche  
   [IDebugDocumentHelper:: Connetti](../../winscript/reference/idebugdocumenthelper-attach.md)  
 [Interfaccia IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [Costanti TEXT_DOC_ATTR](../../winscript/reference/text-doc-attr-constants.md)