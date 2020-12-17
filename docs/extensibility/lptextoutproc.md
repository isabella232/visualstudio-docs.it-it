---
title: LPTEXTOUTPROC | Microsoft Docs
description: Informazioni sul puntatore alla funzione LPTEXTOUTPROC. L'IDE di Visual Studio implementa la funzione per la visualizzazione degli errori e dello stato.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: a04f47a6500c0cd2174d0567029a4f5c86d9f62d
ms.sourcegitcommit: d485b18e46ec4cf08704b5a8d0657bc716ec8393
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/17/2020
ms.locfileid: "97615727"
---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC

Quando l'utente esegue un'operazione del controllo del codice sorgente dall'interno del Integrated Development Environment (IDE), il plug-in del controllo del codice sorgente potrebbe voler inviare messaggi di errore o di stato relativi all'operazione. Il plug-in può visualizzare le proprie finestre di messaggio a questo scopo. Tuttavia, per un'integrazione più trasparente, il plug-in può passare le stringhe all'IDE, che quindi le Visualizza in modo nativo per visualizzare le informazioni sullo stato. Il meccanismo è il puntatore a `LPTEXTOUTPROC` funzione. L'IDE implementa questa funzione (descritta in dettaglio più avanti) per la visualizzazione di errori e stato.

L'IDE passa al plug-in del controllo del codice sorgente un puntatore a funzione per questa funzione, come `lpTextOutProc` parametro, quando si chiama [SccOpenProject](../extensibility/sccopenproject-function.md). Durante un'operazione di SCC, ad esempio, nel mezzo di una chiamata a [SccGet](../extensibility/sccget-function.md) che coinvolgono molti file, il plug-in può chiamare la `LPTEXTOUTPROC` funzione, passando periodicamente le stringhe da visualizzare. L'IDE può visualizzare queste stringhe su una barra di stato, in una finestra di output o in una finestra di messaggio separata, a seconda dei casi. Facoltativamente, è possibile che l'IDE sia in grado di visualizzare determinati messaggi con un pulsante **Annulla** . Ciò consente all'utente di annullare l'operazione e fornisce all'IDE la possibilità di passare le informazioni al plug-in.

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

|valore|Descrizione|
|-----------|-----------------|
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|Il messaggio è considerato informazioni, avviso o errore.|
|`SCC_MSG_STATUS`|Il messaggio Mostra lo stato e può essere visualizzato nella barra di stato.|
|`SCC_MSG_DOCANCEL`|Inviato senza stringa di messaggio.|
|`SCC_MSG_STARTCANCEL`|Inizia a visualizzare un pulsante **Annulla** .|
|`SCC_MSG_STOPCANCEL`|Interrompe la visualizzazione di un pulsante **Annulla** .|
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|Chiede all'IDE se l'operazione in background deve essere annullata: IDE restituisce `SCC_MSG_RTN_CANCEL` se l'operazione è stata annullata; in caso contrario, restituisce `SCC_MSG_RTN_OK` . `display_string`Viene eseguito il cast del parametro come struttura [SccMsgDataIsCancelled](#LinkSccMsgDataIsCancelled) , fornita dal plug-in del controllo del codice sorgente.|
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|Indica all'IDE un file prima che venga recuperato dal controllo della versione. `display_string`Viene eseguito il cast del parametro come struttura [SccMsgDataOnBeforeGetFile](#LinkSccMsgDataOnBeforeGetFile) , fornita dal plug-in del controllo del codice sorgente.|
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|Indica all'IDE un file dopo che è stato recuperato dal controllo della versione. `display_string`Viene eseguito il cast del parametro come struttura [SccMsgDataOnAfterGetFile](#LinkSccMsgDataOnAfterGetFile) , fornita dal plug-in del controllo del codice sorgente.|
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|Indica all'IDE lo stato corrente di un'operazione in background. `display_string`Viene eseguito il cast del parametro come struttura [SccMsgDataOnMessage](#LinkSccMsgDataOnMessage) , fornita dal plug-in del controllo del codice sorgente.|

## <a name="return-value"></a>Valore restituito

|valore|Descrizione|
|-----------|-----------------|
|SCC_MSG_RTN_OK|La stringa è stata visualizzata oppure l'operazione è stata completata correttamente.|
|SCC_MSG_RTN_CANCEL|L'utente desidera annullare l'operazione.|

## <a name="example"></a>Esempio
 Si supponga che l'IDE chiami [SccGet](../extensibility/sccget-function.md) con venti nomi di file. Il plug-in del controllo del codice sorgente vuole impedire l'annullamento dell'operazione all'interno di un file Get. Dopo aver ricevuto ogni file, viene chiamato `lpTextOutProc` , passato le informazioni sullo stato di ogni file e viene inviato un `SCC_MSG_DOCANCEL` messaggio se non è presente alcuno stato per il report. Se in qualsiasi momento il plug-in riceve un valore restituito `SCC_MSG_RTN_CANCEL` dall'IDE, annulla immediatamente l'operazione di recupero, in modo che non vengano recuperati altri file.

## <a name="structures"></a>Strutture

### <a name="sccmsgdataiscancelled"></a><a name="LinkSccMsgDataIsCancelled"></a> SccMsgDataIsCancelled

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
} SccMsgDataIsCancelled;
```

 Questa struttura viene inviata con il `SCC_MSG_BACKGROUND_IS_CANCELLED` messaggio. Viene utilizzato per comunicare l'ID dell'operazione in background annullata.

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

 Questa struttura viene inviata con il `SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE` messaggio. Viene utilizzato per comunicare il risultato del recupero del file specificato, nonché l'ID dell'operazione in background che ha eseguito il recupero. Per informazioni su ciò che è possibile assegnare, vedere i valori restituiti per [SccGet](../extensibility/sccget-function.md) .

### <a name="sccmsgdataonmessage"></a><a name="LinkSccMsgDataOnMessage"></a> SccMsgDataOnMessage

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szMessage;
   BOOL bIsError;
} SccMsgDataOnMessage;
```

 Questa struttura viene inviata con il `SCC_MSG_BACKGROUND_ON_MESSAGE` messaggio. Viene utilizzato per comunicare lo stato corrente di un'operazione in background. Lo stato è espresso come una stringa che deve essere visualizzata dall'IDE e `bIsError` indica la gravità del messaggio (per un `TRUE` messaggio di errore, `FALSE` per un avviso o per un messaggio informativo). Viene anche fornito l'ID dell'operazione in background che invia lo stato.

## <a name="code-example"></a>Esempio di codice
 Ecco un breve esempio di chiamata `LPTEXTOUTPROC` a per inviare il `SCC_MSG_BACKGROUND_ON_MESSAGE` messaggio, mostrando come eseguire il cast della struttura per la chiamata.

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
- [Funzioni di callback implementate dall'IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)
