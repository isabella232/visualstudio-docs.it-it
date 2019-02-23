---
title: Funzione SccGetParentProjectPath | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetParentProjectPath
helpviewer_keywords:
- SccGetParentProjectPath function
ms.assetid: 62a71579-36b3-48b9-a1c8-04ab100efa08
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e05b66f8168701b23c1638b35957777924f9d815
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56679216"
---
# <a name="sccgetparentprojectpath-function"></a>Funzione SccGetParentProjectPath
Questa funzione determina il percorso del progetto padre di un progetto specificato. Questa funzione viene chiamata quando l'utente sta aggiungendo un progetto di Visual Studio al controllo del codice sorgente.

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

[in] Il puntatore di contesto del plug-in controllo di origine.

 hWnd

[in] Handle per la finestra dell'IDE che il plug-in del controllo del codice sorgente è possibile utilizzare come padre per le finestre di dialogo che fornisce.

 lpUser

[in, out] Il nome utente (fino a SCC_USER_SIZE, incluso il carattere di terminazione NULL).

 lpProjPath

[in] Stringa che identifica il percorso del progetto (fino a SCC_PRJPATH_SIZE, incluso il carattere di terminazione NULL).

 lpAuxProjPath

[in, out] Stringa ausiliario che identifica il progetto (fino a SCC_PRJPATH_SIZE, incluso il carattere di terminazione NULL).

 lpParentProjPath

[in, out] Stringa di output che identifica il percorso del progetto padre (fino a SCC_PRJPATH_SIZE, incluso il carattere di terminazione NULL).

## <a name="return-value"></a>Valore restituito
 Implementazione di plug-in del controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:

|Value|Descrizione|
|-----------|-----------------|
|SCC_OK|Percorso del progetto padre è stata ottenuta correttamente.|
|SCC_E_INITIALIZEFAILED|Progetto non è stato possibile inizializzare.|
|SCC_E_INVALIDUSER|L'utente non può accedere per il plug-in del controllo del codice sorgente.|
|SCC_E_UNKNOWNPROJECT|Progetto è sconosciuto per il plug-in del controllo del codice sorgente.|
|SCC_E_INVALIDFILEPATH|Percorso del file non valido o inutilizzabile.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete. È consigliabile un nuovo tentativo.|
|SCC_E_PROJSYNTAXERR|Sintassi non valida del progetto.|
|SCC_E_CONNECTIONFAILURE|Problema di connessione Store.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Errore non specifico.|

## <a name="remarks"></a>Note
 Questa funzione restituisce un codice di esito positivo o negativo e, se ha esito positivo, inserisce la variabile `lpParentProjPath` con il percorso di progetto completo per il progetto specificato.

 Questa funzione restituisce l'elemento padre di percorso del progetto di un progetto esistente. Per il progetto radice, la funzione restituisce il percorso del progetto che è stato passato (vale a dire, stesso progetto percorso radice). Si noti che un percorso del progetto è una stringa che è significativa solo per il plug-in del controllo del codice sorgente.

 L'IDE è pronto per accettare le modifiche per il `lpUser` e `lpAuxProjPath` anche i parametri. L'IDE verrà mantenute queste stringhe e passarle per la [SccOpenProject](../extensibility/sccopenproject-function.md) quando l'utente apre il progetto in futuro. Queste stringhe, pertanto, forniscono un modo per il controllo del codice sorgente del plug-in per le informazioni di traccia da associare a un progetto.

 Questa funzione è simile al [SccGetProjPath](../extensibility/sccgetprojpath-function.md), ad eccezione del fatto che non richiede all'utente di selezionare un progetto. Anche mai crea un nuovo progetto ma funziona solo con un progetto esistente.

 Quando `SccGetParentProjectPath` viene chiamato `lpProjPath` e `lpAuxProjPath` non sarà vuoto e corrisponderà a un progetto valido. Queste stringhe in genere vengono ricevute dall'IDE da una chiamata precedente al `SccGetProjPath` (funzione).

 Il `lpUser` argomento è il nome utente. L'IDE passeranno lo stesso nome utente che ha ricevuto in precedenza dal `SccGetProjPath` (funzione) e il plug-in del controllo del codice sorgente devono usare il nome come valore predefinito. Se l'utente ha già una connessione aperta con il plug-in, quindi il plug-in deve provare a eliminare tutte le istruzioni per assicurarsi che il funzionamento della funzione in modo invisibile. Tuttavia, se l'account di accesso non riesce, il plug-in deve richiedere all'utente per un account di accesso e, quando riceve un account di accesso valido, passare di nuovo il nome `lpUser`. Poiché il plug-in possono modificare questa stringa, l'IDE sempre dovrà allocare un buffer di dimensione (`SCC_USER_LEN`+ 1). Se la stringa viene modificata, la nuova stringa deve essere un nome di account di accesso valido (almeno come valido come stringa precedente).

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Note tecniche per SccCreateSubProject e SccGetParentProjectPath
 Aggiunta di soluzioni e progetti al controllo del codice sorgente è stato semplificato in Visual Studio per ridurre al minimo il numero di volte in cui che un utente viene richiesto di selezionare i percorsi nel sistema di controllo di origine. Queste modifiche sono attivate da Visual Studio, se un controllo del codice sorgente del plug-in supporta sia le nuove funzioni, il [SccCreateSubProject](../extensibility/scccreatesubproject-function.md) e il `SccGetParentProjectPath` (funzione). Tuttavia, la voce del Registro di sistema seguente consente di disabilitare queste modifiche e ripristinare il comportamento precedente di Visual Studio (origine controllo plug-in API versione 1.1):

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl"=dword:00000001**

 Se questa voce del Registro di sistema non esiste o è impostata su dword:00000000, Visual Studio prova a usare le nuove funzioni `SccCreateSubProject`e`SccGetParentProjectPath`.

 Se la voce del Registro di sistema è impostata su dword:00000001, Visual Studio non provi a usare queste nuove funzioni e le operazioni di aggiunta al controllo del codice sorgente funzionano come facevano nelle versioni precedenti di Visual Studio.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in origine controllo](../extensibility/source-control-plug-in-api-functions.md)
- [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)