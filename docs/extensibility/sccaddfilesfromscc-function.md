---
description: Questa funzione aggiunge un elenco di file dal controllo del codice sorgente al progetto attualmente aperto.
title: Funzione SccAddFilesFromSCC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccAddFilesFromSCC
helpviewer_keywords:
- SccAddFilesFromSCC function
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: c8d8715f18d68c6e8f3250f25e14a45da48ab8cd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122144704"
---
# <a name="sccaddfilesfromscc-function"></a>Funzione SccAddFilesFromSCC
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

[in] Puntatore al contesto del plug-in del controllo del codice sorgente.

 hWnd

[in] Handle per la finestra IDE che il plug-in del controllo del codice sorgente può usare come elemento padre per qualsiasi finestra di dialogo fornita.

 lpUser

[in, out] Nome utente (fino a SCC_USER_SIZE, incluso il carattere di terminazione Null).

 lpAuxProjPath

[in, out] Stringa ausiliaria che identifica il progetto (fino a `SCC_PRJPATH_` SIZE, incluso il carattere di terminazione Null).

 cFiles

[in] Numero di file specificato da `lpFilePaths` .

 lpFilePaths

[in, out] Matrice di nomi di file da aggiungere al progetto corrente.

 lpDestination

[in] Percorso di destinazione in cui devono essere scritti i file.

 lpComment

[in] Commento da applicare a ogni file aggiunto.

 pbResults

[in, out] Matrice di flag impostati per indicare l'esito positivo (diverso da zero o TRUE) o negativo (zero o FALSE) per ogni file (le dimensioni della matrice devono essere almeno `cFiles` lunghe).

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_E_PROJNOTOPEN|Project non è aperto.|
|SCC_E_OPNOTPERFORMED|La connessione non è allo stesso progetto specificato da `lpAuxProjPath.`|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato ad aggiornare il database.|
|SCC_E_NONSPECIFICERROR|Errore sconosciuto.|
|SCC_I_RELOADFILE|È necessario ricaricare un file o un progetto.|

## <a name="see-also"></a>Vedi anche
- [Funzioni API plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
