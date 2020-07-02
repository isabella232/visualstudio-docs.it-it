---
title: 'IActiveScriptSiteDebug32:: GetDocumentContextFromPosition | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 53348dff-35a6-4303-b263-90c10af06bf3
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: b43b16f46cc62b6c70460d79c194b5e0d2cfede0
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835277"
---
# <a name="iactivescriptsitedebug32getdocumentcontextfromposition"></a>IActiveScriptSiteDebug32::GetDocumentContextFromPosition
Utilizzato dal motore di linguaggio per delegare `IDebugCodeContext::GetSourceContext` .  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetDocumentContextFromPosition(  
   DWORD_PTR                dwSourceContext,  
   ULONG                    uCharacterOffset,  
   ULONG                    uNumChars,  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwSourceContext`  
 in Contenuto di origine fornito a `ParseScriptText` o `AddScriptlet` .  
  
 `uCharacterOffset`  
 in Offset carattere relativo all'inizio del blocco di script o di scriptlet.  
  
 `uNumChars`  
 in Numero di caratteri in questo contesto.  
  
 `ppsc`  
 out Contesto del documento corrispondente a questo intervallo di posizioni dei caratteri.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Osservazioni  
 I motori di linguaggio utilizzano questo metodo per delegare `IDebugCodeContext::GetSourceContext` .  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptSiteDebug32](../../winscript/reference/iactivescriptsitedebug32-interface.md)