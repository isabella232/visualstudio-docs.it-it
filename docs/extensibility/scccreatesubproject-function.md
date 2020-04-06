---
title: SccCreateSubProject (funzione) . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCreateSubProject
helpviewer_keywords:
- SccCreateSubProject function
ms.assetid: 08154aed-ae5c-463c-8694-745d0e332965
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 74354e05b16830f599dd706fbe48aadd75b11a18
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701043"
---
# <a name="scccreatesubproject-function"></a>SccCreateSubProject (funzione)SccCreateSubProject function
Questa funzione crea un sottoprogetto con il nome specificato `lpParentProjPath` in un progetto padre esistente specificato dall'argomento.

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccCreateSubProject(
   LPVOID pContext,
   HWND   hWnd,
   LPSTR  lpUser,
   LPCSTR lpParentProjPath,
   LPCSTR lpSubProjName,
   LPSTR  lpAuxProjPath,
   LPSTR  lpSubProjPath
);
```

### <a name="parameters"></a>Parametri
 pContext

[in] Puntatore di contesto del plug-in del controllo del codice sorgente.

 hWnd

[in] Un handle per la finestra dell'IDE che il plug-in del controllo del codice sorgente può utilizzare come elemento padre per tutte le finestre di dialogo che fornisce.

 lpUtente

[in, out] Il nome utente (fino a SCC_USER_SIZE, incluso il carattere di terminazione NULL).

 LpParentProjPath (percorso in cui è stato possibile utilizzare il percorso in stato

[in] Stringa che identifica il percorso del progetto padre (fino a SCC_PRJPATH_SIZE, incluso il terminatore NULL).

 LpSubProjName (nome di lavoro)

[in] Il nome del sottoprogetto suggerito (fino a SCC_PRJPATH_SIZE, incluso il terminatore NULL).

 LpAuxProjPath (percorso in assoluto)

[in, out] Stringa ausiliaria che identifica il progetto (fino a SCC_PRJPATH_SIZE, incluso il terminatore NULL).

 lpSubProjPath (percorso lpSubProjPath)

[in, out] Stringa di output che identifica il percorso per il sottoprogetto (fino a SCC_PRJPATH_SIZE, incluso il terminatore NULL).

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei seguenti valori:

|valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Il sottoprogetto è stato creato correttamente.|
|SCC_E_INITIALIZEFAILED|Impossibile inizializzare il progetto padre.|
|SCC_E_INVALIDUSER|L'utente non è riuscito ad accedere al sistema di controllo del codice sorgente.|
|SCC_E_COULDNOTCREATEPROJECT|Impossibile creare un sottoprogetto.|
|SCC_E_PROJSYNTAXERR|Sintassi del progetto non valida.|
|SCC_E_UNKNOWNPROJECT|Il progetto padre è sconosciuto al plug-in del controllo del codice sorgente.|
|SCC_E_INVALIDFILEPATH|Percorso di file non valido o inutilizzabile.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di contesa. È consigliabile eseguire un nuovo tentativo.|
|SCC_E_CONNECTIONFAILURE|Si è verificato un problema di connessione del plug-in del controllo del codice sorgente.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Errore non specifico.|

## <a name="remarks"></a>Osservazioni
 Se esiste già un sottoprogetto con il nome, la funzione può modificare il nome\<predefinito per crearne uno univoco, ad esempio aggiungendovi "_ number>". Il chiamante deve essere `lpUser`pronto `lpSubProjPath`ad `lpAuxProjPath`accettare le modifiche apportate a , e . Gli `lpSubProjPath` `lpAuxProjPath` argomenti e vengono quindi utilizzati in una chiamata a [SccOpenProject](../extensibility/sccopenproject-function.md). Non devono essere modificati dal chiamante al momento della restituzione. Queste stringhe forniscono un modo per il plug-in del controllo del codice sorgente per tenere traccia delle informazioni che è necessario associare a un progetto. L'IDE chiamante non visualizzerà questi due parametri al momento della restituzione, perché il plug-in può utilizzare una stringa formattata che potrebbe non essere adatto per la visualizzazione. La funzione restituisce un codice di esito positivo `lpSubProjPath` o negativo e, in caso di esito positivo, riempie la variabile con il percorso completo del progetto per il nuovo progetto.

 Questa funzione è simile a [SccGetProjPath](../extensibility/sccgetprojpath-function.md), con la differenza che crea automaticamente un progetto anziché richiedere all'utente di selezionarne uno. Quando `SccCreateSubProject` la funzione `lpParentProjName` viene `lpAuxProjPath` chiamata e non sarà vuota e corrisponderà a un progetto valido. Queste stringhe vengono in genere ricevute dall'IDE da una chiamata precedente alla `SccGetProjPath` funzione o da [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).

 L'argomento `lpUser` è il nome utente. L'IDE passerà lo stesso nome utente `SccGetProjPath`che aveva ricevuto in precedenza da e il plug-in del controllo del codice sorgente deve utilizzare il nome come valore predefinito. Se l'utente ha già una connessione aperta con il plug-in, il plug-in dovrebbe tentare di eliminare eventuali richieste per assicurarsi che la funzione funzioni in modo invisibile all'utente. Tuttavia, se l'accesso non riesce, il plug-in deve richiedere all'utente un account `lpUser`di accesso e, quando riceve un account di accesso valido, passare nuovamente il nome in . Poiché il plug-in può modificare questa stringa, l'IDE allocherà sempre un buffer di dimensioni (SCC_USER_LEN, 1 o SCC_USER_SIZE, che include lo spazio per il carattere di terminazione null). Se la stringa viene modificata, la nuova stringa deve essere un nome di accesso valido (almeno valido come la stringa precedente).

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Note tecniche per SccCreateSubProject e SccGetParentProjectPath
 L'aggiunta di soluzioni e progetti al controllo del codice sorgente è stata semplificata in Visual Studio per ridurre al minimo il numero di volte in cui un utente viene richiesto di selezionare percorsi nel sistema di controllo del codice sorgente. Queste modifiche vengono attivate da Visual Studio se un plug-in `SccCreateSubProject` `SccGetParentProjectPath`del controllo del codice sorgente supporta entrambe le nuove funzioni e . Tuttavia, la seguente voce del Registro di sistema può essere utilizzata per disattivare queste modifiche e ripristinare il comportamento precedente di Visual Studio (Source Control Plug-in API versione 1.1):

 **[HKEY_CURRENT_USER Software Microsoft VisualStudio 8.0/SourceControl] "DoNotCreateSolutionRootFolderInSourceControl" : dword:00000001**

 Se questa voce del Registro di sistema non esiste o è impostata su dword:00000000, Visual Studio tenta di utilizzare le nuove funzioni `SccCreateSubProject` e `SccGetParentProjectPath`.

 Se la voce del Registro di sistema è impostata su dword:00000001, Visual Studio non tenta di utilizzare queste nuove funzioni e le operazioni di aggiunta al controllo del codice sorgente funzionano come nelle versioni precedenti di Visual Studio.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
