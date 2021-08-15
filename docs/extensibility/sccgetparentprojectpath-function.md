---
description: Questa funzione determina il percorso del progetto padre di un progetto specificato.
title: Funzione SccGetParentProjectPath | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGetParentProjectPath
helpviewer_keywords:
- SccGetParentProjectPath function
ms.assetid: 62a71579-36b3-48b9-a1c8-04ab100efa08
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 20479eec7cce78996c70a98045747dd5132112fe3f81ec72ffefca3e118e9aa9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121321035"
---
# <a name="sccgetparentprojectpath-function"></a>Funzione SccGetParentProjectPath
Questa funzione determina il percorso del progetto padre di un progetto specificato. Questa funzione viene chiamata quando l'utente aggiunge un progetto Visual Studio al controllo del codice sorgente.

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccGetParentProjectPath(
   LPVOID pContext,
   HWND   hWnd,
   LPSTR  lpUser,
   LPCSTR lpProjPath,
   LPSTR  lpAuxProjPath,
   LPSTR  lpParentProjPath
);
```

### <a name="parameters"></a>Parametri
 pContext

[in] Puntatore al contesto del plug-in del controllo del codice sorgente.

 hWnd

[in] Handle per la finestra IDE che il plug-in del controllo del codice sorgente può usare come elemento padre per qualsiasi finestra di dialogo fornita.

 lpUser

[in, out] Nome utente (fino a SCC_USER_SIZE, incluso il carattere di terminazione NULL).

 lpProjPath

[in] Stringa che identifica il percorso del progetto (fino SCC_PRJPATH_SIZE, incluso il carattere di terminazione NULL).

 lpAuxProjPath

[in, out] Stringa ausiliaria che identifica il progetto (fino a SCC_PRJPATH_SIZE, incluso il terminatore NULL).

 lpParentProjPath

[in, out] Stringa di output che identifica il percorso del progetto padre (fino SCC_PRJPATH_SIZE, incluso il carattere di terminazione NULL).

## <a name="return-value"></a>Valore restituito
 È previsto che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituirà uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Il percorso del progetto padre è stato ottenuto correttamente.|
|SCC_E_INITIALIZEFAILED|Project impossibile inizializzare.|
|SCC_E_INVALIDUSER|L'utente non è stato in grado di accedere al plug-in del controllo del codice sorgente.|
|SCC_E_UNKNOWNPROJECT|Project è sconosciuto al plug-in del controllo del codice sorgente.|
|SCC_E_INVALIDFILEPATH|Percorso di file non valido o inutilizzabile.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di problemi di connessione. È consigliabile eseguire un nuovo tentativo.|
|SCC_E_PROJSYNTAXERR|Sintassi del progetto non valida.|
|SCC_E_CONNECTIONFAILURE|Problema di connessione dell'archivio.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Errore non specifico.|

## <a name="remarks"></a>Commenti
 Questa funzione restituisce un codice di esito positivo o negativo e, in caso di esito positivo, riempie la variabile con il percorso completo `lpParentProjPath` del progetto specificato.

 Questa funzione restituisce il percorso del progetto padre di un progetto esistente. Per il progetto radice, la funzione restituisce il percorso del progetto passato, ovvero lo stesso percorso del progetto radice. Si noti che un percorso di progetto è una stringa significativa solo per il plug-in del controllo del codice sorgente.

 L'IDE è pronto ad accettare anche le modifiche `lpUser` `lpAuxProjPath` ai parametri e . L'IDE rende persistenti queste stringhe e le passa a [SccOpenProject](../extensibility/sccopenproject-function.md) quando l'utente apre questo progetto in futuro. Queste stringhe, pertanto, consentono al plug-in del controllo del codice sorgente di tenere traccia delle informazioni da associare a un progetto.

 Questa funzione è simile a [SccGetProjPath](../extensibility/sccgetprojpath-function.md), ad eccezione del fatto che non richiede all'utente di selezionare un progetto. Non crea mai un nuovo progetto, ma funziona solo con un progetto esistente.

 Quando `SccGetParentProjectPath` viene chiamato , e non sarà vuoto e `lpProjPath` `lpAuxProjPath` corrisponderà a un progetto valido. Queste stringhe vengono in genere ricevute dall'IDE da una chiamata precedente alla `SccGetProjPath` funzione .

 `lpUser`L'argomento è il nome utente. L'IDE passerà lo stesso nome utente ricevuto in precedenza dalla funzione e il plug-in del controllo del codice sorgente deve usare `SccGetProjPath` il nome come predefinito. Se l'utente ha già una connessione aperta con il plug-in, il plug-in deve tentare di eliminare eventuali richieste per assicurarsi che la funzione funzioni in modo invisibile all'utente. Tuttavia, se l'accesso ha esito negativo, il plug-in deve richiedere all'utente un account di accesso e, quando riceve un account di accesso valido, passare nuovamente il nome in `lpUser` . Poiché il plug-in può modificare questa stringa, l'IDE alloca sempre un buffer di dimensioni ( `SCC_USER_LEN` +1). Se la stringa viene modificata, la nuova stringa deve essere un nome di accesso valido (almeno valido come la stringa precedente).

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Note tecniche per SccCreateSubProject e SccGetParentProjectPath
 L'aggiunta di soluzioni e progetti al controllo del codice sorgente è stata semplificata in Visual Studio per ridurre al minimo il numero di volte in cui a un utente viene richiesto di selezionare i percorsi nel sistema di controllo del codice sorgente. Queste modifiche vengono attivate Visual Studio se un plug-in del controllo del codice sorgente supporta entrambe le nuove funzioni, [SccCreateSubProject](../extensibility/scccreatesubproject-function.md) e la `SccGetParentProjectPath` funzione . Tuttavia, la voce del Registro di sistema seguente può essere usata per disabilitare queste modifiche e ripristinare il comportamento precedente Visual Studio (API plug-in controllo del codice sorgente versione 1.1):

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl"=dword:00000001**

 Se questa voce del Registro di sistema non esiste o è impostata su dword:00000000, Visual Studio di usare le nuove funzioni `SccCreateSubProject` e `SccGetParentProjectPath` .

 Se la voce del Registro di sistema è impostata su dword:00000001, Visual Studio non tenta di usare queste nuove funzioni e le operazioni di aggiunta al controllo del codice sorgente funzionano come nelle versioni precedenti di Visual Studio.

## <a name="see-also"></a>Vedi anche
- [Funzioni API plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
