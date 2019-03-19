---
title: IDebugDocumentTextExternalAuthor::GetFileName | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextExternalAuthor.GetFileName
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentTextExternalAuthor::GetFileName
ms.assetid: 87acdce6-acb2-4936-80dd-d624bb7dbd42
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: edb988751b8a0c0e6450e1fa216a474df2e8c59d
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58158711"
---
# <a name="idebugdocumenttextexternalauthorgetfilename"></a>IDebugDocumentTextExternalAuthor::GetFileName
Restituisce il nome del documento senza informazioni sul percorso.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetFileName(  
   BSTR*  pbstrShortName  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pbstrShortName`  
 [out] Stringa contenente il nome breve del documento.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo restituisce il nome del documento senza informazioni sul percorso. Il nome breve viene in genere utilizzato nelle finestre di dialogo.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugDocumentTextExternalAuthor](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)