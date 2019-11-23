---
title: 'IActiveScriptDebug:: GetScriptTextAttributes | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptDebug.GetScriptTextAttributes
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptDebug::GetScriptTextAttributes
ms.assetid: 2e8bda34-db0c-4b2e-a17f-82c4e0dbbc8c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 57bd466965f6431a1418df1aa56cf6a7bbbc78cc
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576926"
---
# <a name="iactivescriptdebuggetscripttextattributes"></a>IActiveScriptDebug::GetScriptTextAttributes
Restituisce gli attributi di testo per un blocco arbitrario di testo di script.  
  
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
 in Testo del blocco di script. Questa stringa non deve essere con terminazione null.  
  
 `uNumCodeChars`  
 in Numero di caratteri nel testo del blocco di script.  
  
 `pstrDelimiter`  
 in Indirizzo del delimitatore di blocco di fine dello script. Quando `pstrCode` viene analizzato da un flusso di testo, l'host usa in genere un delimitatore, ad esempio due virgolette singole (''), per rilevare la fine del blocco di script. Questo parametro specifica il delimitatore utilizzato dall'host, consentendo al motore di scripting di fornire una pre-elaborazione condizionale (ad esempio, sostituendo una virgoletta singola ['] con due virgolette singole da utilizzare come delimitatore). Il modo in cui (e se) il motore di scripting utilizza queste informazioni dipende dal motore di scripting. Impostare questo parametro su NULL se l'host non ha usato un delimitatore per contrassegnare la fine del blocco di script.  
  
 `dwFlags`  
 in Flag associati al blocco di script. Può essere una combinazione di questi valori:  
  
|Costante|Valore|Descrizione|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|Indica che gli identificatori e gli operatori punto devono essere identificati rispettivamente con i flag SOURCETEXT_ATTR_IDENTIFIER e SOURCETEXT_ATTR_MEMBERLOOKUP.|  
|GETATTRFLAG_THIS|0x0100|Indica che l'identificatore per l'oggetto corrente deve essere identificato con il flag di SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0x8000|Indica che il contenuto della stringa e il testo del commento devono essere identificati con il flag di SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [in, out] Buffer contenente gli attributi restituiti.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Uno smart host che implementa `IDebugDocumentText` interfaccia può utilizzare questo metodo per delegare le chiamate al metodo `IDebugDocumentText::GetText`.  
  
 Questo metodo per i blocchi di script; il metodo `GetScriptletTextAttributes` è per gli scriptlet.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptDebug](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IActiveScriptDebug::GetScriptletTextAttributes](../../winscript/reference/iactivescriptdebug-getscriptlettextattributes.md)   
 [Interfaccia IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)   
 [Enumerazione SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)