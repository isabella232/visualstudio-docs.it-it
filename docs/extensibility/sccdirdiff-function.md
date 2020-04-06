---
title: Funzione SccDirDiff . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDirDiff
helpviewer_keywords:
- SccDirDiff function
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1bb592a1174a91480ed76ef818733c288c5273c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701006"
---
# <a name="sccdirdiff-function"></a>SccDirDiff (funzione SccDir)
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

[in] Struttura di contesto del plug-in del controllo del codice sorgente.

 hWnd

[in] Un handle per la finestra dell'IDE che il plug-in del controllo del codice sorgente può utilizzare come elemento padre per tutte le finestre di dialogo che fornisce.

 LpDirName (nome dall'utente)

[in] Percorso completo della directory locale per cui mostrare una differenza visiva.

 dwFlags

[in] Flag di comando (vedere la sezione Osservazioni).

 PvOpzioni

[in] Opzioni specifiche del plug-in del controllo del codice sorgente.

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei seguenti valori:

|valore|Descrizione|
|-----------|-----------------|
|SCC_OK|La directory su disco è la stessa del progetto nel controllo del codice sorgente.|
|SCC_I_FILESDIFFER|La directory su disco è diversa dal progetto nel controllo del codice sorgente.|
|SCC_I_RELOADFILE|Un file o un progetto deve essere ricaricato.|
|SCC_E_FILENOTCONTROLLED|La directory non è sotto il controllo del codice sorgente.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di contesa. È consigliabile eseguire un nuovo tentativo.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Errore non specifico.|
|SCC_E_FILENOTEXIST|Impossibile trovare la directory locale.|

## <a name="remarks"></a>Osservazioni
 Questa funzione viene utilizzata per indicare al plug-in del controllo del codice sorgente di visualizzare all'utente un elenco di modifiche a una directory specificata. Il plug-in apre la propria finestra, in un formato di sua scelta, per visualizzare le differenze tra la directory dell'utente su disco e il progetto corrispondente sotto il controllo della versione.

 Se un plug-in supporta il confronto delle directory, deve supportare il confronto delle directory in base al nome del file anche se le opzioni "quick-diff" non sono supportate.

|`dwFlags`|Interpretazione|
|---------------|--------------------|
|SCC_DIFF_IGNORECASE|Confronto senza distinzione tra maiuscole e minuscole (può essere utilizzato per diff rapido o visivo).|
|SCC_DIFF_IGNORESPACE|Ignora gli spazi vuoti (può essere utilizzato per quick-diff o visual).|
|SCC_DIFF_QD_CONTENTS|Se supportato dal plug-in del controllo del codice sorgente, confronta automaticamente la directory byte per byte.|
|SCC_DIFF_QD_CHECKSUM|Se supportato dal plug-in, confronta automaticamente la directory tramite un checksum o, se non è supportato, esegue il fallback a SCC_DIFF_QD_CONTENTS.|
|SCC_DIFF_QD_TIME|Se supportato dal plug-in, confronta automaticamente la directory tramite il timestamp o, se non è supportato, esegue il fallback su SCC_DIFF_QD_CHECKSUM o SCC_DIFF_QD_CONTENTS.|

> [!NOTE]
> Questa funzione utilizza gli stessi flag di comando di [SccDiff](../extensibility/sccdiff-function.md). Tuttavia, un plug-in del controllo del codice sorgente potrebbe scegliere di non supportare l'operazione "quick-diff" per le directory.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
