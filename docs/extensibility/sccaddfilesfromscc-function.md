---
title: Funzione SccAddFilesFromSCC . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAddFilesFromSCC
helpviewer_keywords:
- SccAddFilesFromSCC function
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d22527644edbf1697112f5cf8b73b8a3f72b774
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701281"
---
# <a name="sccaddfilesfromscc-function"></a>SccAddFilesFromSCC (funzione)
Questa funzione aggiunge un elenco di file dal controllo del codice sorgente al progetto attualmente aperto.

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

[in] Puntatore di contesto del plug-in del controllo del codice sorgente.

 hWnd

[in] Un handle per la finestra dell'IDE che il plug-in del controllo del codice sorgente può utilizzare come elemento padre per tutte le finestre di dialogo che fornisce.

 lpUtente

[in, out] Il nome utente (fino a SCC_USER_SIZE, incluso il carattere di terminazione null).

 LpAuxProjPath (percorso in assoluto)

[in, out] Stringa ausiliaria che identifica il `SCC_PRJPATH_`progetto (fino a DIMENSIONE, incluso il carattere di terminazione null).

 CFile (File)

[in] Numero di file `lpFilePaths`forniti da .

 LpFilePaths (Tracciatore file lp)

[in, out] Matrice di nomi di file da aggiungere al progetto corrente.

 LpDestinazione

[in] Percorso di destinazione in cui devono essere scritti i file.

 LpCommento

[in] Commento da applicare a ciascuno dei file aggiunti.

 PbRisultati

[in, out] Matrice di flag impostati per indicare l'esito positivo (diverso da zero o TRUE) o `cFiles` negativo (zero o FALSO) per ogni file (la dimensione della matrice deve essere almeno lunga).

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei seguenti valori:

|valore|Descrizione|
|-----------|-----------------|
|SCC_E_PROJNOTOPEN|Il progetto non è aperto.|
|SCC_E_OPNOTPERFORMED|La connessione non è lo stesso progetto specificato da`lpAuxProjPath.`|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato ad aggiornare il database.|
|SCC_E_NONSPECIFICERROR|Errore sconosciuto.|
|SCC_I_RELOADFILE|Un file o un progetto deve essere ricaricato.|

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
