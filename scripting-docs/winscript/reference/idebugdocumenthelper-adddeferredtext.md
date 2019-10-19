---
title: 'IDebugDocumentHelper:: AddDeferredText | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 1aae73e44059b1f07fa4cb54f40cdcd12e564a8f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577045"
---
# <a name="idebugdocumenthelperadddeferredtext"></a>IDebugDocumentHelper::AddDeferredText
Notifica all'helper che il testo specificato è disponibile, ma non fornisce i caratteri.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT AddDeferredText(  
   ULONG  cChars,  
   DWORD  dwTextStartCookie  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `cChars`  
 in Numero di caratteri (Unicode) da aggiungere.  
  
 `dwTextStartCookie`  
 in Cookie definito dall'host che rappresenta la posizione iniziale del testo.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_FAIL`|Il metodo non è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo consente all'host di rinviare la fornitura dei caratteri da aggiungere fino a quando non sono necessari, consentendo allo stesso tempo all'helper di generare notifiche accurate e informazioni sulle dimensioni. Il parametro `dwTextStartCookie` è un cookie, definito dall'host, che rappresenta la posizione iniziale del testo. Le chiamate successive a `IDebugDocumentText::GetText` devono fornire questo cookie. Ad esempio, in un host che rappresenta il testo in DBCS, il cookie potrebbe essere un offset di byte.  
  
 Si presuppone che una singola chiamata a `IDebugDocumentText::GetText` possa ottenere caratteri da più chiamate a `AddDeferredText`. Le classi helper possono anche richiedere più volte lo stesso intervallo di caratteri posticipati.  
  
> [!NOTE]
> Le chiamate a `AddDeferredText` non devono essere combinate con chiamate a `AddUnicodeText` o `AddDBCSText`. In tal caso, viene restituito `E_FAIL`.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)    
 @No__t_1 [IDebugDocumentHelper:: AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)  
 @No__t_1 [IDebugDocumentHelper:: AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)  
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)