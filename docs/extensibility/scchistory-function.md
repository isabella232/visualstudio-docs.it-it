---
title: Funzione SccHistory | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccHistory
helpviewer_keywords:
- SccHistory function
ms.assetid: a636d9d3-47c1-4b48-ac6b-bcfde19d6cf9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0ce0b38b8e602688875549edbac671e664809482
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721248"
---
# <a name="scchistory-function"></a>Funzione SccHistory
Questa funzione Visualizza la cronologia dei file specificati.

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

in Struttura del contesto del plug-in del controllo del codice sorgente.

 `hWnd`

in Handle per la finestra IDE che il plug-in del controllo del codice sorgente può utilizzare come elemento padre per tutte le finestre di dialogo fornite.

 `nFiles`

in Numero di file specificati nella matrice `lpFileName`.

 `lpFileName`

in Matrice di nomi completi di file.

 `fOptions`

in Flag di comando (attualmente non usati).

 `pvOptions`

in Opzioni specifiche del plug-in del controllo del codice sorgente.

## <a name="return-value"></a>Valore restituito
 Si prevede che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituisca uno dei valori seguenti:

|Value|Descrizione|
|-----------|-----------------|
|SCC_OK|La cronologia delle versioni è stata ottenuta correttamente.|
|SCC_I_RELOADFILE|Il sistema di controllo del codice sorgente ha effettivamente modificato il file su disco durante il recupero della cronologia (ad esempio, ottenendo una versione precedente), quindi l'IDE deve ricaricare il file.|
|SCC_E_FILENOTCONTROLLED|Il file non è sotto il controllo del codice sorgente.|
|SCC_E_OPNOTSUPPORTED|Il sistema di controllo del codice sorgente non supporta questa operazione.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di conflitto. È consigliabile eseguire un nuovo tentativo.|
|SCC_E_PROJNOTOPEN|Il progetto non è stato aperto.|
|SCC_E_NONSPECIFICERROR|Errore non specifico. Impossibile ottenere la cronologia file.|

## <a name="remarks"></a>Note
 Il plug-in del controllo del codice sorgente può visualizzare la relativa finestra di dialogo per visualizzare la cronologia di ogni file, usando `hWnd` come finestra padre. In alternativa, è possibile usare la funzione di callback di output di testo facoltativa fornita a [SccOpenProject](../extensibility/sccopenproject-function.md) , se supportata.

 Si noti che in determinate circostanze, il file esaminato potrebbe cambiare durante l'esecuzione di questa chiamata. Ad esempio, il comando [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] cronologia offre all'utente la possibilità di ottenere una versione precedente del file. In tal caso, il plug-in del controllo del codice sorgente restituisce `SCC_I_RELOAD` per avvisare l'IDE che è necessario ricaricare il file.

> [!NOTE]
> Se il plug-in del controllo del codice sorgente non supporta questa funzione per una matrice di file, è possibile visualizzare solo la cronologia file per il primo file.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)