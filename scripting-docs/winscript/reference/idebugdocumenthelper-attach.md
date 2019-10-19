---
title: 'IDebugDocumentHelper:: alleghi | Microsoft Docs'
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
ms.openlocfilehash: 3400a5bf6cd3e4a9726fdf4b2f20bbf43b9fc989
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577026"
---
# <a name="idebugdocumenthelperattach"></a>IDebugDocumentHelper::Attach
Aggiunge questo documento all'albero del documento.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT Attach(  
   IDebugDocumentHelper*  pddhParent  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pddhParent`  
 in Albero del documento in cui verrà aggiunto questo documento. Può essere NULL.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo aggiunge questo documento all'albero del documento, usando `pddhParent` come padre. Se la `pddhParent` è `NULL`, questo documento sarà il documento di primo livello.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugDocumentHelper::D etach](../../winscript/reference/idebugdocumenthelper-detach.md)    
 [Interfaccia IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)