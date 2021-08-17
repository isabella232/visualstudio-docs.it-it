---
description: Questa funzione crea un sottoprogetto con il nome specificato in un progetto padre esistente specificato dall'argomento lpParentProjPath.
title: Funzione SccCreateSubProject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccCreateSubProject
helpviewer_keywords:
- SccCreateSubProject function
ms.assetid: 08154aed-ae5c-463c-8694-745d0e332965
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 39575ce0c85ef47867ffc508fd50843e7bae888f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122124451"
---
# <a name="scccreatesubproject-function"></a>Funzione SccCreateSubProject
Questa funzione crea un sottoprogetto con il nome specificato in un progetto padre esistente specificato `lpParentProjPath` dall'argomento .

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

[in] Puntatore al contesto del plug-in del controllo del codice sorgente.

 hWnd

[in] Handle per la finestra IDE che il plug-in del controllo del codice sorgente può usare come elemento padre per qualsiasi finestra di dialogo fornita.

 lpUser

[in, out] Nome utente (fino a SCC_USER_SIZE, incluso il carattere di terminazione NULL).

 lpParentProjPath

[in] Stringa che identifica il percorso del progetto padre (fino a SCC_PRJPATH_SIZE, incluso il carattere di terminazione NULL).

 lpSubProjName

[in] Nome del sottoprogetto suggerito (fino a SCC_PRJPATH_SIZE, incluso il carattere di terminazione NULL).

 lpAuxProjPath

[in, out] Stringa ausiliaria che identifica il progetto (fino a SCC_PRJPATH_SIZE, incluso il carattere di terminazione NULL).

 lpSubProjPath

[in, out] Stringa di output che identifica il percorso del sottoprogetto (fino a SCC_PRJPATH_SIZE, incluso il carattere di terminazione NULL).

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Il sottoprogetto è stato creato correttamente.|
|SCC_E_INITIALIZEFAILED|Non è stato possibile inizializzare il progetto padre.|
|SCC_E_INVALIDUSER|L'utente non è stato in grado di accedere al sistema di controllo del codice sorgente.|
|SCC_E_COULDNOTCREATEPROJECT|Non è possibile creare un sottoprogetto.|
|SCC_E_PROJSYNTAXERR|Sintassi del progetto non valida.|
|SCC_E_UNKNOWNPROJECT|Il progetto padre è sconosciuto al plug-in del controllo del codice sorgente.|
|SCC_E_INVALIDFILEPATH|Percorso di file non valido o inutilizzabile.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di problemi di connessione. È consigliabile riprovare.|
|SCC_E_CONNECTIONFAILURE|Si è verificato un problema di connessione al plug-in del controllo del codice sorgente.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Errore non specifico.|

## <a name="remarks"></a>Commenti
 Se esiste già un sottoprogetto con il nome , la funzione può modificare il nome predefinito per crearne uno univoco, ad esempio aggiungendo "_ \<number> ". Il chiamante deve essere pronto ad accettare le modifiche `lpUser` apportate a , e `lpSubProjPath` `lpAuxProjPath` . Gli `lpSubProjPath` argomenti e vengono quindi usati in una chiamata a `lpAuxProjPath` [SccOpenProject.](../extensibility/sccopenproject-function.md) Non devono essere modificati dal chiamante al momento della restituzione. Queste stringhe consentono al plug-in del controllo del codice sorgente di tenere traccia delle informazioni da associare a un progetto. L'IDE chiamante non visualizzerà questi due parametri al momento della restituzione, perché il plug-in può usare una stringa formattata che potrebbe non essere adatta per la visualizzazione. La funzione restituisce un codice di esito positivo o negativo e, in caso di esito positivo, inserisce nella variabile il percorso completo `lpSubProjPath` del progetto del nuovo progetto.

 Questa funzione è simile a [SccGetProjPath,](../extensibility/sccgetprojpath-function.md)ad eccezione del fatto che crea automaticamente un progetto anziché chiedere all'utente di selezionarne uno. Quando viene `SccCreateSubProject` chiamata la funzione , non sarà vuota e `lpParentProjName` `lpAuxProjPath` corrisponderà a un progetto valido. Queste stringhe vengono in genere ricevute dall'IDE da una chiamata precedente alla funzione `SccGetProjPath` o [da SccGetParentProjectPath.](../extensibility/sccgetparentprojectpath-function.md)

 `lpUser`L'argomento è il nome utente. L'IDE passerà lo stesso nome utente ricevuto in precedenza da e il plug-in del controllo del codice sorgente deve usare `SccGetProjPath` il nome come predefinito. Se l'utente ha già una connessione aperta con il plug-in, il plug-in deve provare a eliminare eventuali richieste per assicurarsi che la funzione funzioni automaticamente. Tuttavia, se l'accesso non riesce, il plug-in deve richiedere all'utente un account di accesso e, quando riceve un account di accesso valido, passare nuovamente il nome in `lpUser` . Poiché il plug-in può modificare questa stringa, l'IDE alloca sempre un buffer di dimensioni (SCC_USER_LEN+1 o SCC_USER_SIZE, che include lo spazio per il carattere di terminazione Null). Se la stringa viene modificata, la nuova stringa deve essere un nome di account di accesso valido (almeno valido come la stringa precedente).

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Note tecniche per SccCreateSubProject e SccGetParentProjectPath
 L'aggiunta di soluzioni e progetti al controllo del codice sorgente è stata semplificata in Visual Studio per ridurre al minimo il numero di volte in cui viene richiesto all'utente di selezionare i percorsi nel sistema di controllo del codice sorgente. Queste modifiche vengono attivate Visual Studio se un plug-in del controllo del codice sorgente supporta entrambe le nuove funzioni, `SccCreateSubProject` e `SccGetParentProjectPath` . È tuttavia possibile usare la voce del Registro di sistema seguente per disabilitare queste modifiche e ripristinare il comportamento precedente di Visual Studio (plug-in del controllo del codice sorgente versione 1.1):

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl"=dword:00000001**

 Se questa voce del Registro di sistema non esiste o è impostata su dword:00000000, Visual Studio tenta di usare le nuove funzioni `SccCreateSubProject` e `SccGetParentProjectPath` .

 Se la voce del Registro di sistema è impostata su dword:00000001, Visual Studio non tenta di usare queste nuove funzioni e le operazioni di aggiunta al controllo del codice sorgente funzionano come nelle versioni precedenti di Visual Studio.

## <a name="see-also"></a>Vedi anche
- [Funzioni API plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
