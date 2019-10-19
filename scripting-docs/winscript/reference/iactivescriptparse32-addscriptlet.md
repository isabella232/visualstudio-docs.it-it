---
title: 'IActiveScriptParse32:: AddScriptlet | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fcf11eb2-8e71-4cca-afda-a91791c243ff
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: b48d89ce2c49bd971fe298d2b4773aad8b65e8c3
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72561690"
---
# <a name="iactivescriptparse32addscriptlet"></a>IActiveScriptParse32::AddScriptlet
Aggiunge un scriptlet di codice allo script. Questo metodo viene utilizzato negli ambienti in cui lo stato persistente dello script è intergemellato con il documento host e l'host è responsabile del ripristino dello script, anziché tramite un'interfaccia `IPersist*`. Gli esempi principali sono i linguaggi di scripting HTML che consentono di associare gli scriptlet di codice incorporato nel documento HTML a eventi intrinseci, ad esempio OnClick = "Button1. Text =' Exit '".  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT AddScriptlet(  
    LPCOLESTR pstrDefaultName,       // address of default name of scriptlet  
    LPCOLESTR pstrCode,              // address of scriptlet text  
    LPCOLESTR pstrItemName,          // address of item name  
    LPCOLESTR pstrSubItemName,       // address of subitem name  
    LPCOLESTR pstrEventName,         // address of event name  
    LPCOLESTR pstrDelimiter,         // address of end-of-scriptlet delimiter  
    DWORD_PTR dwSourceContextCookie, // application-defined value for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // scriptlet flags  
    BSTR *pbstrName,                 // address of actual name of scriptlet  
    EXCEPINFO *pexcepinfo            // address of exception information  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pstrDefaultName`  
 in Indirizzo di un nome predefinito da associare a scriptlet. Se il scriptlet non contiene informazioni di denominazione, come nell'esempio OnClick precedente, questo nome verrà usato per identificare il scriptlet. Se questo parametro è `NULL`, il motore di script produce un nome univoco, se necessario.  
  
 `pstrCode`  
 in Indirizzo del testo di scriptlet da aggiungere. L'interpretazione di questa stringa dipende dal linguaggio di scripting.  
  
 `pstrItemName`  
 in Indirizzo di un buffer che contiene il nome dell'elemento associato a questo scriptlet. Questo parametro, oltre a `pstrSubItemName`, identifica l'oggetto per il quale scriptlet è un gestore eventi.  
  
 `pstrSubItemName`  
 in Indirizzo di un buffer che contiene il nome di un `subobject` dell'elemento denominato a cui è associato il scriptlet; Questo nome deve trovarsi nelle informazioni sul tipo dell'elemento denominato. Questo parametro è NULL se il scriptlet deve essere associato all'elemento denominato invece che a un `subitem`. Questo parametro, oltre a `pstrItemName`, identifica l'oggetto specifico per il quale scriptlet è un gestore eventi.  
  
 `pstrEventName`  
 in Indirizzo di un buffer che contiene il nome dell'evento per il quale scriptlet è un gestore eventi.  
  
 `pstrDelimiter`  
 in Indirizzo del delimitatore di fine del Scriptlet. Quando il parametro `pstrCode` viene analizzato da un flusso di testo, l'host usa in genere un delimitatore, ad esempio due virgolette singole (''), per rilevare la fine del Scriptlet. Questo parametro specifica il delimitatore utilizzato dall'host, consentendo al motore di scripting di fornire una pre-elaborazione condizionale (ad esempio, sostituendo una virgoletta singola ['] con due virgolette singole da utilizzare come delimitatore). Il modo in cui (e se) il motore di scripting utilizza queste informazioni dipende dal motore di scripting. Impostare questo parametro su NULL se l'host non ha usato un delimitatore per contrassegnare la fine di scriptlet.  
  
 `dwSourceContextCookie`  
 in Valore definito dall'applicazione che viene utilizzato a scopo di debug.  
  
 `ulStartingLineNumber`  
 in Valore in base zero che specifica la riga a partire dalla quale inizierà l'analisi.  
  
 `dwFlags`  
 in Flag associati a scriptlet. Può essere una combinazione dei valori seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|SCRIPTTEXT_ISVISIBLE|Indica che il testo dello script deve essere visibile (e, di conseguenza, chiamabile in base al nome) come metodo globale nello spazio dei nomi dello script.|  
|SCRIPTTEXT_ISPERSISTENT|Indica che il codice aggiunto durante la chiamata deve essere salvato nel caso in cui il motore di scripting venga salvato (ad esempio tramite una chiamata a `IPersist*::Save`) o se il motore di scripting viene reimpostato tramite una transizione allo stato inizializzato. Per ulteriori informazioni su questo stato, vedere Stati del motore di script.|  
  
 `pbstrName` ,  
 out Nome effettivo usato per identificare il scriptlet. Questo deve essere in ordine di preferenza: un nome specificato in modo esplicito nel testo scriptlet, il nome predefinito fornito in `pstrDefaultName` o un nome univoco sintetizzato dal motore di script.  
  
 `pexcepinfo` ,  
 out Indirizzo di una struttura contenente informazioni sull'eccezione. Questa struttura deve essere compilata se viene restituito DISP_E_EXCEPTION.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Operazione completata.|  
|`DISP_E_EXCEPTION`|Si è verificata un'eccezione durante l'analisi di scriptlet. Il parametro `pexcepinfo` contiene informazioni sull'eccezione.|  
|`E_INVALIDARG`|Argomento non valido.|  
|`E_NOTIMPL`|Questo metodo non è supportato. il motore di scripting non supporta l'aggiunta di gli scriptlet di sink di evento.|  
|`E_POINTER`|È stato specificato un puntatore non valido.|  
|`E_UNEXPECTED`|La chiamata non era prevista (ad esempio, il motore di scripting non è ancora stato caricato o inizializzato) e pertanto non è riuscito.|  
|`OLESCRIPT_E_INVALIDNAME`|Il nome predefinito specificato non è valido in questo linguaggio di scripting.|  
|`OLESCRIPT_E_SYNTAX`|Si è verificato un errore di sintassi non specificato in scriptlet.|  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)