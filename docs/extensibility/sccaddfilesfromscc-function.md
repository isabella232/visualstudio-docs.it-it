---
title: SccAddFilesFromSCC Function | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAddFilesFromSCC
helpviewer_keywords:
- SccAddFilesFromSCC function
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cfe58c3eef4b09fccb5cd21b714e5987ae1e08aa
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333970"
---
# <a name="sccaddfilesfromscc-function"></a>Funzione SccAddFilesFromSCC
Questa funzione consente di aggiungere un elenco di file dal controllo del codice sorgente al progetto attualmente aperto.

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccAddFilesFromSCC(
   LPVOID  pContext,
   HWND    hWnd,
   LPSTR   lpUser,
   LPSTR   lpAuxProjPath,
   LONG    cFiles,
   LPCSTR* lpFilePaths,
   LPCSTR  lpDestination,
   LPCSTR  lpComment,
   LPBOOL  pbResults
);
```

### <a name="parameters"></a>Parametri
 pContext

[in] Il puntatore di contesto del plug-in controllo di origine.

 hWnd

[in] Handle per la finestra dell'IDE che il plug-in del controllo del codice sorgente è possibile utilizzare come padre per le finestre di dialogo che fornisce.

 lpUser

[in, out] Il nome utente (fino a SCC_USER_SIZE, incluso il carattere di terminazione null).

 lpAuxProjPath

[in, out] Stringa ausiliario che identifica il progetto (fino a `SCC_PRJPATH_`dimensione, incluso il carattere di terminazione null).

 cFiles

[in] Numero di file specificato da `lpFilePaths`.

 lpFilePaths

[in, out] Matrice di nomi di file da aggiungere al progetto corrente.

 lpDestination

[in] Il percorso di destinazione in cui devono essere scritti i file.

 lpComment

[in] Il commento da applicare a ogni file da aggiungere.

 pbResults

[in, out] Matrice di flag di set per indicare l'esito positivo (diverso da zero o TRUE) o negativo (zero o FALSE) per ogni file (dimensione della matrice deve essere almeno `cFiles` long).

## <a name="return-value"></a>Valore restituito
 Implementazione di plug-in del controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:

|Value|Descrizione|
|-----------|-----------------|
|SCC_E_PROJNOTOPEN|Progetto non è aperto.|
|SCC_E_OPNOTPERFORMED|La connessione non è presente nello stesso progetto come specificato da `lpAuxProjPath.`|
|SCC_E_NOTAUTHORIZED|Utente non è autorizzato ad aggiornare il database.|
|SCC_E_NONSPECIFICERROR|Errore sconosciuto.|
|SCC_I_RELOADFILE|Un progetto o il file deve essere ricaricato.|

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in origine controllo](../extensibility/source-control-plug-in-api-functions.md)