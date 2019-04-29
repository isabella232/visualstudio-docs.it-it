---
title: IActiveScriptParseProcedureOld::ParseProcedureText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParseProcedureOld.ParseProcedureText
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptParseProcedureOld::ParseProcedureText
ms.assetid: 21a21313-35ce-432d-b9a6-7999065f19ac
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8e521bbdcd8d7397c1c2dfb377fd9b41811499f5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993215"
---
# <a name="iactivescriptparseprocedureoldparseproceduretext"></a>IActiveScriptParseProcedureOld::ParseProcedureText
Analizza la procedura di codice specificato e aggiunge una routine anonima allo spazio dei nomi.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT ParseProcedureText(  
   LPCOLESTR    pstrCode,  
   LPCOLESTR    pstrFormalParams,  
   LPCOLESTR    pstrItemName,  
   IUnknown*    punkContext,  
   LPCOLESTR    pstrDelimiter,  
   DWORD_PTR    dwSourceContextCookie,  
   ULONG        ulStartingLineNumber,  
   DWORD        dwFlags,  
   IDispatch**  ppdisp  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pstrCode`  
 [in] Il testo della procedura da valutare. L'interpretazione di questa stringa dipende il linguaggio di scripting.  
  
 `pstrFormalParams`  
 [in] Nomi parametri formali per la procedura. I nomi dei parametri devono essere separati con i delimitatori appropriati per il motore di scripting. I nomi non devono essere racchiusi tra parentesi.  
  
 `pstrItemName`  
 [in] Il nome dell'elemento denominato che fornisce il contesto in cui la procedura deve essere valutata. Se questo parametro è `NULL`, il codice viene valutato nel contesto globale del motore di script.  
  
 `punkContext`  
 [in] L'oggetto di contesto. Questo oggetto è riservato per l'uso in un ambiente di debug, in cui tale contesto può essere fornito dal debugger per rappresentare un contesto di runtime attivo. Se questo parametro è `NULL`, il motore utilizza `pstrItemName` per identificare il contesto.  
  
 `pstrDelimiter`  
 [in] Il delimitatore di fine-di-procedure. Quando si `pstrCode` viene analizzata da un flusso di testo, l'host utilizza un delimitatore, in genere, ad esempio due virgolette ("), per rilevare la fine della procedura. Questo parametro specifica il delimitatore utilizzato dall'host, consentendo il motore di scripting fornire alcuni condizionali, pre-elaborazioni primitive (ad esempio, la sostituzione di una virgoletta singola ['] con due virgolette singole per l'utilizzo come un delimitatore). Esattamente come (e se) viene utilizzato il motore scripting queste informazioni dipendono dal motore di script. Impostare questo parametro su `NULL` se l'host non utilizzava un delimitatore per contrassegnare la fine della procedura.  
  
 `dwSourceContextCookie`  
 [in] Valore definito dall'applicazione che viene usato a scopo di debug.  
  
 `ulStartingLineNumber`  
 [in] Valore in base zero che specifica la riga in cui verrà avviata l'analisi.  
  
 `dwFlags`  
 [in] Flag associato con la procedura. Può essere una combinazione di questi valori.  
  
|Costante|Value|Significato|  
|--------------|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|0x00000020|Indica che il codice in `pstrCode` è un'espressione che rappresenta il valore restituito della procedura.|  
|SCRIPTPROC_IMPLICIT_THIS|0x00000100|Indica che il `this` puntatore è incluso nell'ambito della procedura.|  
|SCRIPTPROC_IMPLICIT_PARENTS|0x00000200|Indica che gli elementi padre del `this` puntatore sono inclusi nell'ambito della procedura.|  
  
 `ppdisp`  
 [out] Restituisce un wrapper di recapito in cui il metodo predefinito è la procedura analizzata da questo metodo.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_INVALIDARG`|Un argomento non valido.|  
|`E_POINTER`|È stato specificato un puntatore non valido.|  
|`E_NOTIMPL`|Questo metodo non è supportato. Il motore di scripting non supporta inoltre in fase di esecuzione delle procedure per lo spazio dei nomi.|  
|`E_UNEXPECTED`|La chiamata non era previsto (ad esempio, il motore di scripting è nello stato non inizializzato o chiuso).|  
|`OLESCRIPT_E_SYNTAX`|Si è verificato un errore di sintassi non specificato nella procedura.|  
|`S_FALSE`|Il motore di scripting non supporta un oggetto di distribuzione; il `ppdisp`parametro è impostato su `NULL`.|  
  
## <a name="remarks"></a>Note  
 Nessun codice di script viene valutato durante questa chiamata; piuttosto, la procedura viene compilata in un metodo su `ppdisp` dove può essere chiamata dallo script in un secondo momento.  
  
 Questa interfaccia è deprecata in favore del `IActiveScriptParseProcedure` interfaccia. Il `IActiveScriptParseProcedure::ParseProcedureText` metodo è simile a questo metodo, ma consente di specificare il nome della routine. In tutti i casi, `IActiveScriptParseProcedure::ParseProcedureText` deve essere utilizzato.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptParseProcedureOld Interface](../../winscript/reference/iactivescriptparseprocedureold-interface.md)   
 [IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)