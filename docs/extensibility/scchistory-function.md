---
description: Questa funzione visualizza la cronologia dei file specificati.
title: Funzione SccHistory | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccHistory
helpviewer_keywords:
- SccHistory function
ms.assetid: a636d9d3-47c1-4b48-ac6b-bcfde19d6cf9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1208bd0cb13661f1aa60bb9f97c9e4502e517e6d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902540"
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

[in] Struttura del contesto del plug-in del controllo del codice sorgente.

 `hWnd`

[in] Handle per la finestra IDE che il plug-in del controllo del codice sorgente può usare come elemento padre per qualsiasi finestra di dialogo fornita.

 `nFiles`

[in] Numero di file specificati nella `lpFileName` matrice.

 `lpFileName`

[in] Matrice di nomi completi di file.

 `fOptions`

[in] Flag di comando (attualmente non usati).

 `pvOptions`

[in] Opzioni specifiche del plug-in del controllo del codice sorgente.

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|La cronologia delle versioni è stata ottenuta correttamente.|
|SCC_I_RELOADFILE|Il sistema di controllo del codice sorgente ha effettivamente modificato il file su disco durante il recupero della cronologia (ad esempio, recuperando una versione precedente), quindi l'IDE deve ricaricare questo file.|
|SCC_E_FILENOTCONTROLLED|Il file non è sotto il controllo del codice sorgente.|
|SCC_E_OPNOTSUPPORTED|Il sistema di controllo del codice sorgente non supporta questa operazione.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di problemi di connessione. È consigliabile riprovare.|
|SCC_E_PROJNOTOPEN|Il progetto non è stato aperto.|
|SCC_E_NONSPECIFICERROR|Errore non specifico. Non è stato possibile ottenere la cronologia dei file.|

## <a name="remarks"></a>Commenti
 Il plug-in del controllo del codice sorgente può visualizzare la propria finestra di dialogo per visualizzare la cronologia di ogni file, utilizzando `hWnd` come finestra padre. In alternativa, è possibile usare la funzione di callback di output di testo facoltativa fornita a [SccOpenProject,](../extensibility/sccopenproject-function.md) se supportata.

 Si noti che in determinate circostanze, il file esaminato può cambiare durante l'esecuzione di questa chiamata. Ad esempio, il [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] comando history offre all'utente la possibilità di ottenere una versione precedente del file. In tal caso, il plug-in del controllo del codice sorgente restituisce un avviso all'IDE che `SCC_I_RELOAD` deve ricaricare il file.

> [!NOTE]
> Se il plug-in del controllo del codice sorgente non supporta questa funzione per una matrice di file, è possibile visualizzare solo la cronologia dei file per il primo file.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
