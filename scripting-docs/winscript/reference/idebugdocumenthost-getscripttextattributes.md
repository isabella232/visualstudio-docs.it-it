---
title: 'Idebugdocumenthost:: Getscripttextattributes | Microsoft Docs'
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
ms.openlocfilehash: 6a5e56468e51f6d90e37e90c885b6b9df48d5f6e
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58158997"
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
 [in] Il testo di blocco di script. Questa stringa non dovrà essere con terminazione null.  
  
 `uNumCodeChars`  
 [in] Il numero di caratteri del testo di blocco di script.  
  
 `pstrDelimiter`  
 [in] Indirizzo del delimitatore end-di--blocco di script. Quando si `pstrCode` viene analizzata da un flusso di testo, l'host utilizza un delimitatore, in genere, ad esempio due virgolette ("), per rilevare la fine del blocco di script. Questo parametro specifica il delimitatore utilizzato dall'host, consentendo il motore di scripting fornire alcuni condizionale pre-elaborazioni primitive (ad esempio, sostituire una virgoletta singola ['] con due virgolette singole per l'utilizzo come un delimitatore). Esattamente come (e se) viene utilizzato il motore scripting queste informazioni dipendono dal motore di script. Impostare questo parametro su NULL se l'host non utilizzava un delimitatore per contrassegnare la fine del blocco di script.  
  
 `dwFlags`  
 [in] Flag associato al blocco di script. Può essere una combinazione dei valori seguenti:  
  
|Costante|Valore|Descrizione|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|Indica che gli identificatori e operatori punto devono essere identificati con i flag SOURCETEXT_ATTR_IDENTIFIER e SOURCETEXT_ATTR_MEMBERLOOKUP, rispettivamente.|  
|GETATTRFLAG_THIS|0x0100|Indica che l'identificatore per l'oggetto corrente deve essere identificato con il flag SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0x8000|Indica che deve essere identificato testo della stringa di contenuto e il commento con il flag SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [in, out] Buffer che deve contenere gli attributi restituiti.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_NOTIMPL`|L'host Usa solo gli attributi predefiniti.|  
  
## <a name="remarks"></a>Note  
 Questo metodo restituisce gli attributi di testo per un blocco di testo del documento arbitrario. È accettabile per gli host da restituire `E_NOTIMPL`, nel qual caso vengono utilizzati gli attributi predefiniti.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugDocumentHost](../../winscript/reference/idebugdocumenthost-interface.md)   
 [Enumerazione SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)