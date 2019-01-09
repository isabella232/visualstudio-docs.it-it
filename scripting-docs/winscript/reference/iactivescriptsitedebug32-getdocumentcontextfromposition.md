---
title: IActiveScriptSiteDebug32::GetDocumentContextFromPosition | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53348dff-35a6-4303-b263-90c10af06bf3
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 9a52abcfa4defb49526f944469c95a2247f5d85c
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094484"
---
# <a name="iactivescriptsitedebug32getdocumentcontextfromposition"></a>IActiveScriptSiteDebug32::GetDocumentContextFromPosition
Utilizzato dal motore del linguaggio per delegare `IDebugCodeContext::GetSourceContext`.  
  
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
 [in] Il contenuto di origine alla stregua `ParseScriptText` o `AddScriptlet`.  
  
 `uCharacterOffset`  
 [in] Offset rispetto all'inizio del blocco di script o scriptlet carattere.  
  
 `uNumChars`  
 [in] Numero di caratteri in questo contesto.  
  
 `ppsc`  
 [out] Il contesto del documento corrispondenti a questo intervallo di posizione del carattere.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Motori di linguaggio usano questo metodo per delegare `IDebugCodeContext::GetSourceContext`.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptSiteDebug32](../../winscript/reference/iactivescriptsitedebug32-interface.md)