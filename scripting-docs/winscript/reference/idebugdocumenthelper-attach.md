---
title: 'Idebugdocumenthelper:: Attach | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.Attach
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::Attach
ms.assetid: 834f23a9-716d-44df-b23c-d1bf6da60e79
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8f4fbd1686d27e594b748ca97c82c645de1b93de
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58151206"
---
# <a name="idebugdocumenthelperattach"></a>IDebugDocumentHelper::Attach
Questo documento aggiunto all'albero del documento.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT Attach(  
   IDebugDocumentHelper*  pddhParent  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pddhParent`  
 [in] L'albero del documento in cui verrà aggiunti in questo documento. Può essere NULL.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo aggiunge il documento al documento ad albero, usando `pddhParent` come elemento padre. Se il `pddhParent` è `NULL`, questo documento verrà il documento di primo livello.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugDocumentHelper::Detach](../../winscript/reference/idebugdocumenthelper-detach.md)   
 [Interfaccia IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)