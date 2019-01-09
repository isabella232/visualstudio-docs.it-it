---
title: 'Idebugdocumenthelper:: Adddeferredtext | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.AddDeferredText
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::AddDeferredText
ms.assetid: 9463cfb0-76cc-45ee-b32c-f37dce2b2e0e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba6f945e6c7fa4df83a5e301d73b3fc0bb9da92b
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096083"
---
# <a name="idebugdocumenthelperadddeferredtext"></a>IDebugDocumentHelper::AddDeferredText
Notifica dell'helper che il testo specificato è disponibile, ma non fornisce i caratteri.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT AddDeferredText(  
   ULONG  cChars,  
   DWORD  dwTextStartCookie  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `cChars`  
 [in] Numero di caratteri (Unicode) da aggiungere.  
  
 `dwTextStartCookie`  
 [in] Cookie definito dall'host che rappresenta la posizione iniziale del testo.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_FAIL`|Il metodo non è riuscita.|  
  
## <a name="remarks"></a>Note  
 Questo metodo consente all'host di rinvio che fornisce i caratteri da aggiungere fino a quando non sono necessarie, consentendo l'helper generare notifiche accurate e informazioni sulle dimensioni. Il `dwTextStartCookie` parametro è un cookie, definito dall'host, che rappresenta la posizione iniziale del testo. Le chiamate successive a `IDebugDocumentText::GetText` necessario fornire questo cookie. Ad esempio, in un host che rappresenta il testo in caratteri DBCS, il cookie potrebbe essere un offset di byte.  
  
 Si presuppone che una singola chiamata a `IDebugDocumentText::GetText` può ottenere i caratteri da più chiamate a `AddDeferredText`. Classi helper inoltre possono chiedere più volte lo stesso intervallo di caratteri posticipate.  
  
> [!NOTE]
>  Le chiamate a `AddDeferredText` non devono essere combinati con chiamate a `AddUnicodeText` o `AddDBCSText`. In questo caso, `E_FAIL` viene restituito.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [Idebugdocumenthelper:: Addunicodetext](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)   
 [Idebugdocumenthelper:: Adddbcstext](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)