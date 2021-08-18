---
description: Questa funzione richiede all'utente un percorso di progetto, ovvero una stringa significativa solo per il plug-in del controllo del codice sorgente.
title: Funzione SccGetProjPath | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGetProjPath
helpviewer_keywords:
- SccGetProjPath function
ms.assetid: 1079847e-d45f-4cb8-9d92-1e01ce5d08f6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 196bb80d5e50445fec43f3c9ae50adbdb6bfd53e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122062719"
---
# <a name="sccgetprojpath-function"></a>Funzione SccGetProjPath
Questa funzione richiede all'utente un percorso di progetto, ovvero una stringa significativa solo per il plug-in del controllo del codice sorgente. Viene chiamato quando l'utente è:

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

[in] Struttura del contesto del plug-in del controllo del codice sorgente.

 hWnd

[in] Handle per la finestra IDE che il plug-in del controllo del codice sorgente può usare come elemento padre per qualsiasi finestra di dialogo fornita.

 lpUser

[in, out] Nome utente (da non superare SCC_USER_SIZE, incluso il carattere di terminazione NULL)

 lpProjName

[in, out] Nome del progetto IDE, dell'area di lavoro del progetto o del makefile (da non superare SCC_PRJPATH_SIZE, incluso il carattere di terminazione NULL).

 lpLocalPath

[in, out] Percorso di lavoro del progetto. Se è , il plug-in del controllo del codice sorgente può modificare questa stringa (per non superare _MAX_PATH, incluso il `bAllowChangePath` `TRUE` carattere di terminazione Null).

 lpAuxProjPath

[in, out] Buffer per il percorso del progetto restituito (da non superare SCC_PRJPATH_SIZE, incluso il carattere di terminazione NULL).

 bAllowChangePath

[in] Se è `TRUE` , il plug-in del controllo del codice sorgente può richiedere e modificare la `lpLocalPath` stringa.

 pbNew

[in, out] Il valore in arrivo indica se creare un nuovo progetto. Il valore restituito indica l'esito positivo della creazione di un progetto:

|In arrivo|Interpretazione|
|--------------|--------------------|
|true|L'utente può creare un nuovo progetto.|
|FALSE|L'utente non può creare un nuovo progetto.|

|In uscita|Interpretazione|
|--------------|--------------------|
|true|È stato creato un nuovo progetto.|
|FALSE|È stato selezionato un progetto esistente.|

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Il progetto è stato creato o recuperato correttamente.|
|SCC_I_OPERATIONCANCELED|L'operazione è stata annullata.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di problemi di connessione.|
|SCC_E_CONNECTIONFAILURE|Si è verificato un problema durante il tentativo di connessione al sistema di controllo del codice sorgente.|
|SCC_E_NONSPECIFICERROR|Si è verificato un errore non specificato.|

## <a name="remarks"></a>Commenti
 Lo scopo di questa funzione è fare in modo che l'IDE acquisisca i parametri `lpProjName` e `lpAuxProjPath` . Quando il plug-in del controllo del codice sorgente richiede all'utente queste informazioni, passa di nuovo queste due stringhe all'IDE. L'IDE rende persistenti queste stringhe nel file di soluzione e le passa a [SccOpenProject](../extensibility/sccopenproject-function.md) ogni volta che l'utente apre il progetto. Queste stringhe consentono al plug-in di tenere traccia delle informazioni associate a un progetto.

 Quando la funzione viene chiamata per la prima volta, `lpAuxProjPath` viene impostato su una stringa vuota. `lProjName` può anche essere vuoto o contenere il nome del progetto IDE, che il plug-in del controllo del codice sorgente può usare o ignorare. Quando la funzione viene restituita correttamente, il plug-in restituisce le due stringhe corrispondenti. L'IDE non fa supposizioni su queste stringhe, non le userà e non consentirà all'utente di modificarle. Se l'utente vuole modificare le impostazioni, l'IDE chiamerà nuovamente , passando gli stessi valori ricevuti `SccGetProjPath` l'ora precedente. In questo modo il plug-in ha il controllo completo su queste due stringhe.

 Per `lpUser` , l'IDE può passare un nome utente o semplicemente passare un puntatore a una stringa vuota. Se è presente un nome utente, il plug-in del controllo del codice sorgente deve usarlo come impostazione predefinita. Tuttavia, se non è stato passato alcun nome o se l'accesso non è riuscito con il nome specificato, il plug-in deve richiedere all'utente un account di accesso e passare nuovamente il nome quando riceve un account di accesso `lpUser` valido. Poiché il plug-in può modificare questa stringa, l'IDE alloca sempre un buffer di dimensioni ( `SCC_USER_LEN` +1).

> [!NOTE]
> La prima azione eseguita dall'IDE può essere una chiamata alla `SccOpenProject` funzione o alla funzione `SccGetProjPath` . Di conseguenza, entrambi hanno un parametro identico, che consente al plug-in del controllo del codice sorgente di `lpUser` accedere all'utente in entrambi i casi. Anche se il valore restituito dalla funzione indica un errore, il plug-in deve compilare questa stringa con un nome di accesso valido.

 `lpLocalPath` è la directory in cui l'utente mantiene il progetto. Può essere una stringa vuota. Se non è attualmente definita alcuna directory (come nel caso di un utente che tenta di scaricare un progetto dal sistema di controllo del codice sorgente) e se è , il `bAllowChangePath` plug-in del controllo del codice sorgente può richiedere input all'utente o usare un altro metodo per inserire la propria stringa `TRUE` in `lpLocalPath` . Se `bAllowChangePath` è , il `FALSE` plug-in non deve modificare la stringa, perché l'utente sta già lavorando nella directory specificata.

 Se l'utente crea un nuovo progetto da inserire nel controllo del codice sorgente, il plug-in del controllo del codice sorgente potrebbe non crearlo effettivamente nel sistema di controllo del codice sorgente al momento della `SccGetProjPath` chiamata a . Passa invece la stringa insieme a un valore diverso da zero per , a indicare che il progetto verrà creato nel sistema di controllo `pbNew` del codice sorgente.

 Ad esempio, se un utente nella procedura guidata Nuovo **Project** in Visual Studio aggiunge il proprio progetto al controllo del codice sorgente, Visual Studio chiama questa funzione e il plug-in determina se è possibile creare un nuovo progetto nel sistema di controllo del codice sorgente per contenere il progetto Visual Studio. Se l'utente fa **clic su Annulla** prima di completare la procedura guidata, il progetto non viene mai creato. Se l'utente fa clic **su OK,** Visual Studio chiama , passando , e il progetto controllato dal codice sorgente `SccOpenProject` viene creato in quel `SCC_OPT_CREATEIFNEW` momento.

## <a name="see-also"></a>Vedi anche
- [Funzioni API plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
