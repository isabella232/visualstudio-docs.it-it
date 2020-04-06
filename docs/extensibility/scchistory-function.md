---
title: Funzione SccHistory . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccHistory
helpviewer_keywords:
- SccHistory function
ms.assetid: a636d9d3-47c1-4b48-ac6b-bcfde19d6cf9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 734afefd97e61867076d487acbcf67f10f54e672
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700656"
---
# <a name="scchistory-function"></a>Funzione SccHistory
Questa funzione visualizza la cronologia dei file specificati.

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccHistory(
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

#### <a name="parameters"></a>Parametri
 `pvContext`

[in] Struttura di contesto del plug-in del controllo del codice sorgente.

 `hWnd`

[in] Un handle per la finestra dell'IDE che il plug-in del controllo del codice sorgente può utilizzare come elemento padre per tutte le finestre di dialogo che fornisce.

 `nFiles`

[in] Numero di file `lpFileName` specificati nella matrice.

 `lpFileName`

[in] Matrice di nomi completi di file.

 `fOptions`

[in] Flag di comando (attualmente non utilizzati).

 `pvOptions`

[in] Opzioni specifiche del plug-in del controllo del codice sorgente.

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei seguenti valori:

|valore|Descrizione|
|-----------|-----------------|
|SCC_OK|La cronologia delle versioni è stata ottenuta correttamente.|
|SCC_I_RELOADFILE|Il sistema di controllo del codice sorgente effettivamente modificato il file su disco durante il recupero della cronologia (ad esempio, ottenendo una versione precedente di esso), pertanto l'IDE deve ricaricare il file.|
|SCC_E_FILENOTCONTROLLED|Il file non è sotto il controllo del codice sorgente.|
|SCC_E_OPNOTSUPPORTED|Il sistema di controllo del codice sorgente non supporta questa operazione.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di contesa. È consigliabile eseguire un nuovo tentativo.|
|SCC_E_PROJNOTOPEN|Il progetto non è stato aperto.|
|SCC_E_NONSPECIFICERROR|Errore non specifico. Impossibile ottenere la cronologia dei file.|

## <a name="remarks"></a>Osservazioni
 Il plug-in del controllo del codice sorgente può visualizzare la `hWnd` propria finestra di dialogo per visualizzare la cronologia di ogni file, utilizzando come finestra padre. In alternativa, è possibile utilizzare la funzione di callback di output di testo facoltativa fornita a [SccOpenProject,](../extensibility/sccopenproject-function.md) se supportata.

 Si noti che in determinate circostanze, il file esaminato può cambiare durante l'esecuzione di questa chiamata. Ad esempio, [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] il comando history offre all'utente la possibilità di ottenere una versione precedente del file. In tal caso, il plug-in `SCC_I_RELOAD` controllo del codice sorgente restituisce per avvisare l'IDE che è necessario ricaricare il file.

> [!NOTE]
> Se il plug-in del controllo del codice sorgente non supporta questa funzione per una matrice di file, è possibile visualizzare solo la cronologia dei file per il primo file.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
