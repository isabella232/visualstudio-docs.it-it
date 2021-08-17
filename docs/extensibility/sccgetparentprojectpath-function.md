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
ms.openlocfilehash: d75640372839c4fddf83ec098879e9eb0479eb4f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122049480"
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

[in] Stringa che identifica il percorso del progetto (fino a SCC_PRJPATH_SIZE, incluso il carattere di terminazione NULL).

 lpAuxProjPath

[in, out] Stringa ausiliaria che identifica il progetto (fino a SCC_PRJPATH_SIZE, incluso il carattere di terminazione NULL).

 lpParentProjPath

[in, out] Stringa di output che identifica il percorso del progetto padre (fino a SCC_PRJPATH_SIZE, incluso il carattere di terminazione NULL).

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Il percorso del progetto padre è stato ottenuto correttamente.|
|SCC_E_INITIALIZEFAILED|Project non è stato possibile inizializzare.|
|SCC_E_INVALIDUSER|L'utente non è stato in grado di accedere al plug-in del controllo del codice sorgente.|
|SCC_E_UNKNOWNPROJECT|Project è sconosciuto al plug-in del controllo del codice sorgente.|
|SCC_E_INVALIDFILEPATH|Percorso di file non valido o inutilizzabile.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di problemi di connessione. È consigliabile riprovare.|
|SCC_E_PROJSYNTAXERR|Sintassi del progetto non valida.|
|SCC_E_CONNECTIONFAILURE|Problema di connessione dell'archivio.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Errore non specifico.|

## <a name="remarks"></a>Commenti
 Questa funzione restituisce un codice di esito positivo o negativo e, in caso di esito positivo, inserisce nella variabile il percorso completo del progetto `lpParentProjPath` specificato.

 Questa funzione restituisce il percorso del progetto padre di un progetto esistente. Per il progetto radice, la funzione restituisce il percorso del progetto passato, ovvero lo stesso percorso del progetto radice. Si noti che il percorso di un progetto è una stringa significativa solo per il plug-in del controllo del codice sorgente.

 L'IDE è pronto ad accettare anche le `lpUser` modifiche ai parametri e `lpAuxProjPath` . L'IDE rende persistenti queste stringhe e le passa a [SccOpenProject](../extensibility/sccopenproject-function.md) quando l'utente apre il progetto in futuro. Queste stringhe consentono quindi al plug-in del controllo del codice sorgente di tenere traccia delle informazioni da associare a un progetto.

 Questa funzione è simile a [SccGetProjPath,](../extensibility/sccgetprojpath-function.md)ad eccezione del fatto che non richiede all'utente di selezionare un progetto. Non crea mai un nuovo progetto, ma funziona solo con un progetto esistente.

 Quando `SccGetParentProjectPath` viene chiamato , e non saranno `lpProjPath` `lpAuxProjPath` vuoti e corrisponderanno a un progetto valido. Queste stringhe vengono in genere ricevute dall'IDE da una chiamata precedente alla `SccGetProjPath` funzione .

 `lpUser`L'argomento è il nome utente. L'IDE passerà lo stesso nome utente ricevuto in precedenza dalla funzione e il plug-in del controllo del codice sorgente deve usare `SccGetProjPath` il nome come predefinito. Se l'utente ha già una connessione aperta con il plug-in, il plug-in deve provare a eliminare eventuali richieste per assicurarsi che la funzione funzioni automaticamente. Tuttavia, se l'accesso non riesce, il plug-in deve richiedere all'utente un account di accesso e, quando riceve un account di accesso valido, passare nuovamente il nome in `lpUser` . Poiché il plug-in può modificare questa stringa, l'IDE alloca sempre un buffer di dimensioni ( `SCC_USER_LEN` +1). Se la stringa viene modificata, la nuova stringa deve essere un nome di account di accesso valido (almeno valido come la stringa precedente).

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Note tecniche per SccCreateSubProject e SccGetParentProjectPath
 L'aggiunta di soluzioni e progetti al controllo del codice sorgente è stata semplificata in Visual Studio per ridurre al minimo il numero di volte in cui viene richiesto all'utente di selezionare i percorsi nel sistema di controllo del codice sorgente. Queste modifiche vengono attivate Visual Studio se un plug-in del controllo del codice sorgente supporta entrambe le nuove funzioni, [SccCreateSubProject](../extensibility/scccreatesubproject-function.md) e `SccGetParentProjectPath` la funzione . È tuttavia possibile usare la voce del Registro di sistema seguente per disabilitare queste modifiche e ripristinare il comportamento precedente di Visual Studio (plug-in del controllo del codice sorgente versione 1.1):

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl"=dword:00000001**

 Se questa voce del Registro di sistema non esiste o è impostata su dword:00000000, Visual Studio tenta di usare le nuove funzioni `SccCreateSubProject` e `SccGetParentProjectPath` .

 Se la voce del Registro di sistema è impostata su dword:00000001, Visual Studio non tenta di usare queste nuove funzioni e le operazioni di aggiunta al controllo del codice sorgente funzionano come nelle versioni precedenti di Visual Studio.

## <a name="see-also"></a>Vedi anche
- [Funzioni API plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
