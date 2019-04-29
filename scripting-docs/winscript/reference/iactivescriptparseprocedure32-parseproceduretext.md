---
title: IActiveScriptParseProcedure32::ParseProcedureText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ede37171-2f1e-4467-a358-17bd4a4f1869
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: e772d8276de5528f0aed25278a03725d09edb180
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993397"
---
# <a name="iactivescriptparseprocedure32parseproceduretext"></a>IActiveScriptParseProcedure32::ParseProcedureText
Analizza la procedura di codice specificato e aggiunge la procedura per lo spazio dei nomi.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT ParseProcedureText(  
    LPCOLESTR pstrCode,              // address of procedure text  
    LPCOLESTR pstrFormalParams,      // address of formal parameter names  
    LPCOLESTR pstrProcedureName,     // address of procedure name  
    LPCOLESTR pstrItemName,          // address of item name  
    IUnknown *punkContext,           // address of debugging context  
    LPCOLESTR pstrDelimiter,         // address of end-of-procedure delimiter  
    DWORD_PTR dwSourceContextCookie, // application-defined value for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // procedure flags  
    IDispatch **ppdisp               // receives IDispatch pointer  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pstrCode`  
 [in] Indirizzo del testo procedure da valutare. L'interpretazione di questa stringa dipende il linguaggio di scripting.  
  
 `pstrFormalParams`  
 [in] Indirizzo di nomi di parametri formali per la procedura. I nomi dei parametri devono essere separati con i delimitatori appropriati per il motore di scripting. I nomi non devono essere racchiusi tra parentesi.  
  
 `pstrProcedureName`  
 [in] Indirizzo del nome della routine deve essere analizzato.  
  
 `pstrItemName`  
 [in] Indirizzo del nome dell'elemento che fornisce il contesto in cui la procedura deve essere valutata. Se questo parametro è `NULL`, il codice viene valutato nel contesto globale del motore di script.  
  
 `punkContext`  
 [in] Indirizzo dell'oggetto di contesto. Questo oggetto è riservato per l'uso in un ambiente di debug, in cui tale contesto può essere fornito dal debugger per rappresentare un contesto di runtime attivo. Se questo parametro è `NULL`, il motore utilizza `pstrItemName` per identificare il contesto.  
  
 `pstrDelimiter`  
 [in] Indirizzo del delimitatore end di procedura. Quando si `pstrCode` viene analizzata da un flusso di testo, l'host utilizza un delimitatore, in genere, ad esempio due virgolette ("), per rilevare la fine della procedura. Questo parametro specifica il delimitatore utilizzato dall'host, consentendo il motore di scripting fornire alcuni condizionale pre-elaborazioni primitive (ad esempio, sostituire una virgoletta singola ['] con due virgolette singole per l'utilizzo come un delimitatore). Esattamente come (e se) di scripting rende motore Usa queste informazioni dipende dal motore di script. Impostare questo parametro su `NULL` se l'host non utilizzava un delimitatore per contrassegnare la fine della procedura.  
  
 `dwSourceContextCookie`  
 [in] Valore definito dall'applicazione che viene usato a scopo di debug.  
  
 `ulStartingLineNumber`  
 [in] Valore in base zero che specifica la riga dell'analisi in modo che inizi.  
  
 `dwFlags`  
 [in] Flag associato con la procedura. Può essere una combinazione dei valori seguenti:  
  
|Value|Significato|  
|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|Indica che il codice in `pstrCode` è un'espressione che rappresenta il valore restituito della procedura. Per impostazione predefinita, il codice può contenere un'espressione, un elenco di istruzioni o qualsiasi elemento altrimenti consentito in una procedura per il linguaggio di scripting.|  
|SCRIPTPROC_IMPLICIT_THIS|Indica che il `this` puntatore è incluso nell'ambito della procedura.|  
|SCRIPTPROC_IMPLICIT_PARENTS|Indica che gli elementi padre del `this` puntatore sono inclusi nell'ambito della procedura.|  
  
 `ppdisp`  
 [out] Indirizzo del puntatore per l'oggetto che contiene i metodi globali e le proprietà dello script. Se il motore di scripting non supporta tale tipo di oggetto, `NULL` viene restituito.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Operazione completata.|  
|`E_INVALIDARG`|Un argomento non valido.|  
|`E_POINTER`|È stato specificato un puntatore non valido.|  
|`E_NOTIMPL`|Questo metodo non è supportato. Il motore di scripting non supporta inoltre in fase di esecuzione delle procedure per lo spazio dei nomi.|  
|`E_UNEXPECTED`|La chiamata non era previsto (ad esempio, il motore di scripting è nello stato non inizializzato o chiuso).|  
|`OLESCRIPT_E_SYNTAX`|Si è verificato un errore di sintassi non specificato nella procedura.|  
|`S_FALSE`|Il motore di scripting non supporta un oggetto di distribuzione; il `ppdisp` parametro è impostato su `NULL`.|  
  
## <a name="remarks"></a>Note  
 Nessun codice di script viene valutato durante questa chiamata; piuttosto, la procedura viene compilata nello script in cui può essere chiamata dallo script in un secondo momento.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptParseProcedure32](../../winscript/reference/iactivescriptparseprocedure32.md)