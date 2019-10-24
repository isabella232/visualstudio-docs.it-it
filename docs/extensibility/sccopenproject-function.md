---
title: Funzione SccOpenProject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccOpenProject
helpviewer_keywords:
- SccOpenProject function
ms.assetid: d609510b-660a-46d7-b93d-2406df20434d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6aa4a715f8d1b87aa831f6a315f07a19e5d4f46
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721046"
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

in Struttura del contesto del plug-in del controllo del codice sorgente.

 hWnd

in Handle per la finestra IDE che il plug-in del controllo del codice sorgente può utilizzare come elemento padre per tutte le finestre di dialogo fornite.

 lpUser

[in, out] Nome dell'utente (non deve superare SCC_USER_SIZE, incluso il carattere di terminazione NULL).

 lpProjName

in Stringa che identifica il nome del progetto.

 lpLocalProjPath

in Percorso della cartella di lavoro per il progetto.

 lpAuxProjPath

[in, out] Stringa ausiliaria facoltativa che identifica il progetto (non deve superare SCC_AUXPATH_SIZE, incluso il carattere di terminazione NULL).

 lpComment

in Consente di aggiungere un commento a un nuovo progetto in fase di creazione.

 lpTextOutProc

in Funzione di callback facoltativa per visualizzare l'output di testo dal plug-in del controllo del codice sorgente.

 dwFlags

in Segnala se è necessario creare un nuovo progetto se il progetto è sconosciuto per il plug-in del controllo del codice sorgente. Il valore può essere una combinazione di `SCC_OP_CREATEIFNEW` e `SCC_OP_SILENTOPEN.`

## <a name="return-value"></a>Valore restituito
 Si prevede che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituisca uno dei valori seguenti:

|Value|Descrizione|
|-----------|-----------------|
|SCC_OK|Operazione riuscita durante l'apertura del progetto.|
|SCC_E_INITIALIZEFAILED|Impossibile inizializzare il progetto.|
|SCC_E_INVALIDUSER|L'utente non è riuscito ad accedere al sistema di controllo del codice sorgente.|
|SCC_E_COULDNOTCREATEPROJECT|Il progetto non esisteva prima della chiamata.  il flag di `SCC_OPT_CREATEIFNEW` è stato impostato, ma non è stato possibile creare il progetto.|
|SCC_E_PROJSYNTAXERR|Sintassi del progetto non valida.|
|SCC_E_UNKNOWNPROJECT|Il progetto è sconosciuto per il plug-in del controllo del codice sorgente e il flag di `SCC_OPT_CREATEIFNEW` non è stato impostato.|
|SCC_E_INVALIDFILEPATH|Percorso file non valido o inutilizzabile.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di conflitto. È consigliabile eseguire un nuovo tentativo.|
|SCC_E_NONSPECFICERROR|Errore non specifico. il sistema di controllo del codice sorgente non è stato inizializzato.|

## <a name="remarks"></a>Note
 L'IDE può passare un nome utente (`lpUser`) o semplicemente passare un puntatore a una stringa vuota. Se è presente un nome utente, il plug-in del controllo del codice sorgente deve utilizzarlo come valore predefinito. Tuttavia, se non è stato passato alcun nome o se l'accesso non è riuscito con il nome specificato, il plug-in deve richiedere all'utente di effettuare l'accesso e restituirà il nome valido in `lpUser` quando riceve un account di accesso valido `.` perché il plug-in potrebbe modificare la stringa del nome utente , l'IDE alloca sempre un buffer di dimensione (`SCC_USER_LEN` + 1 o SCC_USER_SIZE, che include lo spazio per il terminatore null).

> [!NOTE]
> La prima azione che l'IDE potrebbe essere necessaria per eseguire potrebbe essere una chiamata alla funzione `SccOpenProject` o a [SccGetProjPath](../extensibility/sccgetprojpath-function.md). Per questo motivo, entrambi hanno un parametro di `lpUser` identico.

 `lpAuxProjPath` e `lpProjName` vengono letti dal file di soluzione o restituiti da una chiamata alla funzione `SccGetProjPath`. Questi parametri contengono le stringhe associate dal plug-in del controllo del codice sorgente al progetto e sono significative solo per il plug-in. Se tali stringhe non sono presenti nel file di soluzione e all'utente non viene richiesto di eseguire la ricerca (che restituirà una stringa tramite la funzione `SccGetProjPath`), l'IDE passa stringhe vuote sia per `lpAuxProjPath` che per `lpProjName` e prevede che questi valori vengano aggiornati dal plug-in quando la funzione is restituisce.

 `lpTextOutProc` è un puntatore a una funzione di callback fornita dall'IDE al plug-in del controllo del codice sorgente allo scopo di visualizzare l'output dei risultati del comando. Questa funzione di callback è descritta in dettaglio in [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).

> [!NOTE]
> Se il plug-in del controllo del codice sorgente intende sfruttarlo, è necessario impostare il flag `SCC_CAP_TEXTOUT` in [SccInitialize](../extensibility/sccinitialize-function.md). Se il flag non è stato impostato o se l'IDE non supporta questa funzionalità, `lpTextOutProc` verrà `NULL`.

 Il parametro `dwFlags` controlla il risultato nel caso in cui il progetto in fase di apertura non esista. È costituito da due flag, `SCC_OP_CREATEIFNEW` e `SCC_OP_SILENTOPEN`. Se il progetto aperto esiste già, la funzione apre semplicemente il progetto e restituisce `SCC_OK`. Se il progetto non esiste e il flag di `SCC_OP_CREATEIFNEW` è on, il plug-in del controllo del codice sorgente può creare il progetto nel sistema di controllo del codice sorgente, aprirlo e restituire `SCC_OK`. Se il progetto non esiste e il flag `SCC_OP_CREATEIFNEW` è disattivato, il plug-in deve quindi verificare la presenza del flag di `SCC_OP_SILENTOPEN`. Se il flag non è acceso, il plug-in potrebbe richiedere all'utente un nome di progetto. Se il flag è on, il plug-in deve restituire semplicemente `SCC_E_UNKNOWNPROJECT`.

## <a name="calling-order"></a>Ordine di chiamata
 Nel corso normale degli eventi, il [SccInitialize](../extensibility/sccinitialize-function.md) viene chiamato per primo per aprire una sessione del controllo del codice sorgente. Una sessione può essere costituita da una chiamata a `SccOpenProject`, seguita da altre chiamate alle funzioni API del plug-in del controllo del codice sorgente e termina con una chiamata a [SccCloseProject](../extensibility/scccloseproject-function.md). Tali sessioni possono essere ripetute più volte prima della chiamata a [SccUninitialize](../extensibility/sccuninitialize-function.md) .

 Se il plug-in del controllo del codice sorgente imposta il bit `SCC_CAP_REENTRANT` in `SccInitialize`, la sequenza di sessione precedente può essere ripetuta molte volte in parallelo. Diverse strutture di `pvContext` tengono traccia delle diverse sessioni, in cui ogni `pvContext` è associato a un progetto aperto alla volta. In base al parametro `pvContext`, il plug-in è in grado di determinare a quale progetto viene fatto riferimento in una particolare chiamata. Se il bit di funzionalità `SCC_CAP_REENTRANT` non è impostato, i plug-in del controllo del codice sorgente nonreentrant hanno la possibilità di lavorare con più progetti.

> [!NOTE]
> Il bit `SCC_CAP_REENTRANT` è stato introdotto nella versione 1,1 dell'API del plug-in del controllo del codice sorgente. Non è impostato o viene ignorato nella versione 1,0 e si presuppone che tutti i plug-in del controllo del codice sorgente della versione 1,0 siano nonreentrant.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [SccCloseProject](../extensibility/scccloseproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [Limitazioni delle lunghezze di stringa](../extensibility/restrictions-on-string-lengths.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)