---
title: IActiveScriptParseProcedure32::P arseProcedureText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: ede37171-2f1e-4467-a358-17bd4a4f1869
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 52333d13731b5c31329ee812be403c09cf43d63b
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835732"
---
# <a name="iactivescriptparseprocedure32parseproceduretext"></a>IActiveScriptParseProcedure32::ParseProcedureText
Analizza la procedura del codice specificata e aggiunge la routine allo spazio dei nomi.  
  
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
 in Indirizzo del testo della procedura da valutare. L'interpretazione di questa stringa dipende dal linguaggio di scripting.  
  
 `pstrFormalParams`  
 in Indirizzo dei nomi di parametro formali per la procedura. I nomi dei parametri devono essere separati con i delimitatori appropriati per il motore di scripting. I nomi non devono essere racchiusi tra parentesi.  
  
 `pstrProcedureName`  
 in Indirizzo del nome della stored procedure da analizzare.  
  
 `pstrItemName`  
 in Indirizzo del nome dell'elemento che fornisce il contesto in cui deve essere valutata la procedura. Se questo parametro è `NULL` , il codice viene valutato nel contesto globale del motore di script.  
  
 `punkContext`  
 in Indirizzo dell'oggetto di contesto. Questo oggetto è riservato per l'utilizzo in un ambiente di debug, in cui un contesto di questo tipo può essere fornito dal debugger per rappresentare un contesto attivo della fase di esecuzione. Se questo parametro è `NULL` , il motore utilizza `pstrItemName` per identificare il contesto.  
  
 `pstrDelimiter`  
 in Indirizzo del delimitatore di fine della procedura. Quando `pstrCode` viene analizzato da un flusso di testo, l'host usa in genere un delimitatore, ad esempio due virgolette singole (''), per rilevare la fine della procedura. Questo parametro specifica il delimitatore utilizzato dall'host, consentendo al motore di scripting di fornire una pre-elaborazione condizionale (ad esempio, sostituendo una virgoletta singola ['] con due virgolette singole da utilizzare come delimitatore). Il modo in cui (e se) il motore di scripting utilizza queste informazioni dipende dal motore di scripting. Impostare questo parametro su `NULL` se l'host non utilizza un delimitatore per contrassegnare la fine della procedura.  
  
 `dwSourceContextCookie`  
 in Valore definito dall'applicazione che viene utilizzato a scopo di debug.  
  
 `ulStartingLineNumber`  
 in Valore in base zero che specifica la riga a partire dalla quale inizierà l'analisi.  
  
 `dwFlags`  
 in Flag associati alla procedura. Può essere una combinazione di questi valori:  
  
|valore|Significato|  
|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|Indica che il codice in `pstrCode` è un'espressione che rappresenta il valore restituito della stored procedure. Per impostazione predefinita, il codice può contenere un'espressione, un elenco di istruzioni o qualsiasi altro elemento consentito in una procedura dal linguaggio di script.|  
|SCRIPTPROC_IMPLICIT_THIS|Indica che il `this` puntatore è incluso nell'ambito della procedura.|  
|SCRIPTPROC_IMPLICIT_PARENTS|Indica che gli elementi padre del `this` puntatore sono inclusi nell'ambito della procedura.|  
  
 `ppdisp`  
 out Indirizzo del puntatore per l'oggetto che contiene le proprietà e i metodi globali dello script. Se il motore di scripting non supporta tale oggetto, `NULL` viene restituito.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Operazione completata.|  
|`E_INVALIDARG`|Un argomento non è valido.|  
|`E_POINTER`|È stato specificato un puntatore non valido.|  
|`E_NOTIMPL`|Questo metodo non è supportato. Il motore di scripting non supporta l'aggiunta in fase di esecuzione delle procedure allo spazio dei nomi.|  
|`E_UNEXPECTED`|La chiamata non era prevista (ad esempio, il motore di scripting è nello stato non inizializzato o chiuso).|  
|`OLESCRIPT_E_SYNTAX`|Si è verificato un errore di sintassi non specificato nella procedura.|  
|`S_FALSE`|Il motore di scripting non supporta un oggetto dispatch. il `ppdisp` parametro è impostato su `NULL` .|  
  
## <a name="remarks"></a>Osservazioni  
 Nessun codice di script viene valutato durante la chiamata. la procedura viene invece compilata nello stato di script in cui può essere chiamata successivamente dallo script.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptParseProcedure32](../../winscript/reference/iactivescriptparseprocedure32.md)