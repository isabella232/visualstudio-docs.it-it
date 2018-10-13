---
title: LPTEXTOUTPROC | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- LPTEXTOUTPROC
helpviewer_keywords:
- SccMsgDataOnMessage structure
- SccMsgDataOnBeforeGetFile structure
- SccMsgDataIsCancelled structure
- LPTEXTOUTPROC callback function
- SccMsgDataOnAfterGetFile structure
ms.assetid: 2025c969-e3c7-4cf4-a5c5-099d342895ea
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d5ef5d1c5e92282de6454ca3da8c2adbb8914248
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49266948"
---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando l'utente esegue un'operazione di controllo codice sorgente all'interno dell'ambiente di sviluppo integrato (IDE), il plug-in del controllo del codice sorgente potrebbe essere necessario trasmettere i messaggi di stato o di errore relativi al funzionamento. Il plug-in può visualizzare il proprio le finestre di messaggio per questo scopo. Tuttavia, per più facile integrazione, il plug-in possono passare stringhe all'IDE, che quindi li visualizza in modo nativo per la visualizzazione di informazioni sullo stato. Il meccanismo per questo è il `LPTEXTOUTPROC` puntatore a funzione. L'IDE implementa questa funzione (descritta in dettaglio più avanti) per la visualizzazione di errore e stato.  
  
 L'IDE passa il controllo del codice sorgente del plug-in un puntatore a funzione a questa funzione, come le `lpTextOutProc` parametro, quando si chiama il [SccOpenProject](../extensibility/sccopenproject-function.md). Durante un'operazione di controllo del codice sorgente, ad esempio, all'interno di una chiamata ai [SccGet](../extensibility/sccget-function.md) che interessa numerosi file, può chiamare il plug-in di `LPTEXTOUTPROC` funzione periodicamente passando stringhe da visualizzare. L'IDE può visualizzare queste stringhe in una barra di stato, in una finestra di output, o in una finestra di messaggio separata, come appropriato. Facoltativamente, l'IDE potrebbe essere in grado di visualizzare alcuni messaggi con una **annullare** pulsante. Ciò consente all'utente di annullare l'operazione e offre l'IDE la possibilità di passare queste informazioni per il plug-in.  
  
## <a name="signature"></a>Signature  
 L'IDE di output (funzione) ha la firma seguente:  
  
```cpp#  
typedef LONG (*LPTEXTOUTPROC) (  
   LPSTR display_string,  
   LONG mesg_type  
);  
```  
  
## <a name="parameters"></a>Parametri  
 display_string  
 Una stringa di testo da visualizzare. Questa stringa non deve essere terminata con un ritorno a capo o ritorno a capo/avanzamento riga.  
  
 mesg_type  
 Tipo di messaggio. La tabella seguente elenca i valori supportati per questo parametro.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|Il messaggio è considerato informazioni, avviso o errore.|  
|`SCC_MSG_STATUS`|Il messaggio Mostra lo stato e può essere visualizzato nella barra di stato.|  
|`SCC_MSG_DOCANCEL`|Con nessuna stringa di messaggio inviato.|  
|`SCC_MSG_STARTCANCEL`|Inizia la visualizzazione di un **annullare** pulsante.|  
|`SCC_MSG_STOPCANCEL`|Non verrà più visualizzato una **annullare** pulsante.|  
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|Chiede IDE se l'operazione in background deve essere annullata: restituisce IDE `SCC_MSG_RTN_CANCEL` se l'operazione è stata annullata; in caso contrario, restituisce `SCC_MSG_RTN_OK`. Il `display_string` parametro viene eseguito il cast come un [SccMsgDataIsCancelled](#LinkSccMsgDataIsCancelled) struttura, che viene fornito per il plug-in del controllo del codice sorgente.|  
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|Indica all'IDE relative a un file prima che vengano recuperati dal controllo della versione. Il `display_string` parametro viene eseguito il cast come un [SccMsgDataOnBeforeGetFile](#LinkSccMsgDataOnBeforeGetFile) struttura, che viene fornito per il plug-in del controllo del codice sorgente.|  
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|Indica all'IDE relative a un file dopo che è stato recuperato dal controllo della versione. Il `display_string` parametro viene eseguito il cast come un [SccMsgDataOnAfterGetFile](#LinkSccMsgDataOnAfterGetFile) struttura, che viene fornito per il plug-in del controllo del codice sorgente.|  
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|Indica all'IDE dello stato corrente di un'operazione in background. Il `display_string` parametro viene eseguito il cast come un [SccMsgDataOnMessage](#LinkSccMsgDataOnMessage) struttura, che viene fornito per il plug-in del controllo del codice sorgente.|  
  
## <a name="return-value"></a>Valore restituito  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_MSG_RTN_OK|Zobrazilo se la stringa o l'operazione è stata completata correttamente.|  
|SCC_MSG_RTN_CANCEL|L'utente desidera annullare l'operazione.|  
  
## <a name="example"></a>Esempio  
 Si supponga che le chiamate dell'IDE di [SccGet](../extensibility/sccget-function.md) con 20 nomi di file. Il plug-in del controllo del codice sorgente desidera impedire l'annullamento dell'operazione all'interno di un'operazione get file. Dopo aver ottenuto ogni file, viene chiamato `lpTextOutProc`, passando le informazioni sullo stato per ogni file e invia un `SCC_MSG_DOCANCEL` il messaggio se non dispone di alcun stato da segnalare. Se in qualsiasi momento il plug-in riceve un valore restituito di `SCC_MSG_RTN_CANCEL` dall'IDE, Annulla l'operazione get immediatamente, in modo che nessun altro file vengono recuperato.  
  
## <a name="structures"></a>Strutture  
  
###  <a name="LinkSccMsgDataIsCancelled"></a> SccMsgDataIsCancelled  
  
```cpp#  
typedef struct {  
   DWORD dwBackgroundOperationID;  
} SccMsgDataIsCancelled;  
```  
  
 Questa struttura viene inviata con il `SCC_MSG_BACKGROUND_IS_CANCELLED` messaggio. Viene utilizzato per comunicare l'ID dell'operazione in background che è stata annullata.  
  
###  <a name="LinkSccMsgDataOnBeforeGetFile"></a> SccMsgDataOnBeforeGetFile  
  
```cpp#  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
} SccMsgDataOnBeforeGetFile;  
```  
  
 Questa struttura viene inviata con il `SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE` messaggio. Viene utilizzato per comunicare l'ID dell'operazione in background che esegue il recupero e il nome del file sta per essere recuperato.  
  
###  <a name="LinkSccMsgDataOnAfterGetFile"></a> SccMsgDataOnAfterGetFile  
  
```cpp#  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
   SCCRTN sResult;  
} SccMsgDataOnAfterGetFile;  
```  
  
 Questa struttura viene inviata con il `SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE` messaggio. Viene utilizzato per comunicare il risultato del recupero del file specificato, nonché l'ID dell'operazione in background che ha eseguito il recupero. Vedere i valori restituiti per il [SccGet](../extensibility/sccget-function.md) per ciò che è possibile assegnare di conseguenza.  
  
###  <a name="LinkSccMsgDataOnMessage"></a> SccMsgDataOnMessage  
 [C++]  
  
```  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szMessage;  
   BOOL bIsError;  
} SccMsgDataOnMessage;  
```  
  
 Questa struttura viene inviata con il `SCC_MSG_BACKGROUND_ON_MESSAGE` messaggio. Viene utilizzato per comunicare lo stato corrente di un'operazione in background. Lo stato viene espresso sotto forma di stringa da visualizzare tramite l'IDE e `bIsError` indica la gravità del messaggio (`TRUE` per un messaggio di errore. `FALSE` per un avviso o per un messaggio informativo). L'ID dell'operazione in background inviare lo stato viene inoltre assegnata.  
  
## <a name="code-example"></a>Esempio di codice  
 Ecco un breve esempio della chiamata al metodo `LPTEXTOUTPROC` per inviare il `SCC_MSG_BACKGROUND_ON_MESSAGE` messaggio, che illustra come eseguire il cast della struttura per la chiamata.  
  
```cpp#  
LONG SendStatusMessage(  
    LPTEXTOUTPROC pTextOutProc,  
    DWORD         dwBackgroundID,  
    LPCTSTR       pStatusMsg,  
    BOOL          bIsError)  
{  
    SccMsgDataOnMessage msgData = { 0 };  
    LONG                result  = 0;  
  
    msgData.dwBackgroundOperationID = dwBackgroundID;  
    msgData.szMessage               = pStatusMsg;  
    msgData.bIsError                = bIsError;  
  
    result = pTextOutProc(reinterpret_cast<LPCTSTR>(&msgData), SCC_MSG_BACKGROUND_ON_MESSAGE);  
    return result;  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni di callback implementate dall'IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)

