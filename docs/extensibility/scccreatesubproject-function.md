---
title: Funzione SccCreateSubProject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCreateSubProject
helpviewer_keywords:
- SccCreateSubProject function
ms.assetid: 08154aed-ae5c-463c-8694-745d0e332965
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f27226e768d639706e5db777b52a0e4957f70e9
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56716233"
---
# <a name="scccreatesubproject-function"></a>Funzione SccCreateSubProject
Questa funzione crea un sottoprogetto con il nome specificato in un progetto padre esistente specificato da di `lpParentProjPath` argomento.

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

[in] Il puntatore di contesto del plug-in controllo di origine.

 hWnd

[in] Handle per la finestra dell'IDE che il plug-in del controllo del codice sorgente è possibile utilizzare come padre per le finestre di dialogo che fornisce.

 lpUser

[in, out] Il nome utente (fino a SCC_USER_SIZE, incluso il carattere di terminazione NULL).

 lpParentProjPath

[in] Stringa che identifica il percorso del progetto principale (fino a SCC_PRJPATH_SIZE, incluso il carattere di terminazione NULL).

 lpSubProjName

[in] Il nome suggerito sottoprogetto (fino a SCC_PRJPATH_SIZE, incluso il carattere di terminazione NULL).

 lpAuxProjPath

[in, out] Stringa ausiliario che identifica il progetto (fino a SCC_PRJPATH_SIZE, incluso il carattere di terminazione NULL).

 lpSubProjPath

[in, out] Stringa di output che identifica il percorso per il sottoprogetto (fino a SCC_PRJPATH_SIZE, incluso il carattere di terminazione NULL).

## <a name="return-value"></a>Valore restituito
 Implementazione di plug-in del controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Sottoprogetto creato correttamente.|
|SCC_E_INITIALIZEFAILED|Nelze inicializovat progetto padre.|
|SCC_E_INVALIDUSER|L'utente non può accedere al sistema di controllo di origine.|
|SCC_E_COULDNOTCREATEPROJECT|Non è possibile creare sottoprogetto.|
|SCC_E_PROJSYNTAXERR|Sintassi non valida del progetto.|
|SCC_E_UNKNOWNPROJECT|Il progetto padre è sconosciuto per il plug-in del controllo del codice sorgente.|
|SCC_E_INVALIDFILEPATH|Percorso del file non valido o inutilizzabile.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete. È consigliabile un nuovo tentativo.|
|SCC_E_CONNECTIONFAILURE|Si è verificato un problema di connessione del plug-in controllo di origine.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Errore non specifico.|

## <a name="remarks"></a>Note
 Se esiste già un sottoprogetto con il nome, la funzione può modificare il nome predefinito per crearne uno univoco, ad esempio aggiungendo "_\<numero >" ad esso. Il chiamante deve essere preparato ad accettare le modifiche apportate a `lpUser`, `lpSubProjPath`, e `lpAuxProjPath`. Il `lpSubProjPath` e`lpAuxProjPath` gli argomenti vengono quindi utilizzati in una chiamata ai [SccOpenProject](../extensibility/sccopenproject-function.md). Essi non deve essere modificati dal chiamante al momento della restituzione. Queste stringhe offrono un modo per il controllo del codice sorgente del plug-in per tenere traccia delle informazioni da associare a un progetto. Il chiamante IDE non visualizzerà questi due parametri al momento della restituzione, perché il plug-in possono usare una stringa formattata che potrebbe non essere appropriata per la visualizzazione. La funzione restituisce un codice di esito positivo o negativo e, se ha esito positivo, inserisce la variabile `lpSubProjPath` con il percorso di progetto completo per il nuovo progetto.

 Questa funzione è simile al [SccGetProjPath](../extensibility/sccgetprojpath-function.md), ad eccezione del fatto che viene creato automaticamente un progetto, invece di chiedere conferma all'utente di selezionare uno. Quando la `SccCreateSubProject` funzione viene chiamata, `lpParentProjName` e `lpAuxProjPath` non sarà vuoto e corrisponderà a un progetto valido. Queste stringhe in genere vengono ricevute dall'IDE da una precedente chiamata ai `SccGetProjPath` funzione o il [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).

 Il `lpUser` argomento è il nome utente. L'IDE passeranno lo stesso nome utente che ha ricevuto in precedenza da `SccGetProjPath`, e il plug-in del controllo del codice sorgente è necessario utilizzare il nome come valore predefinito. Se l'utente ha già una connessione aperta con il plug-in, quindi il plug-in deve provare a eliminare tutte le istruzioni per assicurarsi che il funzionamento della funzione in modo invisibile. Tuttavia, se l'account di accesso non riesce, il plug-in deve richiedere all'utente per un account di accesso e, quando riceve un account di accesso valido, passare di nuovo il nome `lpUser`. Perché il plug-in possono modificare questa stringa, l'IDE sempre dovrà allocare un buffer di dimensione (SCC_USER_LEN + 1 o SCC_USER_SIZE, che include lo spazio per il carattere di terminazione null). Se la stringa viene modificata, la nuova stringa deve essere un nome di account di accesso valido (almeno come valido come stringa precedente).

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Note tecniche per SccCreateSubProject e SccGetParentProjectPath
 Aggiunta di soluzioni e progetti al controllo del codice sorgente è stato semplificato in Visual Studio per ridurre al minimo il numero di volte in cui che un utente viene richiesto di selezionare i percorsi nel sistema di controllo di origine. Queste modifiche sono attivate da Visual Studio, se un controllo del codice sorgente del plug-in supporta sia le nuove funzioni, `SccCreateSubProject` e `SccGetParentProjectPath`. Tuttavia, la voce del Registro di sistema seguente consente di disabilitare queste modifiche e tornare al comportamento precedente di Visual Studio (origine controllo plug-in API versione 1.1):

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl"=dword:00000001**

 Se questa voce del Registro di sistema non esiste o è impostata su dword:00000000, Visual Studio prova a usare le nuove funzioni `SccCreateSubProject` e `SccGetParentProjectPath`.

 Se la voce del Registro di sistema è impostata su dword:00000001, Visual Studio non provi a usare queste nuove funzioni e le operazioni di aggiunta al controllo del codice sorgente funzionano come facevano nelle versioni precedenti di Visual Studio.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in origine controllo](../extensibility/source-control-plug-in-api-functions.md)
- [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)