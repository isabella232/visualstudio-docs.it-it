---
title: SccGetParentProjectPath (funzione) . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetParentProjectPath
helpviewer_keywords:
- SccGetParentProjectPath function
ms.assetid: 62a71579-36b3-48b9-a1c8-04ab100efa08
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0f258558207f86ff76746d18aa432fe4c5850290
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700708"
---
# <a name="sccgetparentprojectpath-function"></a>SccGetParentProjectPath (funzione)SccGetParentProjectPath function
Questa funzione determina il percorso del progetto padre di un progetto specificato. Questa funzione viene chiamata quando l'utente aggiunge un progetto di Visual Studio al controllo del codice sorgente.

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

[in] Puntatore di contesto del plug-in del controllo del codice sorgente.

 hWnd

[in] Un handle per la finestra dell'IDE che il plug-in del controllo del codice sorgente può utilizzare come elemento padre per tutte le finestre di dialogo che fornisce.

 lpUtente

[in, out] Il nome utente (fino a SCC_USER_SIZE, incluso il carattere di terminazione NULL).

 lpProjPath (oggetto <a1>tall<<

[in] Stringa che identifica il percorso del progetto (fino a SCC_PRJPATH_SIZE, incluso il carattere di terminazione NULL).

 LpAuxProjPath (percorso in assoluto)

[in, out] Stringa ausiliaria che identifica il progetto (fino a SCC_PRJPATH_SIZE, incluso il terminatore NULL).

 LpParentProjPath (percorso in cui è stato possibile utilizzare il percorso in stato

[in, out] Stringa di output che identifica il percorso del progetto padre (fino a SCC_PRJPATH_SIZE, incluso il terminatore NULL).

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei seguenti valori:

|valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Il percorso del progetto padre è stato ottenuto correttamente.|
|SCC_E_INITIALIZEFAILED|Impossibile inizializzare il progetto.|
|SCC_E_INVALIDUSER|L'utente non è riuscito ad accedere al plug-in del controllo del codice sorgente.|
|SCC_E_UNKNOWNPROJECT|Il progetto è sconosciuto al plug-in del controllo del codice sorgente.|
|SCC_E_INVALIDFILEPATH|Percorso di file non valido o inutilizzabile.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di contesa. È consigliabile eseguire un nuovo tentativo.|
|SCC_E_PROJSYNTAXERR|Sintassi del progetto non valida.|
|SCC_E_CONNECTIONFAILURE|Problemi di connessione all'archivio.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Errore non specifico.|

## <a name="remarks"></a>Osservazioni
 Questa funzione restituisce un codice di esito positivo `lpParentProjPath` o negativo e, in caso di esito positivo, riempie la variabile con il percorso completo del progetto del progetto specificato.

 Questa funzione restituisce il percorso del progetto padre di un progetto esistente. Per il progetto radice, la funzione restituisce il percorso del progetto passato, ovvero lo stesso percorso del progetto radice. Si noti che un percorso di progetto è una stringa significativa solo per il plug-in del controllo del codice sorgente.

 L'IDE è pronto ad `lpUser` `lpAuxProjPath` accettare le modifiche ai parametri e. L'IDE mancherà di mantenere queste stringhe e passarli a [SccOpenProject](../extensibility/sccopenproject-function.md) quando l'utente apre il progetto in futuro. Queste stringhe, pertanto, forniscono un modo per il plug-in del controllo del codice sorgente per tenere traccia delle informazioni che è necessario associare a un progetto.

 Questa funzione è simile a [SccGetProjPath](../extensibility/sccgetprojpath-function.md), con la differenza che non richiede all'utente di selezionare un progetto. Inoltre, non crea mai un nuovo progetto, ma funziona solo con un progetto esistente.

 Quando `SccGetParentProjectPath` viene `lpProjPath` chiamato, e `lpAuxProjPath` non sarà vuoto e corrisponderà a un progetto valido. Queste stringhe vengono in genere ricevute dall'IDE da una chiamata precedente alla `SccGetProjPath` funzione.

 L'argomento `lpUser` è il nome utente. L'IDE passerà lo stesso nome utente che `SccGetProjPath` aveva ricevuto in precedenza dalla funzione e il plug-in controllo del codice sorgente deve utilizzare il nome come valore predefinito. Se l'utente ha già una connessione aperta con il plug-in, il plug-in dovrebbe tentare di eliminare eventuali richieste per assicurarsi che la funzione funzioni in modo invisibile all'utente. Tuttavia, se l'accesso non riesce, il plug-in deve richiedere all'utente un account `lpUser`di accesso e, quando riceve un account di accesso valido, passare nuovamente il nome in . Poiché il plug-in può modificare questa stringa, l'IDE allocherà sempre un buffer di dimensioni (n.`SCC_USER_LEN`1). Se la stringa viene modificata, la nuova stringa deve essere un nome di accesso valido (almeno valido come la stringa precedente).

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Note tecniche per SccCreateSubProject e SccGetParentProjectPath
 L'aggiunta di soluzioni e progetti al controllo del codice sorgente è stata semplificata in Visual Studio per ridurre al minimo il numero di volte in cui un utente viene richiesto di selezionare percorsi nel sistema di controllo del codice sorgente. Queste modifiche vengono attivate da Visual Studio se un plug-in del controllo del codice `SccGetParentProjectPath` sorgente supporta entrambe le nuove funzioni, [SccCreateSubProject](../extensibility/scccreatesubproject-function.md) e la funzione. Tuttavia, la seguente voce del Registro di sistema può essere utilizzata per disattivare queste modifiche e ripristinare il comportamento precedente di Visual Studio (Api del plug-in del controllo del codice sorgente versione 1.1):

 **[HKEY_CURRENT_USER Software Microsoft VisualStudio 8.0/SourceControl] "DoNotCreateSolutionRootFolderInSourceControl" : dword:00000001**

 Se questa voce del Registro di sistema non esiste o è impostata su dword:00000000, Visual Studio tenta di utilizzare le nuove funzioni `SccCreateSubProject`e`SccGetParentProjectPath`.

 Se la voce del Registro di sistema è impostata su dword:00000001, Visual Studio non tenta di utilizzare queste nuove funzioni e le operazioni di aggiunta al controllo del codice sorgente funzionano come nelle versioni precedenti di Visual Studio.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
