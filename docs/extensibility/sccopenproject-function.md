---
title: Funzione SccOpenProject . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccOpenProject
helpviewer_keywords:
- SccOpenProject function
ms.assetid: d609510b-660a-46d7-b93d-2406df20434d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fbf566e593bb1ddbc31c70de1570d746a14fbdcf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700575"
---
# <a name="sccopenproject-function"></a>Funzione SccOpenProject
Questa funzione apre un progetto di controllo del codice sorgente esistente o ne crea uno nuovo.

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccOpenProject (
   LPVOID        pvContext,
   HWND          hWnd,
   LPSTR         lpUser,
   LPCSTR        lpProjName,
   LPCSTR        lpLocalProjPath,
   LPSTR         lpAuxProjPath,
   LPCSTR        lpComment,
   LPTEXTOUTPROC lpTextOutProc,
   LONG          dwFlags
);
```

#### <a name="parameters"></a>Parametri
 pvContext

[in] Struttura di contesto del plug-in del controllo del codice sorgente.

 hWnd

[in] Un handle per la finestra dell'IDE che il plug-in del controllo del codice sorgente può utilizzare come elemento padre per tutte le finestre di dialogo che fornisce.

 lpUtente

[in, out] Il nome dell'utente (da non superare SCC_USER_SIZE, incluso il carattere di terminazione NULL).

 LpProjName (nome lpProjName)

[in] Stringa che identifica il nome del progetto.

 lpLocalProjPath (informazioni in base ai criteri della finestra del su windows

[in] Percorso della cartella di lavoro per il progetto.

 LpAuxProjPath (percorso in assoluto)

[in, out] Stringa ausiliaria facoltativa che identifica il progetto (da non superare SCC_AUXPATH_SIZE, incluso il terminatore NULL).

 LpCommento

[in] Commentare un nuovo progetto che viene creato.

 lpTextOutProc (informazioni in base alla protezione dei dati)

[in] Funzione di callback facoltativa per visualizzare l'output di testo dal plug-in del controllo del codice sorgente.

 dwFlags

[in] Segnala se è necessario creare un nuovo progetto se il progetto è sconosciuto al plug-in del controllo del codice sorgente. Il valore può `SCC_OP_CREATEIFNEW` essere una combinazione di e`SCC_OP_SILENTOPEN.`

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei seguenti valori:

|valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Successo nell'apertura del progetto.|
|SCC_E_INITIALIZEFAILED|Impossibile inizializzare il progetto.|
|SCC_E_INVALIDUSER|L'utente non è riuscito ad accedere al sistema di controllo del codice sorgente.|
|SCC_E_COULDNOTCREATEPROJECT|Il progetto non esisteva prima della chiamata;  il `SCC_OPT_CREATEIFNEW` flag è stato impostato, ma non è stato possibile creare il progetto.|
|SCC_E_PROJSYNTAXERR|Sintassi del progetto non valida.|
|SCC_E_UNKNOWNPROJECT|Il progetto è sconosciuto al plug-in `SCC_OPT_CREATEIFNEW` del controllo del codice sorgente e il flag non è stato impostato.|
|SCC_E_INVALIDFILEPATH|Percorso di file non valido o inutilizzabile.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di contesa. È consigliabile eseguire un nuovo tentativo.|
|SCC_E_NONSPECFICERROR|Un errore non specifico; il sistema di controllo del codice sorgente non è stato inizializzato.|

## <a name="remarks"></a>Osservazioni
 L'IDE può passare un`lpUser`nome utente ( ) o può semplicemente passare un puntatore a una stringa vuota. Se è presente un nome utente, il plug-in del controllo del codice sorgente deve utilizzarlo come impostazione predefinita. Tuttavia, se non è stato passato alcun nome o se l'accesso non è riuscito con il `lpUser` nome specificato, il`.` plug-in deve richiedere all'utente di accedere e restituirà il`SCC_USER_LEN`nome valido quando riceve un account di accesso valido Poiché il plug-in può modificare la stringa del nome utente, l'IDE allocherà sempre un buffer di dimensione ( s 1 o SCC_USER_SIZE, che include lo spazio per il terminatore null).

> [!NOTE]
> La prima azione che l'IDE potrebbe essere `SccOpenProject` necessario eseguire può essere una chiamata alla funzione o [SccGetProjPath](../extensibility/sccgetprojpath-function.md). Per questo motivo, entrambi `lpUser` hanno un parametro identico.

 `lpAuxProjPath`e`lpProjName` vengono letti dal file di soluzione o vengono `SccGetProjPath` restituiti da una chiamata alla funzione. Questi parametri contengono le stringhe che il plug-in del controllo del codice sorgente associa al progetto e sono significativi solo per il plug-in. Se tali stringhe non sono presenti nel file di soluzione e all'utente non `SccGetProjPath` è stato richiesto di esplorare (che restituirebbe una stringa tramite la funzione ), l'IDE passa stringhe vuote per entrambi `lpAuxProjPath` e `lpProjName`, e prevede che questi valori vengano aggiornati dal plug-in quando questa funzione restituisce .

 `lpTextOutProc`è un puntatore a una funzione di callback fornita dall'IDE al plug-in del controllo del codice sorgente allo scopo di visualizzare l'output del risultato del comando. Questa funzione di callback è descritta in dettaglio in [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).

> [!NOTE]
> Se il plug-in del controllo del codice sorgente intende `SCC_CAP_TEXTOUT` sfruttare questa soluzione, è necessario che il flag sia stato impostato in [SccInitialize](../extensibility/sccinitialize-function.md). Se tale flag non è stato impostato o se `lpTextOutProc` l'IDE non supporta questa funzionalità, sarà `NULL`.

 Il `dwFlags` parametro controlla il risultato nel caso in cui il progetto aperto non esista attualmente. È costituito da `SCC_OP_CREATEIFNEW` due `SCC_OP_SILENTOPEN`flag di bit e . Se il progetto da aprire esiste già, la `SCC_OK`funzione apre semplicemente il progetto e restituisce . Se il progetto non esiste `SCC_OP_CREATEIFNEW` e se il flag è attivato, il plug-in del controllo del `SCC_OK`codice sorgente può creare il progetto nel sistema del controllo del codice sorgente, aprirlo e restituire . Se il progetto non esiste `SCC_OP_CREATEIFNEW` e se il flag è disattivato, `SCC_OP_SILENTOPEN` il plug-in deve quindi verificare la presenza del flag. Se tale flag non è attivato, il plug-in può richiedere all'utente un nome di progetto. Se tale flag è attivato, il `SCC_E_UNKNOWNPROJECT`plug-in deve semplicemente restituire .

## <a name="calling-order"></a>Ordine di chiamata
 Nel normale corso degli eventi, il [SccInitialize](../extensibility/sccinitialize-function.md) verrebbe chiamato prima per aprire una sessione di controllo del codice sorgente. Una sessione può essere `SccOpenProject`costituita da una chiamata a , seguita da altre chiamate di funzione API del plug-in del controllo del codice sorgente e terminerà con una chiamata a [SccCloseProject](../extensibility/scccloseproject-function.md). Tali sessioni possono essere ripetute più volte prima che venga chiamato [SccUninitialize.](../extensibility/sccuninitialize-function.md)

 Se il plug-in del `SCC_CAP_REENTRANT` controllo `SccInitialize`del codice sorgente imposta il bit in , la sequenza di sessione precedente può essere ripetuta più volte in parallelo. Strutture `pvContext` diverse tengono traccia delle `pvContext` diverse sessioni, in cui ognuna è associata a un progetto aperto alla volta. In base`pvContext` al parametro, il plug-in può determinare a quale progetto viene fatto riferimento in una particolare chiamata. Se il bit `SCC_CAP_REENTRANT` di funzionalità non è impostato, i plug-in del controllo del codice sorgente non rientranti sono limitati nella loro capacità di lavorare con più progetti.

> [!NOTE]
> Il `SCC_CAP_REENTRANT` bit è stato introdotto nella versione 1.1 dell'API del plug-in del controllo del codice sorgente. Non è impostato o viene ignorato nella versione 1.0 e tutti i plug-in del controllo del codice sorgente versione 1.0 vengono considerati non rientranti.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [SccCloseProject](../extensibility/scccloseproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [Limitazioni delle lunghezze di stringa](../extensibility/restrictions-on-string-lengths.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
