---
description: Questa funzione visualizza le differenze tra la directory locale corrente sul disco client e il progetto corrispondente nel controllo del codice sorgente.
title: Funzione SccDirDiff | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccDirDiff
helpviewer_keywords:
- SccDirDiff function
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 617c94220d13eed915a854bb9cf638bb390db1aeaa3a111c089d65283446f15e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121447766"
---
# <a name="sccdirdiff-function"></a>Funzione SccDirDiff
Questa funzione visualizza le differenze tra la directory locale corrente sul disco client e il progetto corrispondente nel controllo del codice sorgente.

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccDirDiff(
   LPVOID    pContext,
   HWND      hWnd,
   LPCSTR    lpDirName,
   LONG      dwFlags,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Parametri
 pContext

[in] Struttura del contesto del plug-in del controllo del codice sorgente.

 hWnd

[in] Handle per la finestra IDE che il plug-in del controllo del codice sorgente può usare come elemento padre per qualsiasi finestra di dialogo fornita.

 lpDirName

[in] Percorso completo della directory locale per cui visualizzare una differenza visiva.

 dwFlags

[in] Flag di comando (vedere la sezione Osservazioni).

 pvOptions

[in] Opzioni specifiche del plug-in del controllo del codice sorgente.

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|La directory su disco corrisponde al progetto nel controllo del codice sorgente.|
|SCC_I_FILESDIFFER|La directory su disco è diversa dal progetto nel controllo del codice sorgente.|
|SCC_I_RELOADFILE|È necessario ricaricare un file o un progetto.|
|SCC_E_FILENOTCONTROLLED|La directory non è sotto il controllo del codice sorgente.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di problemi di connessione. È consigliabile riprovare.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Errore non specifico.|
|SCC_E_FILENOTEXIST|Impossibile trovare la directory locale.|

## <a name="remarks"></a>Commenti
 Questa funzione viene usata per indicare al plug-in del controllo del codice sorgente di visualizzare all'utente un elenco di modifiche apportate a una directory specificata. Il plug-in apre la propria finestra, in un formato a scelta, per visualizzare le differenze tra la directory dell'utente su disco e il progetto corrispondente nel controllo della versione.

 Se un plug-in supporta il confronto delle directory, deve supportare il confronto delle directory in base al nome file anche se le opzioni "quick-diff" non sono supportate.

|`dwFlags`|Interpretazione|
|---------------|--------------------|
|SCC_DIFF_IGNORECASE|Confronto senza distinzione tra maiuscole e minuscole (può essere usato per diff rapide o oggetti visivi).|
|SCC_DIFF_IGNORESPACE|Ignora gli spazi vuoti (può essere usato per le diff rapide o gli oggetti visivi).|
|SCC_DIFF_QD_CONTENTS|Se supportato dal plug-in del controllo del codice sorgente, confronta automaticamente la directory, byte per byte.|
|SCC_DIFF_QD_CHECKSUM|Se supportato dal plug-in, confronta automaticamente la directory tramite un checksum o, se non è supportato, torna a SCC_DIFF_QD_CONTENTS.|
|SCC_DIFF_QD_TIME|Se supportato dal plug-in, confronta automaticamente la directory tramite il relativo timestamp o, se non è supportato, SCC_DIFF_QD_CHECKSUM o SCC_DIFF_QD_CONTENTS.|

> [!NOTE]
> Questa funzione usa gli stessi flag di comando di [SccDiff.](../extensibility/sccdiff-function.md) Tuttavia, un plug-in di controllo del codice sorgente può scegliere di non supportare l'operazione "quick-diff" per le directory.

## <a name="see-also"></a>Vedi anche
- [Funzioni API plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
