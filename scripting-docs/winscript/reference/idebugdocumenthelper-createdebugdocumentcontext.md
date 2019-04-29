---
title: IDebugDocumentHelper::CreateDebugDocumentContext | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.CreateDebugDocumentContext
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::CreateDebugDocumentContext
ms.assetid: aa4ec691-9fb1-4da7-8085-b40d8a062467
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8b2dddfc76f2bbc3e629b2d48febb6b582a3a779
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62783171"
---
# <a name="idebugdocumenthelpercreatedebugdocumentcontext"></a>IDebugDocumentHelper::CreateDebugDocumentContext
Crea un nuovo contesto di documento di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT CreateDebugDocumentContext(  
   ULONG                    iCharPos,  
   ULONG                    cChars,  
   IDebugDocumentContext**  ppddc  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `iCharPos`  
 [in] Posizione di inizio del contenuto del documento di debug.  
  
 `cChars`  
 [in] Numero di caratteri nel contesto.  
  
 `ppddc`  
 [out] Il nuovo contesto di documento di debug.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo consente all'host creare un nuovo contesto di documento di debug.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)