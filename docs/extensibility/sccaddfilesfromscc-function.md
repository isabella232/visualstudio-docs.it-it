---
title: Funzione SccAddFilesFromSCC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAddFilesFromSCC
helpviewer_keywords:
- SccAddFilesFromSCC function
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c230d1dae4b6ff9552a8ff464d3128eac9be1482
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99926846"
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

in Puntatore al contesto del plug-in del controllo del codice sorgente.

 hWnd

in Handle per la finestra IDE che il plug-in del controllo del codice sorgente può utilizzare come elemento padre per tutte le finestre di dialogo fornite.

 lpUser

[in, out] Nome utente (fino a SCC_USER_SIZE, incluso il carattere di terminazione null).

 lpAuxProjPath

[in, out] Stringa ausiliaria che identifica il progetto (fino alla `SCC_PRJPATH_` dimensione, incluso il carattere di terminazione null).

 cFiles

in Numero di file specificati da `lpFilePaths` .

 lpFilePaths

[in, out] Matrice di nomi di file da aggiungere al progetto corrente.

 lpDestination

in Percorso di destinazione in cui devono essere scritti i file.

 lpComment

in Commento da applicare a ognuno dei file aggiunti.

 pbResults

[in, out] Matrice di flag impostati per indicare l'esito positivo (valore diverso da zero o TRUE) o errore (zero o FALSE) per ogni file (la dimensione della matrice deve essere almeno `cFiles` Long).

## <a name="return-value"></a>Valore restituito
 Si prevede che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituisca uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_E_PROJNOTOPEN|Il progetto non è aperto.|
|SCC_E_OPNOTPERFORMED|La connessione non è allo stesso progetto specificata da `lpAuxProjPath.`|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato ad aggiornare il database.|
|SCC_E_NONSPECIFICERROR|Errore sconosciuto.|
|SCC_I_RELOADFILE|È necessario ricaricare un file o un progetto.|

## <a name="see-also"></a>Vedi anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
