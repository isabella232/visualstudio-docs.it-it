---
title: IActiveScriptParse::AddScriptlet | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParse.AddScriptlet
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParse_AddScriptlet
ms.assetid: 824929f4-4dd3-473a-92d9-0b96acea2f14
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ee5d76060789118e9051c2d8dcc5fc570617f6a8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62954954"
---
# <a name="iactivescriptparseaddscriptlet"></a>IActiveScriptParse::AddScriptlet
Aggiunge un scriptlet di codice allo script. Questo metodo viene utilizzato in ambienti in cui lo stato persistente dello script è legato a documento host e l'host è responsabile per il ripristino di script, anziché tramite un `IPersist*` interfaccia. Gli esempi primari sono linguaggi di script HTML che consentono gli scriptlet di codice incorporati nel documento HTML da collegare agli eventi intrinseci (ad esempio, ONCLICK="button1.text='Exit'").  
  
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
 [in] Indirizzo di un nome predefinito per associare lo scriptlet. Se lo scriptlet non contiene informazioni sulla denominazione (come nell'esempio ONCLICK precedente), questo nome verrà usato per identificare lo scriptlet. Se questo parametro è `NULL`, il motore di script produce un nome univoco, se necessario.  
  
 `pstrCode`  
 [in] Indirizzo del testo dello scriptlet da aggiungere. L'interpretazione di questa stringa dipende il linguaggio di scripting.  
  
 `pstrItemName`  
 [in] Indirizzo di un buffer che contiene il nome dell'elemento associato a questo scriptlet. Questo parametro, oltre a `pstrSubItemName`, identifica l'oggetto per cui lo scriptlet è un gestore eventi.  
  
 `pstrSubItemName`  
 [in] Indirizzo di un buffer che contiene il nome di un `subobject` dell'elemento denominato con il quale è associato questo scriptlet; questo nome deve essere trovato nelle informazioni sul tipo dell'elemento denominato. Questo parametro è NULL se lo scriptlet deve essere associata all'elemento denominato anziché un `subitem`. Questo parametro, oltre a `pstrItemName`, identifica l'oggetto specifico per cui lo scriptlet è un gestore eventi.  
  
 `pstrEventName`  
 [in] Indirizzo di un buffer che contiene il nome dell'evento per cui lo scriptlet è un gestore eventi.  
  
 `pstrDelimiter`  
 [in] Indirizzo del delimitatore end-of-scriptlet. Quando il `pstrCode` parametro viene analizzato da un flusso di testo, l'host utilizza in genere un delimitatore, ad esempio due virgolette ("), per rilevare la fine dello scriptlet. Questo parametro specifica il delimitatore utilizzato dall'host, consentendo il motore di scripting fornire alcuni condizionale pre-elaborazioni primitive (ad esempio, sostituire una virgoletta singola ['] con due virgolette singole per l'utilizzo come un delimitatore). Esattamente come (e se) di scripting rende motore Usa queste informazioni dipende dal motore di script. Impostare questo parametro su NULL se l'host non utilizzava un delimitatore per contrassegnare la fine dello scriptlet.  
  
 `dwSourceContextCookie`  
 [in] Valore definito dall'applicazione che viene usato a scopo di debug.  
  
 `ulStartingLineNumber`  
 [in] Valore in base zero che specifica la riga dell'analisi in modo che inizi.  
  
 `dwFlags`  
 [in] Flag associati allo scriptlet. Può essere una combinazione dei valori seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|SCRIPTTEXT_ISVISIBLE|Indica che il testo dello script dovrebbe essere visibile (e, di conseguenza, può essere chiamato dal nome) come metodo globale nello spazio dei nomi dello script.|  
|SCRIPTTEXT_ISPERSISTENT|Indica che il codice aggiunto durante la chiamata deve essere salvato se il motore di scripting viene salvato (ad esempio, tramite una chiamata a `IPersist*::Save`), o se il motore di scripting viene reimpostato tramite una transizione allo stato inizializzato. Per ulteriori informazioni su questo stato, vedere Stati del motore di Script.|  
  
 `pbstrName` ,  
 [out] Nome effettivo usato per identificare lo scriptlet. Questa operazione deve essere in ordine di preferenza: nel testo dello scriptlet specificato in modo esplicito un nome, il nome predefinito fornito in `pstrDefaultName`, o un nome univoco sintetizzati dal motore di script.  
  
 `pexcepinfo` ,  
 [out] Indirizzo di una struttura contenente informazioni sull'eccezione. Questa struttura deve essere inserita se viene restituito DISP_E_EXCEPTION.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Operazione completata.|  
|`DISP_E_EXCEPTION`|Si è verificata un'eccezione durante l'analisi dello scriptlet. Il `pexcepinfo` parametro contiene le informazioni sull'eccezione.|  
|`E_INVALIDARG`|Un argomento non valido.|  
|`E_NOTIMPL`|Questo metodo non è supportato. il motore di scripting non supporta l'aggiunta gli scriptlet sink di evento.|  
|`E_POINTER`|È stato specificato un puntatore non valido.|  
|`E_UNEXPECTED`|La chiamata non era previsto (ad esempio, il motore di scripting non è ancora caricato o inizializzato) e pertanto non è riuscita.|  
|`OLESCRIPT_E_INVALIDNAME`|Il nome predefinito fornito non è valido in questo linguaggio di scripting.|  
|`OLESCRIPT_E_SYNTAX`|Nello scriptlet si è verificato un errore di sintassi non specificato.|  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)