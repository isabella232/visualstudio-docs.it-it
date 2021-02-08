---
title: Funzione SccGetProjPath | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetProjPath
helpviewer_keywords:
- SccGetProjPath function
ms.assetid: 1079847e-d45f-4cb8-9d92-1e01ce5d08f6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bad1cae248c0fe3babd920e0773825d9d36b7042
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99844567"
---
# <a name="sccgetprojpath-function"></a>SccGetProjPath (funzione)
Questa funzione richiede all'utente un percorso del progetto, ovvero una stringa significativa solo per il plug-in del controllo del codice sorgente. Viene chiamato quando l'utente è:

- Creazione di un nuovo progetto

- Aggiunta di un progetto esistente al controllo della versione

- Tentativo di ricerca di un progetto di controllo della versione esistente

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

in Struttura del contesto del plug-in del controllo del codice sorgente.

 hWnd

in Handle per la finestra IDE che il plug-in del controllo del codice sorgente può utilizzare come elemento padre per tutte le finestre di dialogo fornite.

 lpUser

[in, out] Nome utente (per non superare SCC_USER_SIZE, incluso il carattere di terminazione NULL)

 lpProjName

[in, out] Nome del progetto IDE, dell'area di lavoro del progetto o del makefile (per non superare SCC_PRJPATH_SIZE, incluso il carattere di terminazione NULL).

 lpLocalPath

[in, out] Percorso di lavoro del progetto. Se `bAllowChangePath` è `TRUE` , il plug-in del controllo del codice sorgente può modificare questa stringa (senza superare _MAX_PATH, incluso il carattere di terminazione null).

 lpAuxProjPath

[in, out] Buffer per il percorso del progetto restituito (per non superare SCC_PRJPATH_SIZE, incluso il carattere di terminazione NULL).

 bAllowChangePath

in Se è `TRUE` , il plug-in del controllo del codice sorgente può richiedere e modificare la `lpLocalPath` stringa.

 pbNew

[in, out] Il valore in arrivo indica se creare un nuovo progetto. Il valore restituito indica la riuscita della creazione di un progetto:

|In arrivo|Interpretazione|
|--------------|--------------------|
|true|L'utente può creare un nuovo progetto.|
|FALSE|L'utente non può creare un nuovo progetto.|

|In uscita|Interpretazione|
|--------------|--------------------|
|true|È stato creato un nuovo progetto.|
|FALSE|È stato selezionato un progetto esistente.|

## <a name="return-value"></a>Valore restituito
 Si prevede che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituisca uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Il progetto è stato creato o recuperato correttamente.|
|SCC_I_OPERATIONCANCELED|L'operazione è stata annullata.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di conflitto.|
|SCC_E_CONNECTIONFAILURE|Si è verificato un problema durante il tentativo di connessione al sistema di controllo del codice sorgente.|
|SCC_E_NONSPECIFICERROR|Si è verificato un errore non specificato.|

## <a name="remarks"></a>Commenti
 Lo scopo di questa funzione è che l'IDE acquisisca i parametri `lpProjName` e `lpAuxProjPath` . Dopo che il plug-in del controllo del codice sorgente ha richiesto all'utente di ottenere tali informazioni, le due stringhe vengono passate all'IDE. L'IDE mantiene queste stringhe nel file della soluzione e le passa a [SccOpenProject](../extensibility/sccopenproject-function.md) ogni volta che l'utente apre il progetto. Queste stringhe consentono al plug-in di tenere traccia delle informazioni associate a un progetto.

 Quando la funzione viene chiamata per la prima volta, `lpAuxProjPath` viene impostata su una stringa vuota. `lProjName` può anche essere vuoto o contenere il nome del progetto IDE, che può essere usato o ignorato dal plug-in del controllo del codice sorgente. Quando la funzione restituisce correttamente, il plug-in restituisce le due stringhe corrispondenti. L'IDE non fa supposizioni su queste stringhe, non le userà e non consentirà all'utente di modificarle. Se l'utente desidera modificare le impostazioni, l'IDE chiamerà `SccGetProjPath` nuovamente, passando gli stessi valori ricevuti dall'ora precedente. In questo modo il plug-in consente il controllo completo su queste due stringhe.

 Per `lpUser` , l'IDE può passare un nome utente o semplicemente passare un puntatore a una stringa vuota. Se è presente un nome utente, il plug-in del controllo del codice sorgente deve utilizzarlo come valore predefinito. Tuttavia, se non è stato passato alcun nome o se l'accesso non è riuscito con il nome specificato, il plug-in deve richiedere all'utente un account di accesso e ripassare il nome `lpUser` quando riceve un account di accesso valido. Poiché il plug-in può modificare questa stringa, l'IDE alloca sempre un buffer di dimensione ( `SCC_USER_LEN` + 1).

> [!NOTE]
> La prima azione eseguita dall'IDE può essere una chiamata alla `SccOpenProject` funzione o alla `SccGetProjPath` funzione. Di conseguenza, entrambi hanno un parametro identico `lpUser` , che consente al plug-in del controllo del codice sorgente di accedere all'utente in qualsiasi momento. Anche se il valore restituito dalla funzione indica un errore, il plug-in deve riempire questa stringa con un nome di account di accesso valido.

 `lpLocalPath` è la directory in cui l'utente mantiene il progetto. Può essere una stringa vuota. Se non è attualmente definita alcuna directory (come nel caso in cui un utente tenti di scaricare un progetto dal sistema di controllo del codice sorgente) e `bAllowChangePath` , se è `TRUE` , il plug-in del controllo del codice sorgente può richiedere l'input dell'utente o usare un altro metodo per inserire la propria stringa in `lpLocalPath` . Se `bAllowChangePath` è `FALSE` , il plug-in non deve modificare la stringa, perché l'utente sta già lavorando nella directory specificata.

 Se l'utente crea un nuovo progetto da inserire nel controllo del codice sorgente, il plug-in del controllo del codice sorgente potrebbe non crearlo effettivamente nel sistema di controllo del codice sorgente al momento della `SccGetProjPath` chiamata a. Al contrario, restituisce la stringa insieme a un valore diverso da zero per `pbNew` , che indica che il progetto verrà creato nel sistema di controllo del codice sorgente.

 Se, ad esempio, un utente nella creazione guidata **nuovo progetto** di Visual Studio aggiunge il progetto al controllo del codice sorgente, Visual Studio chiama questa funzione e il plug-in determina se è corretto creare un nuovo progetto nel sistema di controllo del codice sorgente per contenere il progetto di Visual Studio. Se l'utente fa clic su **Annulla** prima di completare la procedura guidata, il progetto non viene mai creato. Se l'utente fa clic su **OK**, in Visual Studio `SccOpenProject` viene chiamato, passato `SCC_OPT_CREATEIFNEW` e il progetto con controllo del codice sorgente viene creato in quel momento.

## <a name="see-also"></a>Vedi anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
