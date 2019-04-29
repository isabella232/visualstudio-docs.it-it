---
title: IActiveScriptParse::ParseScriptText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParse.ParseScriptText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParse_ParseScriptText
ms.assetid: 2d237d6c-cc65-415b-8808-72791304a136
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3396aee8c044ee9b84d7d6256c6ad69a99965170
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62954889"
---
# <a name="iactivescriptparseparsescripttext"></a>IActiveScriptParse::ParseScriptText
Analizza lo scriptlet di codice specificato, aggiungendo le dichiarazioni nello spazio dei nomi e la valutazione del codice come appropriato.  
  
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
|`pstrCode`|[in] Indirizzo del testo dello scriptlet da valutare. L'interpretazione di questa stringa dipende il linguaggio di scripting.|  
|`pstrItemName`|[in] Indirizzo del nome dell'elemento che fornisce il contesto in cui lo scriptlet deve essere valutata. Se questo parametro è NULL, il codice viene valutato nel contesto globale del motore di script.|  
|`punkContext`|[in] Indirizzo dell'oggetto di contesto. Questo oggetto è riservato per l'uso in un ambiente di debug, in cui tale contesto può essere fornito dal debugger per rappresentare un contesto di runtime attivo. Se questo parametro è NULL, il motore utilizza `pstrItemName` per identificare il contesto.|  
|`pstrDelimiter`|[in] Indirizzo del delimitatore end-of-scriptlet. Quando si `pstrCode` viene analizzata da un flusso di testo, l'host utilizza un delimitatore, in genere, ad esempio due virgolette ("), per rilevare la fine dello scriptlet. Questo parametro specifica il delimitatore utilizzato dall'host, consentendo il motore di scripting fornire alcuni condizionale pre-elaborazioni primitive (ad esempio, sostituire una virgoletta singola ['] con due virgolette singole per l'utilizzo come un delimitatore). Esattamente come (e se) di scripting rende motore Usa queste informazioni dipende dal motore di script. Impostare questo parametro su `NULL` se l'host non utilizzava un delimitatore per contrassegnare la fine dello scriptlet.|  
|`dwSourceContextCookie`|[in] Cookie utilizzato per scopi di debug.|  
|`ulStartingLineNumber`|[in] Valore in base zero che specifica la riga dell'analisi in modo che inizi.|  
|`dwFlags`|[in] Flag associati allo scriptlet. Può essere una combinazione dei valori seguenti:|  
  
|Value|Significato|  
|-----------|-------------|  
|SCRIPTTEXT_ISEXPRESSION|Se la distinzione tra un'espressione di calcolo e un'istruzione è importante ma sintatticamente ambigua nel linguaggio di script, questo flag specifica che lo scriptlet deve essere interpretato come un'espressione, anziché come un'istruzione o un elenco di istruzioni. Per impostazione predefinita, le istruzioni vengono presupposte a meno che la scelta corretta può essere determinata dalla sintassi del testo dello scriptlet.|  
|SCRIPTTEXT_ISPERSISTENT|Indica che il codice aggiunto durante la chiamata deve essere salvato se il motore di scripting viene salvato (ad esempio, tramite una chiamata a `IPersist*::Save`), o se il motore di scripting viene reimpostato tramite una transizione allo stato inizializzato.|  
|SCRIPTTEXT_ISVISIBLE|Indica che il testo dello script dovrebbe essere visibile (e, di conseguenza, può essere chiamato dal nome) come metodo globale nello spazio dei nomi dello script.|  
  
|||  
|-|-|  
|`pvarResult`|[out] Indirizzo di un buffer che riceve i risultati dell'elaborazione di scriptlet, o `NULL` se il chiamante non prevede risultati (vale a dire, il valore di SCRIPTTEXT_ISEXPRESSION non è impostato).|  
|`pexcepinfo`|[out] Indirizzo di una struttura che riceve le informazioni sull'eccezione. Questa struttura viene compilata se `IActiveScriptParse::ParseScriptText` restituisce DISP_E_EXCEPTION.|  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Operazione completata.|  
|`DISP_E_EXCEPTION`|Si è verificata un'eccezione durante l'elaborazione dello scriptlet. Il `pexcepinfo` parametro contiene le informazioni sull'eccezione.|  
|`E_INVALIDARG`|Un argomento non valido.|  
|`E_POINTER`|È stato specificato un puntatore non valido.|  
|`E_NOTIMPL`|Questo metodo non è supportato. Il motore di scripting non supporta la valutazione in fase di esecuzione di istruzioni o espressioni.|  
|`E_UNEXPECTED`|La chiamata non era previsto (ad esempio, il motore di scripting è nello stato non inizializzato o chiuso, oppure è stato impostato il flag SCRIPTTEXT_ISEXPRESSION e il motore di scripting è nello stato inizializzato).|  
|`OLESCRIPT_E_SYNTAX`|Nello scriptlet si è verificato un errore di sintassi non specificato.|  
  
## <a name="remarks"></a>Note  
 Se il motore di scripting è nello stato inizializzato, non restituirà in realtà alcun codice durante questa chiamata; piuttosto, tale codice viene accodato ed eseguito quando il motore di scripting viene eseguita la transizione allo (o tramite) questo stato avviato. Poiché l'esecuzione non è consentita nello stato inizializzato, è possibile chiamare questo metodo con il flag SCRIPTTEXT_ISEXPRESSION quando è in stato non inizializzato.  
  
 Lo scriptlet può essere un'espressione, un elenco di istruzioni o qualsiasi elemento consentito dal linguaggio di script. Ad esempio, questo metodo viene utilizzato nella valutazione del codice HTML \<SCRIPT > tag, che consente di istruzioni da eseguire quando la pagina HTML viene costruita, anziché limitarsi alla loro compilazione nello script.  
  
 Il codice passato a questo metodo deve essere una parte valida e completa del codice. Ad esempio, in VBScript non è consentito chiamare questo metodo una volta con Sub Function (x) e quindi una seconda volta con `End Sub`. Il parser non deve attendere la seconda chiamata completi la subroutine, ma piuttosto deve generare un errore di analisi in quanto una dichiarazione di subroutine è stata avviata ma non completata.  
  
 Per altre informazioni sugli stati dello script, vedere la sezione degli Stati del motore di Script di [motori di Script di Windows](../../winscript/windows-script-engines.md).  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)