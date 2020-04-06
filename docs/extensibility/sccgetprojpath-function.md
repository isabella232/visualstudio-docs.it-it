---
title: SccGetProjPath (funzione) . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetProjPath
helpviewer_keywords:
- SccGetProjPath function
ms.assetid: 1079847e-d45f-4cb8-9d92-1e01ce5d08f6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 281787da3499c081fbbe6f59b7b8175a4dbf24d7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700697"
---
# <a name="sccgetprojpath-function"></a>SccGetProjPath (funzione)
Questa funzione richiede all'utente un percorso di progetto, ovvero una stringa significativa solo per il plug-in del controllo del codice sorgente. Viene chiamato quando l'utente è:Is called when the user is:

- Creazione di un nuovo progetto

- Aggiunta di un progetto esistente al controllo della versione

- Tentativo di trovare un progetto di controllo della versione esistente

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccGetProjPath (
   LPVOID pvContext,
   HWND   hWnd,
   LPSTR  lpUser,
   LPSTR  lpProjName,
   LPSTR  lpLocalPath,
   LPSTR  lpAuxProjPath,
   BOOL   bAllowChangePath,
   LPBOOL pbNew
);
```

### <a name="parameters"></a>Parametri
 pvContext

[in] Struttura di contesto del plug-in del controllo del codice sorgente.

 hWnd

[in] Un handle per la finestra dell'IDE che il plug-in del controllo del codice sorgente può utilizzare come elemento padre per tutte le finestre di dialogo che fornisce.

 lpUtente

[in, out] Il nome utente (non superare SCC_USER_SIZE, incluso il carattere di terminazione NULL)

 LpProjName (nome lpProjName)

[in, out] Nome del progetto IDE, dell'area di lavoro del progetto o del makefile (non superare SCC_PRJPATH_SIZE, incluso il carattere di terminazione NULL).

 Percorso locale lpLocalPath

[in, out] Il percorso di lavoro del progetto. Se `bAllowChangePath` `TRUE`è , il plug-in del controllo del codice sorgente può modificare questa stringa (non superare _MAX_PATH, incluso il carattere di terminazione null).

 LpAuxProjPath (percorso in assoluto)

[in, out] Un buffer per il percorso di progetto restituito (non superare SCC_PRJPATH_SIZE, incluso il terminatore NULL).

 bAllowChangePath (informazioni in base alle modifiche

[in] In caso `TRUE`contrario, il plug-in del `lpLocalPath` controllo del codice sorgente può richiedere e modificare la stringa.

 pbNew (pbNew)

[in, out] Il valore in arrivo indica se creare un nuovo progetto. Il valore restituito indica la riuscita della creazione di un progetto:Value returned indicates success of creating a project:

|In ingresso|Interpretazione|
|--------------|--------------------|
|TRUE|L'utente può creare un nuovo progetto.|
|FALSE|L'utente non può creare un nuovo progetto.|

|In uscita|Interpretazione|
|--------------|--------------------|
|TRUE|È stato creato un nuovo progetto.|
|FALSE|È stato selezionato un progetto esistente.|

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei seguenti valori:

|valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Il progetto è stato creato o recuperato correttamente.|
|SCC_I_OPERATIONCANCELED|L'operazione è stata annullata.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di contesa.|
|SCC_E_CONNECTIONFAILURE|Si è verificato un problema durante il tentativo di connessione al sistema di controllo del codice sorgente.|
|SCC_E_NONSPECIFICERROR|Si è verificato un errore non specificato.|

## <a name="remarks"></a>Osservazioni
 Lo scopo di questa funzione è che `lpProjName` l'IDE acquisisca i parametri e `lpAuxProjPath`. Dopo che il plug-in controllo del codice sorgente richiede all'utente per queste informazioni, passa queste due stringhe all'IDE. L'IDE mantiene queste stringhe nel file di soluzione e le passa a [SccOpenProject](../extensibility/sccopenproject-function.md) ogni volta che l'utente apre il progetto. Queste stringhe consentono al plug-in di tenere traccia delle informazioni associate a un progetto.

 Quando la funzione viene `lpAuxProjPath` chiamata per la prima volta, viene impostata su una stringa vuota. `lProjName`può anche essere vuoto o può contenere il nome del progetto IDE, che il plug-in del controllo del codice sorgente può utilizzare o ignorare. Quando la funzione viene restituita correttamente, il plug-in restituisce le due stringhe corrispondenti. L'IDE non fa supposizioni su queste stringhe, non le utilizzerà e non consentirà all'utente di modificarle. Se l'utente desidera modificare le impostazioni, `SccGetProjPath` l'IDE chiamerà nuovamente, passando gli stessi valori che aveva ricevuto l'ora precedente. In questo modo il plug-in il controllo completo su queste due stringhe.

 Per `lpUser`, l'IDE può passare un nome utente o può semplicemente passare un puntatore a una stringa vuota. Se è presente un nome utente, il plug-in del controllo del codice sorgente deve utilizzarlo come impostazione predefinita. Tuttavia, se non è stato passato alcun nome o se l'account di accesso non è `lpUser` riuscito con il nome specificato, il plug-in deve richiedere all'utente un account di accesso e restituire nuovamente il nome quando riceve un account di accesso valido. Poiché il plug-in può modificare questa stringa, l'IDE allocherà sempre un buffer di dimensioni (n.`SCC_USER_LEN`1).

> [!NOTE]
> La prima azione eseguita dall'IDE può `SccOpenProject` essere `SccGetProjPath` una chiamata alla funzione o alla funzione. Di conseguenza, entrambi `lpUser` hanno un parametro identico, che consente al plug-in del controllo del codice sorgente di accedere all'utente in qualsiasi momento. Anche se il ritorno dalla funzione indica un errore, il plug-in deve riempire questa stringa con un nome di accesso valido.

 `lpLocalPath`è la directory in cui l'utente conserva il progetto. Può essere una stringa vuota. Se non è attualmente definita alcuna directory (come nel caso in cui un utente `bAllowChangePath` `TRUE`tenti di scaricare un progetto dal sistema di controllo del codice sorgente) e, se lo è, il plug-in del controllo del codice sorgente può richiedere all'utente l'input o utilizzare un altro metodo per inserire la propria stringa in `lpLocalPath`. Se `bAllowChangePath` `FALSE`è , il plug-in non deve modificare la stringa, perché l'utente sta già lavorando nella directory specificata.

 Se l'utente crea un nuovo progetto da inserire nel controllo del codice sorgente, il plug-in del controllo del codice sorgente potrebbe non crearlo effettivamente nel sistema di controllo del codice sorgente al momento `SccGetProjPath` viene chiamato. Passa invece nuovamente la stringa con un `pbNew`valore diverso da zero per , che indica che il progetto verrà creato nel sistema di controllo del codice sorgente.

 Ad esempio, se un utente nella creazione guidata **nuovo progetto** in Visual Studio aggiunge il proprio progetto al controllo del codice sorgente, Visual Studio chiama questa funzione e il plug-in determina se è possibile creare un nuovo progetto nel sistema di controllo del codice sorgente per contenere il progetto di Visual Studio. Se l'utente fa clic su **Annulla** prima di completare la procedura guidata, il progetto non viene mai creato. Se l'utente **OK**fa clic `SccOpenProject`su OK `SCC_OPT_CREATEIFNEW`, Visual Studio chiama , passando e il progetto dal punto di vista del codice sorgente viene creato in quel momento.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
