---
description: Questa funzione crea un sottoprogetto con il nome specificato in un progetto padre esistente specificato dall'argomento lpParentProjPath.
title: Funzione SccCreateSubProject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCreateSubProject
helpviewer_keywords:
- SccCreateSubProject function
ms.assetid: 08154aed-ae5c-463c-8694-745d0e332965
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 70568c27afb4bdb5794db64322113dffbd824452
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074002"
---
# <a name="scccreatesubproject-function"></a>SccCreateSubProject (funzione)
Questa funzione crea un sottoprogetto con il nome specificato in un progetto padre esistente specificato dall' `lpParentProjPath` argomento.

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

in Puntatore al contesto del plug-in del controllo del codice sorgente.

 hWnd

in Handle per la finestra IDE che il plug-in del controllo del codice sorgente può utilizzare come elemento padre per tutte le finestre di dialogo fornite.

 lpUser

[in, out] Nome utente (fino a SCC_USER_SIZE, incluso il carattere di terminazione NULL).

 lpParentProjPath

in Stringa che identifica il percorso del progetto padre (fino a SCC_PRJPATH_SIZE, incluso il carattere di terminazione NULL).

 lpSubProjName

in Nome del sottoprogetto suggerito (fino a SCC_PRJPATH_SIZE, incluso il carattere di terminazione NULL).

 lpAuxProjPath

[in, out] Stringa ausiliaria che identifica il progetto (fino a SCC_PRJPATH_SIZE, incluso il terminatore NULL).

 lpSubProjPath

[in, out] Stringa di output che identifica il percorso del sottoprogetto (fino a SCC_PRJPATH_SIZE, incluso il carattere di terminazione NULL).

## <a name="return-value"></a>Valore restituito
 Si prevede che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituisca uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Creazione del sottoprogetto completata.|
|SCC_E_INITIALIZEFAILED|Impossibile inizializzare il progetto padre.|
|SCC_E_INVALIDUSER|L'utente non è riuscito ad accedere al sistema di controllo del codice sorgente.|
|SCC_E_COULDNOTCREATEPROJECT|Non è possibile creare il sottoprogetto.|
|SCC_E_PROJSYNTAXERR|Sintassi del progetto non valida.|
|SCC_E_UNKNOWNPROJECT|Il progetto padre è sconosciuto per il plug-in del controllo del codice sorgente.|
|SCC_E_INVALIDFILEPATH|Percorso file non valido o inutilizzabile.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di conflitto. È consigliabile eseguire un nuovo tentativo.|
|SCC_E_CONNECTIONFAILURE|Si è verificato un problema di connessione del plug-in del controllo del codice sorgente.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Errore non specifico.|

## <a name="remarks"></a>Commenti
 Se esiste già un sottoprogetto con il nome, la funzione può modificare il nome predefinito per crearne uno univoco, ad esempio aggiungendo "_ \<number> ". Il chiamante deve essere pronto ad accettare le modifiche apportate a `lpUser` , `lpSubProjPath` e `lpAuxProjPath` . Gli `lpSubProjPath` `lpAuxProjPath` argomenti e vengono quindi utilizzati in una chiamata a [SccOpenProject](../extensibility/sccopenproject-function.md). Non devono essere modificati dal chiamante al momento della restituzione. Queste stringhe forniscono un modo per il plug-in del controllo del codice sorgente per tenere traccia delle informazioni che devono essere associate a un progetto. L'IDE chiamante non visualizzerà questi due parametri al momento della restituzione, perché il plug-in può usare una stringa formattata che potrebbe non essere adatta per la visualizzazione. La funzione restituisce un codice di esito positivo o negativo e, in caso di esito positivo, compila la variabile `lpSubProjPath` con il percorso completo del progetto del nuovo progetto.

 Questa funzione è simile a [SccGetProjPath](../extensibility/sccgetprojpath-function.md), con la differenza che viene creato automaticamente un progetto anziché richiedere all'utente di selezionarne uno. Quando `SccCreateSubProject` viene chiamata la funzione, `lpParentProjName` e `lpAuxProjPath` non saranno vuoti e corrisponderanno a un progetto valido. Queste stringhe vengono in genere ricevute dall'IDE da una precedente chiamata alla `SccGetProjPath` funzione o a [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).

 L' `lpUser` argomento è il nome utente. L'IDE passerà lo stesso nome utente ricevuto in precedenza da `SccGetProjPath` e il plug-in del controllo del codice sorgente deve usare il nome come valore predefinito. Se l'utente dispone già di una connessione aperta con il plug-in, il plug-in deve tentare di eliminare qualsiasi richiesta per assicurarsi che la funzione funzioni automaticamente. Tuttavia, se l'accesso ha esito negativo, il plug-in deve richiedere all'utente un account di accesso e, quando riceve un account di accesso valido, riportare il nome in `lpUser` . Poiché il plug-in può modificare questa stringa, l'IDE alloca sempre un buffer di dimensione (SCC_USER_LEN + 1 o SCC_USER_SIZE, che include lo spazio per il carattere di terminazione null). Se la stringa viene modificata, la nuova stringa deve essere un nome di account di accesso valido (almeno valido come stringa precedente).

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Note tecniche per SccCreateSubProject e SccGetParentProjectPath
 L'aggiunta di soluzioni e progetti al controllo del codice sorgente è stata semplificata in Visual Studio per ridurre al minimo il numero di volte in cui a un utente viene richiesto di selezionare i percorsi nel sistema di controllo del codice sorgente. Queste modifiche vengono attivate da Visual Studio se un plug-in del controllo del codice sorgente supporta entrambe le nuove funzioni, `SccCreateSubProject` e `SccGetParentProjectPath` . Tuttavia, la voce del registro di sistema seguente può essere usata per disabilitare queste modifiche e ripristinare il comportamento precedente di Visual Studio (API plug-in del controllo del codice sorgente versione 1,1):

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl" = DWORD: 00000001**

 Se questa voce del registro di sistema non esiste o è impostata su DWORD: 00000000, Visual Studio tenta di usare le nuove funzioni, `SccCreateSubProject` e `SccGetParentProjectPath` .

 Se la voce del registro di sistema è impostata su DWORD: 00000001, Visual Studio non tenta di usare queste nuove funzioni e le operazioni di aggiunta al controllo del codice sorgente funzionano come nelle versioni precedenti di Visual Studio.

## <a name="see-also"></a>Vedi anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
