---
title: 'Idebugdocumenthelper:: Init | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: d4bcb64b7bbb1c61e7f031d872f7d1440fd17833
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086632"
---
# <a name="idebugdocumenthelperinit"></a>IDebugDocumentHelper::Init
Il `Init` metodo inizializza un helper di documenti di debug con un nome e gli attributi iniziali.  
  
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
 [in] Il debug dell'applicazione associato al documento.  
  
 `pszShortName`  
 [in] Stringa con terminazione null contenente il nome breve del documento.  
  
 `pszLongName`  
 [in] Stringa con terminazione null contenente il nome lungo del documento.  
  
 `docAttr`  
 [in] Specifica gli attributi di documento di testo.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo inizializza un helper di documenti di debug con un nome e gli attributi iniziali.  
  
 Questo documento non viene visualizzata nell'albero fino alla `IDebugDocumentHelper::Attach` viene chiamato.  
  
## <a name="see-also"></a>Vedere anche  
 [Idebugdocumenthelper:: Attach](../../winscript/reference/idebugdocumenthelper-attach.md)   
 [Interfaccia IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [Costanti TEXT_DOC_ATTR](../../winscript/reference/text-doc-attr-constants.md)