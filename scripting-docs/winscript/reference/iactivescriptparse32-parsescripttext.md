---
title: IActiveScriptParse32::P arseScriptText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: f33e454c-69d8-4cab-9150-d1e7fd04786d
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: e26b5cb1790cab38a6544a04307b7e336a952519
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835368"
---
# <a name="iactivescriptparse32parsescripttext"></a>IActiveScriptParse32::ParseScriptText
Analizza il codice scriptlet specificato, aggiungendo le dichiarazioni nello spazio dei nomi e valutando il codice nel modo appropriato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT ParseScriptText(  
    LPCOLESTR pstrCode,              // address of scriptlet text  
    LPCOLESTR pstrItemName,          // address of item name  
    IUnknown *punkContext,           // address of debugging context  
    LPCOLESTR pstrDelimiter,         // address of end-of-scriptlet delimiter  
    DWORD_PTR dwSourceContextCookie, // cookie for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // scriptlet flags  
    VARIANT *pvarResult,             // address of buffer for results  
    EXCEPINFO *pexcepinfo            // address of buffer for error data  
);  
```  
  
#### <a name="parameters"></a>Parametri  
  
|||  
|-|-|  
|`pstrCode`|in Indirizzo del testo scriptlet da valutare. L'interpretazione di questa stringa dipende dal linguaggio di scripting.|  
|`pstrItemName`|in Indirizzo del nome dell'elemento che fornisce il contesto in cui valutare scriptlet. Se questo parametro è NULL, il codice viene valutato nel contesto globale del motore di script.|  
|`punkContext`|in Indirizzo dell'oggetto di contesto. Questo oggetto è riservato per l'utilizzo in un ambiente di debug, in cui un contesto di questo tipo può essere fornito dal debugger per rappresentare un contesto attivo della fase di esecuzione. Se questo parametro è NULL, il motore utilizza `pstrItemName` per identificare il contesto.|  
|`pstrDelimiter`|in Indirizzo del delimitatore di fine del Scriptlet. Quando `pstrCode` viene analizzato da un flusso di testo, l'host usa in genere un delimitatore, ad esempio due virgolette singole (''), per rilevare la fine del Scriptlet. Questo parametro specifica il delimitatore utilizzato dall'host, consentendo al motore di scripting di fornire una pre-elaborazione condizionale (ad esempio, sostituendo una virgoletta singola ['] con due virgolette singole da utilizzare come delimitatore). Il modo in cui (e se) il motore di scripting utilizza queste informazioni dipende dal motore di scripting. Impostare questo parametro su `NULL` se l'host non ha usato un delimitatore per contrassegnare la fine di scriptlet.|  
|`dwSourceContextCookie`|in Cookie usato a scopo di debug.|  
|`ulStartingLineNumber`|in Valore in base zero che specifica la riga a partire dalla quale inizierà l'analisi.|  
|`dwFlags`|in Flag associati a scriptlet. Può essere una combinazione di questi valori:|  
  
|valore|Significato|  
|-----------|-------------|  
|SCRIPTTEXT_ISEXPRESSION|Se la distinzione tra un'espressione di calcolo e un'istruzione è importante ma sintatticamente ambigua nel linguaggio di script, questo flag specifica che scriptlet deve essere interpretato come un'espressione, anziché come un'istruzione o un elenco di istruzioni. Per impostazione predefinita, vengono presupposte le istruzioni, a meno che la scelta corretta non possa essere determinata dalla sintassi del testo scriptlet.|  
|SCRIPTTEXT_ISPERSISTENT|Indica che il codice aggiunto durante la chiamata deve essere salvato nel caso in cui il motore di scripting venga salvato, ad esempio tramite una chiamata a `IPersist*::Save` , o se il motore di scripting viene reimpostato tramite una transizione allo stato inizializzato.|  
|SCRIPTTEXT_ISVISIBLE|Indica che il testo dello script deve essere visibile (e, di conseguenza, chiamabile in base al nome) come metodo globale nello spazio dei nomi dello script.|  
  
|||  
|-|-|  
|`pvarResult`|out Indirizzo di un buffer che riceve i risultati dell'elaborazione di scriptlet o `NULL` se il chiamante non prevede alcun risultato (ovvero, il valore SCRIPTTEXT_ISEXPRESSION non è impostato).|  
|`pexcepinfo`|out Indirizzo di una struttura che riceve informazioni sull'eccezione. Questa struttura viene compilata se `IActiveScriptParse::ParseScriptText` restituisce DISP_E_EXCEPTION.|  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Operazione completata.|  
|`DISP_E_EXCEPTION`|Si è verificata un'eccezione durante l'elaborazione di scriptlet. Il `pexcepinfo` parametro contiene informazioni sull'eccezione.|  
|`E_INVALIDARG`|Un argomento non è valido.|  
|`E_POINTER`|È stato specificato un puntatore non valido.|  
|`E_NOTIMPL`|Questo metodo non è supportato. Il motore di scripting non supporta la valutazione in fase di esecuzione di espressioni o istruzioni.|  
|`E_UNEXPECTED`|La chiamata non era prevista (ad esempio, il motore di scripting è nello stato non inizializzato o chiuso oppure è stato impostato il flag di SCRIPTTEXT_ISEXPRESSION e il motore di scripting è nello stato inizializzato).|  
|`OLESCRIPT_E_SYNTAX`|Si è verificato un errore di sintassi non specificato in scriptlet.|  
  
## <a name="remarks"></a>Osservazioni  
 Se il motore di scripting è nello stato inizializzato, nessun codice verrà effettivamente valutato durante la chiamata. Questo codice viene invece accodato ed eseguito quando il motore di scripting viene passato allo stato Started (o through). Poiché l'esecuzione non è consentita nello stato Initialized, è un errore chiamare questo metodo con il flag SCRIPTTEXT_ISEXPRESSION quando si trova nello stato Initialized.  
  
 Scriptlet può essere un'espressione, un elenco di istruzioni o qualsiasi elemento consentito dal linguaggio di script. Questo metodo, ad esempio, viene usato nella valutazione del tag HTML \<SCRIPT> , che consente l'esecuzione delle istruzioni durante la costruzione della pagina HTML, anziché semplicemente compilarle nello stato dello script.  
  
 Il codice passato a questo metodo deve essere una parte di codice valida e completa. In VBScript, ad esempio, non è consentito chiamare questo metodo una volta con Sub Function (x) e quindi una seconda volta con `End Sub` . Il parser non deve attendere la seconda chiamata per completare la subroutine, bensì deve generare un errore di analisi perché una dichiarazione di subroutine è stata avviata ma non completata.  
  
 Per ulteriori informazioni sugli stati degli script, vedere la sezione Stati del motore di script dei [motori di script Windows](../../winscript/windows-script-engines.md).  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)