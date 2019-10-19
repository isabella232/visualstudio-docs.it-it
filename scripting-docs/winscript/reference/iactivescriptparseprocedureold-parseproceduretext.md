---
title: IActiveScriptParseProcedureOld::P arseProcedureText | Microsoft Docs
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
ms.openlocfilehash: 116cbc7fac0d53b55c9766945d56ecebd27b6785
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577442"
---
# <a name="iactivescriptparseprocedureoldparseproceduretext"></a>IActiveScriptParseProcedureOld::ParseProcedureText
Analizza la procedura del codice specificata e aggiunge una procedura anonima allo spazio dei nomi.  
  
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
 in Testo della procedura da valutare. L'interpretazione di questa stringa dipende dal linguaggio di scripting.  
  
 `pstrFormalParams`  
 in Nomi dei parametri formali per la procedura. I nomi dei parametri devono essere separati con i delimitatori appropriati per il motore di scripting. I nomi non devono essere racchiusi tra parentesi.  
  
 `pstrItemName`  
 in Nome dell'elemento denominato che fornisce il contesto in cui deve essere valutata la procedura. Se questo parametro è `NULL`, il codice viene valutato nel contesto globale del motore di script.  
  
 `punkContext`  
 in Oggetto di contesto. Questo oggetto è riservato per l'utilizzo in un ambiente di debug, in cui un contesto di questo tipo può essere fornito dal debugger per rappresentare un contesto attivo della fase di esecuzione. Se questo parametro è `NULL`, il motore utilizza `pstrItemName` per identificare il contesto.  
  
 `pstrDelimiter`  
 in Delimitatore di fine della procedura. Quando `pstrCode` viene analizzato da un flusso di testo, l'host usa in genere un delimitatore, ad esempio due virgolette singole (''), per rilevare la fine della procedura. Questo parametro specifica il delimitatore usato dall'host, consentendo al motore di scripting di fornire una pre-elaborazione condizionale e primitiva (ad esempio, sostituendo una virgoletta singola ['] con due virgolette singole da usare come delimitatore). Il modo in cui (e se) il motore di scripting utilizza queste informazioni dipende dal motore di scripting. Impostare questo parametro su `NULL` se l'host non ha usato un delimitatore per contrassegnare la fine della procedura.  
  
 `dwSourceContextCookie`  
 in Valore definito dall'applicazione che viene utilizzato a scopo di debug.  
  
 `ulStartingLineNumber`  
 in Valore in base zero che specifica la riga da cui inizierà l'analisi.  
  
 `dwFlags`  
 in Flag associati alla procedura. Può essere una combinazione di questi valori.  
  
|Costante|Value|Significato|  
|--------------|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|0x00000020|Indica che il codice in `pstrCode` è un'espressione che rappresenta il valore restituito della stored procedure.|  
|SCRIPTPROC_IMPLICIT_THIS|0x00000100|Indica che il puntatore `this` è incluso nell'ambito della procedura.|  
|SCRIPTPROC_IMPLICIT_PARENTS|0x00000200|Indica che gli elementi padre del puntatore `this` sono inclusi nell'ambito della procedura.|  
  
 `ppdisp`  
 out Restituisce un wrapper di distribuzione in cui il metodo predefinito è la procedura analizzata da questo metodo.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_INVALIDARG`|Argomento non valido.|  
|`E_POINTER`|È stato specificato un puntatore non valido.|  
|`E_NOTIMPL`|Questo metodo non è supportato. Il motore di scripting non supporta l'aggiunta in fase di esecuzione delle procedure allo spazio dei nomi.|  
|`E_UNEXPECTED`|La chiamata non era prevista (ad esempio, il motore di scripting è nello stato non inizializzato o chiuso).|  
|`OLESCRIPT_E_SYNTAX`|Si è verificato un errore di sintassi non specificato nella procedura.|  
|`S_FALSE`|Il motore di scripting non supporta un oggetto dispatch. il `ppdisp`parameter è impostato su `NULL`.|  
  
## <a name="remarks"></a>Note  
 Nessun codice di script viene valutato durante la chiamata. la procedura viene invece compilata in un metodo in `ppdisp`, dove può essere chiamata successivamente dallo script.  
  
 Questa interfaccia è deprecata a favore dell'interfaccia `IActiveScriptParseProcedure`. Il metodo `IActiveScriptParseProcedure::ParseProcedureText` è simile a questo metodo, ma consente di specificare il nome della stored procedure. In tutti i casi, è necessario usare `IActiveScriptParseProcedure::ParseProcedureText`.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptParseProcedureOld](../../winscript/reference/iactivescriptparseprocedureold-interface.md)    
 [IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)