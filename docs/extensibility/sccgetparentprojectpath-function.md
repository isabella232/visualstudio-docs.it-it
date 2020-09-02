---
title: Funzione SccGetParentProjectPath | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80700708"
---
# <a name="sccgetparentprojectpath-function"></a>SccGetParentProjectPath (funzione)
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

in Puntatore al contesto del plug-in del controllo del codice sorgente.

 hWnd

in Handle per la finestra IDE che il plug-in del controllo del codice sorgente può utilizzare come elemento padre per tutte le finestre di dialogo fornite.

 lpUser

[in, out] Nome utente (fino a SCC_USER_SIZE, incluso il carattere di terminazione NULL).

 lpProjPath

in Stringa che identifica il percorso del progetto (fino a SCC_PRJPATH_SIZE, incluso il carattere di terminazione NULL).

 lpAuxProjPath

[in, out] Stringa ausiliaria che identifica il progetto (fino a SCC_PRJPATH_SIZE, incluso il terminatore NULL).

 lpParentProjPath

[in, out] Stringa di output che identifica il percorso del progetto padre (fino a SCC_PRJPATH_SIZE, incluso il terminatore NULL).

## <a name="return-value"></a>Valore restituito
 Si prevede che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituisca uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Il percorso del progetto padre è stato ottenuto correttamente.|
|SCC_E_INITIALIZEFAILED|Impossibile inizializzare il progetto.|
|SCC_E_INVALIDUSER|L'utente non è riuscito ad accedere al plug-in del controllo del codice sorgente.|
|SCC_E_UNKNOWNPROJECT|Progetto sconosciuto per il plug-in del controllo del codice sorgente.|
|SCC_E_INVALIDFILEPATH|Percorso file non valido o inutilizzabile.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di conflitto. È consigliabile eseguire un nuovo tentativo.|
|SCC_E_PROJSYNTAXERR|Sintassi del progetto non valida.|
|SCC_E_CONNECTIONFAILURE|Problema di connessione dell'archivio.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Errore non specifico.|

## <a name="remarks"></a>Osservazioni
 Questa funzione restituisce un codice di esito positivo o negativo e, in caso di esito positivo, compila la variabile `lpParentProjPath` con il percorso completo del progetto per il progetto specificato.

 Questa funzione restituisce il percorso del progetto padre di un progetto esistente. Per il progetto radice, la funzione restituisce il percorso del progetto passato, ovvero lo stesso percorso del progetto radice. Si noti che un percorso del progetto è una stringa significativa solo per il plug-in del controllo del codice sorgente.

 L'IDE è pronto ad accettare anche le modifiche `lpUser` ai `lpAuxProjPath` parametri e. L'IDE renderà permanente queste stringhe e le passerà a [SccOpenProject](../extensibility/sccopenproject-function.md) quando l'utente apre il progetto in futuro. Queste stringhe forniscono pertanto un modo per il plug-in del controllo del codice sorgente per tenere traccia delle informazioni necessarie per l'associazione a un progetto.

 Questa funzione è simile a [SccGetProjPath](../extensibility/sccgetprojpath-function.md), con la differenza che non richiede all'utente di selezionare un progetto. Inoltre, non crea mai un nuovo progetto ma funziona solo con un progetto esistente.

 Quando `SccGetParentProjectPath` viene chiamato il metodo, `lpProjPath` e `lpAuxProjPath` non saranno vuoti e corrisponderanno a un progetto valido. Queste stringhe vengono in genere ricevute dall'IDE da una precedente chiamata alla `SccGetProjPath` funzione.

 L' `lpUser` argomento è il nome utente. L'IDE passerà lo stesso nome utente ricevuto in precedenza dalla `SccGetProjPath` funzione e il plug-in del controllo del codice sorgente deve usare il nome come valore predefinito. Se l'utente dispone già di una connessione aperta con il plug-in, il plug-in deve tentare di eliminare qualsiasi richiesta per assicurarsi che la funzione funzioni automaticamente. Tuttavia, se l'accesso ha esito negativo, il plug-in deve richiedere all'utente un account di accesso e, quando riceve un account di accesso valido, riportare il nome in `lpUser` . Poiché il plug-in può modificare questa stringa, l'IDE alloca sempre un buffer di dimensione ( `SCC_USER_LEN` + 1). Se la stringa viene modificata, la nuova stringa deve essere un nome di account di accesso valido (almeno valido come stringa precedente).

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Note tecniche per SccCreateSubProject e SccGetParentProjectPath
 L'aggiunta di soluzioni e progetti al controllo del codice sorgente è stata semplificata in Visual Studio per ridurre al minimo il numero di volte in cui a un utente viene richiesto di selezionare i percorsi nel sistema di controllo del codice sorgente. Queste modifiche vengono attivate da Visual Studio se un plug-in del controllo del codice sorgente supporta entrambe le nuove funzioni, [SccCreateSubProject](../extensibility/scccreatesubproject-function.md) e la `SccGetParentProjectPath` funzione. Tuttavia, la voce del registro di sistema seguente può essere usata per disabilitare queste modifiche e ripristinare il comportamento precedente di Visual Studio (plug-in del controllo del codice sorgente versione 1,1):

 **[HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl" = DWORD: 00000001**

 Se questa voce del registro di sistema non esiste o è impostata su DWORD: 00000000, Visual Studio tenta di usare le nuove funzioni, `SccCreateSubProject` e `SccGetParentProjectPath` .

 Se la voce del registro di sistema è impostata su DWORD: 00000001, Visual Studio non tenta di usare queste nuove funzioni e le operazioni di aggiunta al controllo del codice sorgente funzionano come nelle versioni precedenti di Visual Studio.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
