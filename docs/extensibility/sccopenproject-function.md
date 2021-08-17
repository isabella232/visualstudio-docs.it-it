---
description: Questa funzione apre un progetto di controllo del codice sorgente esistente o ne crea uno nuovo.
title: Funzione SccOpenProject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccOpenProject
helpviewer_keywords:
- SccOpenProject function
ms.assetid: d609510b-660a-46d7-b93d-2406df20434d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 8fcd8ba5b7c3fc1759432d0b33d7b49aa3a257cd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122110046"
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

[in] Struttura del contesto del plug-in del controllo del codice sorgente.

 hWnd

[in] Handle per la finestra IDE che il plug-in del controllo del codice sorgente può usare come elemento padre per qualsiasi finestra di dialogo fornita.

 lpUser

[in, out] Nome dell'utente (da non superare SCC_USER_SIZE, incluso il carattere di terminazione NULL).

 lpProjName

[in] Stringa che identifica il nome del progetto.

 lpLocalProjPath

[in] Percorso della cartella di lavoro per il progetto.

 lpAuxProjPath

[in, out] Stringa ausiliaria facoltativa che identifica il progetto (da non superare SCC_AUXPATH_SIZE, incluso il terminatore NULL).

 lpComment

[in] Aggiungere un commento a un nuovo progetto che viene creato.

 lpTextOutProc

[in] Funzione di callback facoltativa per visualizzare l'output di testo dal plug-in del controllo del codice sorgente.

 dwFlags

[in] Segnala se è necessario creare un nuovo progetto se il progetto è sconosciuto al plug-in del controllo del codice sorgente. Il valore può essere una combinazione `SCC_OP_CREATEIFNEW` di e `SCC_OP_SILENTOPEN.`

## <a name="return-value"></a>Valore restituito
 È previsto che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituirà uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Esito positivo nell'apertura del progetto.|
|SCC_E_INITIALIZEFAILED|Project impossibile inizializzare.|
|SCC_E_INVALIDUSER|L'utente non è stato in grado di accedere al sistema di controllo del codice sorgente.|
|SCC_E_COULDNOTCREATEPROJECT|Il progetto non esisteva prima della chiamata.  Il `SCC_OPT_CREATEIFNEW` flag è stato impostato, ma non è stato possibile creare il progetto.|
|SCC_E_PROJSYNTAXERR|Sintassi del progetto non valida.|
|SCC_E_UNKNOWNPROJECT|Il progetto è sconosciuto al plug-in del controllo del codice sorgente e il `SCC_OPT_CREATEIFNEW` flag non è stato impostato.|
|SCC_E_INVALIDFILEPATH|Percorso di file non valido o inutilizzabile.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di problemi di connessione. È consigliabile eseguire un nuovo tentativo.|
|SCC_E_NONSPECFICERROR|Errore non specifico. Il sistema di controllo del codice sorgente non è stato inizializzato.|

## <a name="remarks"></a>Commenti
 L'IDE può passare un nome utente ( ) o semplicemente passare `lpUser` un puntatore a una stringa vuota. Se è presente un nome utente, il plug-in del controllo del codice sorgente deve usarlo come impostazione predefinita. Tuttavia, se non è stato passato alcun nome o se l'accesso ha avuto esito negativo con il nome specificato, il plug-in deve richiedere all'utente di accedere e restituirà il nome valido in quando riceve un account di accesso valido Poiché il plug-in può modificare la stringa del nome utente, l'IDE alloca sempre un buffer di dimensioni ( +1 o SCC_USER_SIZE, che include spazio per il `lpUser` `.` `SCC_USER_LEN` terminatore Null).

> [!NOTE]
> La prima azione che l'IDE può essere necessario eseguire può essere una chiamata alla funzione `SccOpenProject` o [SccGetProjPath.](../extensibility/sccgetprojpath-function.md) Per questo motivo, entrambi hanno un parametro `lpUser` identico.

 `lpAuxProjPath` e `lpProjName` vengono letti dal file di soluzione oppure vengono restituiti da una chiamata alla funzione `SccGetProjPath` . Questi parametri contengono le stringhe associate dal plug-in del controllo del codice sorgente al progetto e sono significativi solo per il plug-in. Se non sono presenti stringhe di questo tipo nel file di soluzione e all'utente non è stato richiesto di esplorare (che restituirebbe una stringa tramite la funzione), l'IDE passa stringhe vuote per e e prevede che questi valori siano aggiornati dal plug-in quando questa funzione `SccGetProjPath` `lpAuxProjPath` viene `lpProjName` restituita.

 `lpTextOutProc` è un puntatore a una funzione di callback fornita dall'IDE al plug-in del controllo del codice sorgente allo scopo di visualizzare l'output del risultato del comando. Questa funzione di callback è descritta in dettaglio in [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).

> [!NOTE]
> Se il plug-in del controllo del codice sorgente intende sfruttare questo vantaggio, deve avere impostato il `SCC_CAP_TEXTOUT` flag in [SccInitialize](../extensibility/sccinitialize-function.md). Se tale flag non è stato impostato o se l'IDE non supporta questa funzionalità, `lpTextOutProc` sarà `NULL` .

 Il `dwFlags` parametro controlla il risultato nel caso in cui il progetto aperto non esista attualmente. È costituito da due flag di bit e `SCC_OP_CREATEIFNEW` `SCC_OP_SILENTOPEN` . Se il progetto aperto esiste già, la funzione apre semplicemente il progetto e restituisce `SCC_OK` . Se il progetto non esiste e se il flag è impostato su , il plug-in di controllo del codice sorgente può creare il progetto nel sistema di controllo del codice sorgente, aprirlo `SCC_OP_CREATEIFNEW` e restituire `SCC_OK` . Se il progetto non esiste e se il flag è disattivato, il plug-in deve cercare `SCC_OP_CREATEIFNEW` il `SCC_OP_SILENTOPEN` flag. Se il flag non è impostato, il plug-in potrebbe richiedere all'utente un nome di progetto. Se il flag è impostato su , il plug-in deve semplicemente restituire `SCC_E_UNKNOWNPROJECT` .

## <a name="calling-order"></a>Ordine di chiamata
 Nel corso normale degli eventi, [SccInitialize](../extensibility/sccinitialize-function.md) viene chiamato per primo per aprire una sessione di controllo del codice sorgente. Una sessione può essere costituita da una chiamata a , seguita da altre chiamate di funzione api plug-in del controllo del codice sorgente e termina con una chiamata `SccOpenProject` a [SccCloseProject](../extensibility/scccloseproject-function.md). Tali sessioni possono essere ripetute più volte prima che [venga chiamato SccUninitialize.](../extensibility/sccuninitialize-function.md)

 Se il plug-in del controllo del codice sorgente imposta il bit in , la sequenza di sessione precedente può essere ripetuta `SCC_CAP_REENTRANT` `SccInitialize` più volte in parallelo. Strutture `pvContext` diverse tiene traccia delle diverse sessioni, in cui ognuna è `pvContext` associata a un progetto aperto alla volta. In base al `pvContext` parametro , il plug-in può determinare a quale progetto viene fatto riferimento in qualsiasi chiamata specifica. Se il bit di funzionalità non è impostato, i plug-in di controllo del codice sorgente non a tolleranza sono limitati nella possibilità di `SCC_CAP_REENTRANT` lavorare con più progetti.

> [!NOTE]
> Il `SCC_CAP_REENTRANT` bit è stato introdotto nella versione 1.1 dell'API plug-in del controllo del codice sorgente. Non è impostato o viene ignorato nella versione 1.0 e si presuppone che tutti i plug-in del controllo del codice sorgente della versione 1.0 non siano rientranti.

## <a name="see-also"></a>Vedi anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [SccCloseProject](../extensibility/scccloseproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [Limitazioni delle lunghezze di stringa](../extensibility/restrictions-on-string-lengths.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
