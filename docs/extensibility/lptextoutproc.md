---
title: LPTEXTOUTPROC Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- LPTEXTOUTPROC
helpviewer_keywords:
- SccMsgDataOnMessage structure
- SccMsgDataOnBeforeGetFile structure
- SccMsgDataIsCancelled structure
- LPTEXTOUTPROC callback function
- SccMsgDataOnAfterGetFile structure
ms.assetid: 2025c969-e3c7-4cf4-a5c5-099d342895ea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 38c3e8263b9a30058c2de019e5e92160b716aa71
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702797"
---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC

Quando l'utente esegue un'operazione di controllo del codice sorgente dall'interno dell'ambiente di sviluppo integrato (IDE), il plug-in controllo del codice sorgente potrebbe voler trasmettere messaggi di errore o di stato relativi all'operazione. Il plug-in può visualizzare le proprie finestre di messaggio per questo scopo. Tuttavia, per un'integrazione più semplice, il plug-in può passare stringhe all'IDE, che quindi li visualizza nel modo nativo di visualizzare le informazioni sullo stato. Il meccanismo per `LPTEXTOUTPROC` questo è il puntatore a funzione. L'IDE implementa questa funzione (descritta in modo più dettagliato di seguito) per la visualizzazione di errore e stato.

L'IDE passa al plug-in del controllo del codice `lpTextOutProc` sorgente un puntatore a funzione a questa funzione, come parametro , quando si chiama [il SccOpenProject](../extensibility/sccopenproject-function.md). Durante un'operazione SCC, ad esempio, nel mezzo di una chiamata a [SccGet](../extensibility/sccget-function.md) `LPTEXTOUTPROC` che coinvolge molti file, il plug-in può chiamare la funzione, passando periodicamente le stringhe da visualizzare. L'IDE può visualizzare queste stringhe su una barra di stato, in una finestra di output o in una finestra di messaggio separata, in base alle esigenze. Facoltativamente, l'IDE potrebbe essere in grado di visualizzare determinati messaggi con un pulsante Annulla.Optionally, the IDE may be able to display certain messages with **a Cancel** button. Ciò consente all'utente di annullare l'operazione e offre all'IDE la possibilità di passare queste informazioni al plug-in.

## <a name="signature"></a>Firma
 La funzione di output dell'IDE ha la firma seguente:The IDE's output function has the following signature:

```cpp
typedef LONG (*LPTEXTOUTPROC) (
   LPSTR display_string,
   LONG mesg_type
);
```

## <a name="parameters"></a>Parametri

display_string

Stringa di testo da visualizzare. Questa stringa non deve essere terminata con un ritorno a capo o un avanzamento riga.

mesg_type

Tipo di messaggio. Nella tabella seguente sono elencati i valori supportati per questo parametro.

|valore|Descrizione|
|-----------|-----------------|
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|Il messaggio è considerato Informazioni, Avviso o Errore.|
|`SCC_MSG_STATUS`|Il messaggio mostra lo stato e può essere visualizzato nella barra di stato.|
|`SCC_MSG_DOCANCEL`|Inviato senza stringa di messaggio.|
|`SCC_MSG_STARTCANCEL`|Avvia la visualizzazione di un pulsante **Annulla.**|
|`SCC_MSG_STOPCANCEL`|Interrompe la visualizzazione di un pulsante **Annulla.**|
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|Chiede IDE se l'operazione in background deve `SCC_MSG_RTN_CANCEL` essere annullata: IDE restituisce se l'operazione è stata annullata; in caso `SCC_MSG_RTN_OK`contrario, restituisce . Il `display_string` parametro viene eseguito il cast come una struttura [SccMsgDataIsCancelled,](#LinkSccMsgDataIsCancelled) fornita dal plug-in del controllo del codice sorgente.|
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|Indica all'IDE di un file prima che venga recuperato dal controllo della versione. Il `display_string` cast del parametro viene eseguito come una struttura [SccMsgDataOnBeforeGetFile,](#LinkSccMsgDataOnBeforeGetFile) fornita dal plug-in del controllo del codice sorgente.|
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|Indica all'IDE di un file dopo che è stato recuperato dal controllo della versione. Il `display_string` cast del parametro viene eseguito come una struttura [SccMsgDataOnAfterGetFile,](#LinkSccMsgDataOnAfterGetFile) fornita dal plug-in del controllo del codice sorgente.|
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|Indica all'IDE lo stato corrente di un'operazione in background. Il `display_string` valore del parametro viene eseguito come struttura [SccMsgDataOnMessage,](#LinkSccMsgDataOnMessage) fornita dal plug-in del controllo del codice sorgente.|

## <a name="return-value"></a>Valore restituito

|valore|Descrizione|
|-----------|-----------------|
|SCC_MSG_RTN_OK|La stringa è stata visualizzata o l'operazione è stata completata correttamente.|
|SCC_MSG_RTN_CANCEL|L'utente desidera annullare l'operazione.|

## <a name="example"></a>Esempio
 Si supponga che l'IDE chiama [SccGet](../extensibility/sccget-function.md) con venti nomi di file. Il plug-in del controllo del codice sorgente desidera impedire l'annullamento dell'operazione nel mezzo di un get di file. Dopo aver ottenuto `lpTextOutProc`ogni file, chiama , passando le `SCC_MSG_DOCANCEL` informazioni sullo stato su ogni file e invia un messaggio se non ha lo stato da segnalare. Se in qualsiasi momento il plug-in `SCC_MSG_RTN_CANCEL` riceve un valore restituito di dall'IDE, annulla immediatamente l'operazione get, in modo che non vengano recuperati altri file.

## <a name="structures"></a>Strutture

### <a name="sccmsgdataiscancelled"></a><a name="LinkSccMsgDataIsCancelled"></a>SccMsgDataIsCancelled

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
} SccMsgDataIsCancelled;
```

 Questa struttura viene `SCC_MSG_BACKGROUND_IS_CANCELLED` inviata con il messaggio. Viene utilizzato per comunicare l'ID dell'operazione in background annullata.

### <a name="sccmsgdataonbeforegetfile"></a><a name="LinkSccMsgDataOnBeforeGetFile"></a>SccMsgDataOnBeforeGetFile

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
} SccMsgDataOnBeforeGetFile;
```

 Questa struttura viene `SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE` inviata con il messaggio. Viene utilizzato per comunicare il nome del file che sta per essere recuperato e l'ID dell'operazione in background che esegue il recupero.

### <a name="sccmsgdataonaftergetfile"></a><a name="LinkSccMsgDataOnAfterGetFile"></a>SccMsgDataOnAfterGetFile

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
   SCCRTN sResult;
} SccMsgDataOnAfterGetFile;
```

 Questa struttura viene `SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE` inviata con il messaggio. Viene utilizzato per comunicare il risultato del recupero del file specificato e l'ID dell'operazione in background che ha eseguito il recupero. Vedere i valori restituiti per [SccGet](../extensibility/sccget-function.md) per ciò che può essere specificato come risultato.

### <a name="sccmsgdataonmessage"></a><a name="LinkSccMsgDataOnMessage"></a>SccMsgDataOnMessage

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szMessage;
   BOOL bIsError;
} SccMsgDataOnMessage;
```

 Questa struttura viene `SCC_MSG_BACKGROUND_ON_MESSAGE` inviata con il messaggio. Viene utilizzato per comunicare lo stato corrente di un'operazione in background. Lo stato è espresso come stringa che deve essere `bIsError` visualizzata dall'IDE`TRUE` e indica la gravità del messaggio (per un messaggio di errore; `FALSE` per un avviso o per un messaggio informativo). Viene inoltre fornito l'ID dell'operazione in background che invia lo stato.

## <a name="code-example"></a>Esempio di codice
 Ecco un breve esempio `LPTEXTOUTPROC` di `SCC_MSG_BACKGROUND_ON_MESSAGE` chiamata per inviare il messaggio, mostrando come eseguire il cast della struttura per la chiamata.

```cpp
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
- [Callback functions implemented by the IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)
