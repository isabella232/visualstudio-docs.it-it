---
title: 'IDebugDocumentHost:: GetScriptTextAttributes | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.GetScriptTextAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::GetScriptTextAttributes
ms.assetid: fe459d0d-937f-4176-be81-99d5cca121a1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3b18f4f49fa157b78e4f1fd6c7766e929890a6c6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72569208"
---
# <a name="idebugdocumenthostgetscripttextattributes"></a>IDebugDocumentHost::GetScriptTextAttributes
Restituisce gli attributi di testo per un blocco di testo del documento.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetScriptTextAttributes(  
   LPCOLESTR          pstrCode,  
   ULONG              uNumCodeChars,  
   LPCOLESTR          pstrDelimiter,  
   DWORD              dwFlags,  
   SOURCE_TEXT_ATTR*  pattr  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pstrCode`  
 in Testo del blocco di script. Questa stringa non deve essere terminata con null.  
  
 `uNumCodeChars`  
 in Numero di caratteri nel testo del blocco di script.  
  
 `pstrDelimiter`  
 in Indirizzo del delimitatore di blocco di fine dello script. Quando `pstrCode` viene analizzato da un flusso di testo, l'host usa in genere un delimitatore, ad esempio due virgolette singole (''), per rilevare la fine del blocco di script. Questo parametro specifica il delimitatore utilizzato dall'host, consentendo al motore di scripting di fornire una pre-elaborazione condizionale (ad esempio, sostituendo una virgoletta singola ['] con due virgolette singole da utilizzare come delimitatore). Il modo in cui (e se) il motore di scripting utilizza queste informazioni dipende dal motore di scripting. Impostare questo parametro su NULL se l'host non ha usato un delimitatore per contrassegnare la fine del blocco di script.  
  
 `dwFlags`  
 in Flag associati al blocco di script. Può essere una combinazione di questi valori:  
  
|Costante|Value|Descrizione|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|Indica che gli identificatori e gli operatori punto devono essere identificati rispettivamente con i flag SOURCETEXT_ATTR_IDENTIFIER e SOURCETEXT_ATTR_MEMBERLOOKUP.|  
|GETATTRFLAG_THIS|0x0100|Indica che l'identificatore per l'oggetto corrente deve essere identificato con il flag SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0x8000|Indica che il contenuto della stringa e il testo del commento devono essere identificati con il flag SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [in, out] Buffer contenente gli attributi restituiti.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_NOTIMPL`|L'host utilizza solo attributi predefiniti.|  
  
## <a name="remarks"></a>Note  
 Questo metodo restituisce gli attributi di testo per un blocco arbitrario di testo del documento. È accettabile che gli host restituiscano `E_NOTIMPL`, nel qual caso vengono usati gli attributi predefiniti.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugDocumentHost](../../winscript/reference/idebugdocumenthost-interface.md)    
 [Enumerazione SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)