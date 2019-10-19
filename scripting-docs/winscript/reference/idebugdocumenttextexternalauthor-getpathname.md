---
title: 'IDebugDocumentTextExternalAuthor:: GetPathName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextExternalAuthor.GetPathName
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentTextExternalAuthor::GetPathName
ms.assetid: 445152a1-9cf8-402e-93d6-3d4bf2b81d17
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e876b41ce1bde4defffd11267c6665f9d57da077
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575960"
---
# <a name="idebugdocumenttextexternalauthorgetpathname"></a>IDebugDocumentTextExternalAuthor::GetPathName
Restituisce il percorso completo e il nome file del documento.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetPathName(  
   BSTR*  pbstrLongName,  
   BOOL*  pfIsOriginalFile  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pbstrLongName`  
 out Stringa contenente il percorso completo e il nome file.  
  
 `pfIsOriginalFile`  
 out Valore booleano che indica se il percorso e il nome file fanno riferimento al documento originale.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_FAIL`|Impossibile creare o determinare il file di origine.|  
  
## <a name="remarks"></a>Note  
 Questo metodo restituisce il percorso completo e il nome file del documento.  
  
 Se `pfIsOriginalFile` è FALSE, il percorso e il nome del file in `pbstrLongName` fanno riferimento a un file temporaneo appena creato.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugDocumentTextExternalAuthor](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)