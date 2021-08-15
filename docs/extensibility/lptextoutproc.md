---
title: LPTEXTOUTPROC | Microsoft Docs
description: Informazioni sul puntatore a funzione LPTEXTOUTPROC. L Visual Studio IDE implementa la funzione per visualizzare l'errore e lo stato.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- LPTEXTOUTPROC
helpviewer_keywords:
- SccMsgDataOnMessage structure
- SccMsgDataOnBeforeGetFile structure
- SccMsgDataIsCancelled structure
- LPTEXTOUTPROC callback function
- SccMsgDataOnAfterGetFile structure
ms.assetid: 2025c969-e3c7-4cf4-a5c5-099d342895ea
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: b266ea06ce79d0028e289210c7bfc11c62ea5ccde0f5050e246b38a4f06f5b16
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121321194"
---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC

Quando l'utente esegue un'operazione di controllo del codice sorgente dall'interno dell'ambiente di sviluppo integrato (IDE), il plug-in del controllo del codice sorgente potrebbe voler trasmettere messaggi di errore o di stato relativi all'operazione. A questo scopo, il plug-in può visualizzare le proprie finestre di messaggio. Tuttavia, per una migliore integrazione, il plug-in può passare stringhe all'IDE, che le visualizza in modo nativo per visualizzare le informazioni sullo stato. Il meccanismo per questo è il `LPTEXTOUTPROC` puntatore a funzione. L'IDE implementa questa funzione (descritta più dettagliatamente di seguito) per visualizzare l'errore e lo stato.

L'IDE passa al plug-in del controllo del codice sorgente un puntatore a funzione a questa funzione, come parametro, quando si `lpTextOutProc` chiama [SccOpenProject.](../extensibility/sccopenproject-function.md) Durante un'operazione SCC, ad esempio, durante una chiamata a [SccGet](../extensibility/sccget-function.md) che interessa molti file, il plug-in può chiamare la funzione , passando periodicamente stringhe da `LPTEXTOUTPROC` visualizzare. L'IDE può visualizzare queste stringhe in una barra di stato, in una finestra di output o in una finestra di messaggio separata, in base alle esigenze. Facoltativamente, l'IDE potrebbe essere in grado di visualizzare determinati messaggi con un **pulsante** Annulla. Ciò consente all'utente di annullare l'operazione e offre all'IDE la possibilità di passare queste informazioni al plug-in.

## <a name="signature"></a>Firma
 La funzione di output dell'IDE ha la firma seguente:

```cpp
typedef LONG (*LPTEXTOUTPROC) (
   LPSTR display_string,
   LONG mesg_type
);
```

## <a name="parameters"></a>Parametri

display_string

Stringa di testo da visualizzare. Questa stringa non deve terminare con un ritorno a capo o un avanzamento riga.

mesg_type

Tipo di messaggio. Nella tabella seguente sono elencati i valori supportati per questo parametro.

|Valore|Descrizione|
|-----------|-----------------|
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|Il messaggio è considerato Informazioni, Avviso o Errore.|
|`SCC_MSG_STATUS`|Il messaggio mostra lo stato e può essere visualizzato nella barra di stato.|
|`SCC_MSG_DOCANCEL`|Inviato senza stringa di messaggio.|
|`SCC_MSG_STARTCANCEL`|Inizia a visualizzare un **pulsante** Annulla.|
|`SCC_MSG_STOPCANCEL`|Arresta la visualizzazione di **un pulsante** Annulla.|
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|Chiede all'IDE se l'operazione in background deve essere annullata: l'IDE restituisce se l'operazione è stata `SCC_MSG_RTN_CANCEL` annullata; in caso contrario, restituisce `SCC_MSG_RTN_OK` . Viene `display_string` eseguito il cast del parametro come struttura [SccMsgDataIsCancelled,](#LinkSccMsgDataIsCancelled) fornita dal plug-in del controllo del codice sorgente.|
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|Indica all'IDE un file prima che venga recuperato dal controllo della versione. Viene eseguito il cast del parametro come `display_string` [struttura SccMsgDataOnBeforeGetFile,](#LinkSccMsgDataOnBeforeGetFile) fornita dal plug-in del controllo del codice sorgente.|
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|Indica all'IDE un file dopo che è stato recuperato dal controllo della versione. Viene eseguito il cast del parametro come `display_string` [struttura SccMsgDataOnAfterGetFile,](#LinkSccMsgDataOnAfterGetFile) fornita dal plug-in del controllo del codice sorgente.|
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|Indica all'IDE lo stato corrente di un'operazione in background. Viene `display_string` eseguito il cast del parametro come struttura [SccMsgDataOnMessage,](#LinkSccMsgDataOnMessage) fornita dal plug-in del controllo del codice sorgente.|

## <a name="return-value"></a>Valore restituito

|Valore|Descrizione|
|-----------|-----------------|
|SCC_MSG_RTN_OK|La stringa è stata visualizzata o l'operazione è stata completata correttamente.|
|SCC_MSG_RTN_CANCEL|L'utente vuole annullare l'operazione.|

## <a name="example"></a>Esempio
 Si supponga che l'IDE [chiami SccGet](../extensibility/sccget-function.md) con venti nomi di file. Il plug-in del controllo del codice sorgente vuole impedire l'annullamento dell'operazione nel mezzo di un file get. Dopo aver ricevuto ogni file, chiama , passando le informazioni sullo stato in ogni file e invia un messaggio se non ha `lpTextOutProc` `SCC_MSG_DOCANCEL` stato da segnalare. Se in qualsiasi momento il plug-in riceve un valore restituito dall'IDE, annulla immediatamente l'operazione get, in modo che non venga recuperato `SCC_MSG_RTN_CANCEL` alcun altro file.

## <a name="structures"></a>Strutture

### <a name="sccmsgdataiscancelled"></a><a name="LinkSccMsgDataIsCancelled"></a> SccMsgDataIsCancelled

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
} SccMsgDataIsCancelled;
```

 Questa struttura viene inviata con il `SCC_MSG_BACKGROUND_IS_CANCELLED` messaggio. Viene usato per comunicare l'ID dell'operazione in background annullata.

### <a name="sccmsgdataonbeforegetfile"></a><a name="LinkSccMsgDataOnBeforeGetFile"></a> SccMsgDataOnBeforeGetFile

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
} SccMsgDataOnBeforeGetFile;
```

 Questa struttura viene inviata con il `SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE` messaggio. Viene usato per comunicare il nome del file che sta per essere recuperato e l'ID dell'operazione in background che sta eseguendo il recupero.

### <a name="sccmsgdataonaftergetfile"></a><a name="LinkSccMsgDataOnAfterGetFile"></a> SccMsgDataOnAfterGetFile

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
   SCCRTN sResult;
} SccMsgDataOnAfterGetFile;
```

 Questa struttura viene inviata con il `SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE` messaggio. Viene usato per comunicare il risultato del recupero del file specificato e l'ID dell'operazione in background che ha avuto esito il recupero. Vedere i valori restituiti per [SccGet](../extensibility/sccget-function.md) per informazioni su ciò che è possibile specificare come risultato.

### <a name="sccmsgdataonmessage"></a><a name="LinkSccMsgDataOnMessage"></a> SccMsgDataOnMessage

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szMessage;
   BOOL bIsError;
} SccMsgDataOnMessage;
```

 Questa struttura viene inviata con il `SCC_MSG_BACKGROUND_ON_MESSAGE` messaggio. Viene usato per comunicare lo stato corrente di un'operazione in background. Lo stato è espresso come stringa da visualizzare nell'IDE e indica la gravità del messaggio ( per un messaggio di errore, per un avviso o per un messaggio `bIsError` `TRUE` `FALSE` informativo). Viene fornito anche l'ID dell'operazione in background che invia lo stato.

## <a name="code-example"></a>Esempio di codice
 Di seguito è riportato un breve esempio di `LPTEXTOUTPROC` chiamata a per inviare il messaggio, che mostra come eseguire il cast della struttura per la `SCC_MSG_BACKGROUND_ON_MESSAGE` chiamata.

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

## <a name="see-also"></a>Vedi anche
- [Funzioni di callback implementate dall'IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)
