---
title: IDebugDocumentTextEvents::onReplaceText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextEvents.onReplaceText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentTextEvents::onReplaceText
ms.assetid: 3cb053c4-1f7f-4aed-aee6-f8a9e9e69d29
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b65496f3bf64dfaf1a4fc1f1180dd6715277cd59
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946700"
---
# <a name="idebugdocumenttexteventsonreplacetext"></a>IDebugDocumentTextEvents::onReplaceText
Indica che il testo è stato sostituito.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT onReplaceText(  
   ULONG  cCharacterPosition,  
   ULONG  cNumToReplace  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `cCharacterPosition`  
 [in] Posizione del carattere del primo carattere è stato sostituito.  
  
 `cNumToReplace`  
 [in] Il numero di caratteri sostituiti.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo indica che il testo è stato sostituito.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugDocumentTextEvents](../../winscript/reference/idebugdocumenttextevents-interface.md)