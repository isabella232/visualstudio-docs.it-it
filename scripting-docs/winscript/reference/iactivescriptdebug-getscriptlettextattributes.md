---
title: IActiveScriptDebug::GetScriptletTextAttributes | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptDebug.GetScriptletTextAttributes
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptDebug::GetScriptletTextAttributes
ms.assetid: b3990d86-5fdf-4c9f-9678-3f4b808c7ca8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 781282b5c825954ada4fbb35daa2a97b379c3f13
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157594"
---
# <a name="iactivescriptdebuggetscriptlettextattributes"></a>IActiveScriptDebug::GetScriptletTextAttributes
Restituisce gli attributi di testo per un scriptlet arbitrario.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetScriptletTextAttributes(  
   LPCOLESTR          pstrCode,  
   ULONG              uNumCodeChars,  
   LPCOLESTR          pstrDelimiter,  
   DWORD              dwFlags,  
   SOURCE_TEXT_ATTR*  pattr  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pstrCode`  
 [in] Il testo dello scriptlet. Questa stringa non deve essere con terminata null.  
  
 `uNumCodeChars`  
 [in] Il numero di caratteri nel testo dello scriptlet.  
  
 `pstrDelimiter`  
 [in] Indirizzo del delimitatore end-of-scriptlet. Quando si `pstrCode` viene analizzata da un flusso di testo, l'host utilizza un delimitatore, in genere, ad esempio due virgolette ("), per rilevare la fine dello scriptlet. Questo parametro specifica il delimitatore utilizzato dall'host, consentendo il motore di scripting fornire alcuni condizionale pre-elaborazioni primitive (ad esempio, sostituire una virgoletta singola ['] con due virgolette singole per l'utilizzo come un delimitatore). Esattamente come (e se) viene utilizzato il motore scripting queste informazioni dipendono dal motore di script. Impostare questo parametro su NULL se l'host non utilizzava un delimitatore per contrassegnare la fine dello scriptlet.  
  
 `dwFlags`  
 [in] Flag associati allo scriptlet. Può essere una combinazione dei valori seguenti:  
  
|Costante|Value|Descrizione|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|Indica che gli identificatori e operatori punto devono essere identificati con i flag SOURCETEXT_ATTR_IDENTIFIER e SOURCETEXT_ATTR_MEMBERLOOKUP, rispettivamente.|  
|GETATTRFLAG_THIS|0x0100|Indica che l'identificatore per l'oggetto corrente deve essere identificato con il flag SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0x8000|Indica che deve essere identificato testo della stringa di contenuto e il commento con il flag SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [in, out] Buffer che deve contenere gli attributi restituiti.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Uno smart host che implementa `IDebugDocumentText` interfaccia è possibile usare questo metodo per delegare le chiamate al `IDebugDocumentText::GetText` (metodo).  
  
 Questa chiamata viene fornita perché gli scriptlet tendono a essere le espressioni e possono avere una sintassi diversa rispetto a un blocco di script. Se hanno la stessa sintassi, l'implementazione di questo metodo sarà identico all'implementazione del `GetScriptTextAttributes` (metodo).  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptDebug](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IActiveScriptDebug::GetScriptTextAttributes](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)   
 [Interfaccia IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)   
 [Enumerazione SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)