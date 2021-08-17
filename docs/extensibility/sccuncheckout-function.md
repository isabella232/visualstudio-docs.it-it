---
description: Questa funzione annulla un'operazione di estrazione precedente, ripristinando così il contenuto del file o dei file selezionati allo stato precedente all'estrazione.
title: Funzione SccUncheckout | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccUncheckout
helpviewer_keywords:
- SccUncheckout function
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 2282cb845dfb10bf2e0f216ae4203e9b617597c4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122062641"
---
# <a name="sccuncheckout-function"></a>Funzione SccUncheckout
Questa funzione annulla un'operazione di estrazione precedente, ripristinando così il contenuto del file o dei file selezionati allo stato precedente all'estrazione. Tutte le modifiche apportate al file dopo l'estrazione vengono perse.

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccUncheckout (
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

#### <a name="parameters"></a>Parametri
 pvContext

[in] Struttura del contesto del plug-in del controllo del codice sorgente.

 hWnd

[in] Handle per la finestra IDE che il plug-in del controllo del codice sorgente può usare come elemento padre per qualsiasi finestra di dialogo fornita.

 nFiles

[in] Numero di file specificati nella `lpFileNames` matrice.

 lpFileNames

[in] Matrice di nomi di percorsi locali completi dei file per i quali annullare un'estrazione.

 fOptions

[in] Flag di comando (non usati).

 pvOptions

[in] Opzioni specifiche del plug-in del controllo del codice sorgente.

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Annullamento dell'estrazione completato.|
|SCC_E_FILENOTCONTROLLED|Il file selezionato non è sotto il controllo del codice sorgente.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di problemi di connessione. È consigliabile riprovare.|
|SCC_E_NONSPECIFICERROR|Errore non specifico. Annullamento dell'estrazione non riuscito.|
|SCC_E_NOTCHECKEDOUT|Il file non è estratto dall'utente.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|
|SCC_E_PROJNOTOPEN|Il progetto non è stato aperto dal controllo del codice sorgente.|
|SCC_I_OPERATIONCANCELED|L'operazione è stata annullata prima del completamento.|

## <a name="remarks"></a>Commenti
 Dopo questa operazione, i flag e verranno cancellati per i file in cui è stata eseguita `SCC_STATUS_CHECKEDOUT` `SCC_STATUS_MODIFIED` l'estrazione dell'annullamento.

## <a name="see-also"></a>Vedi anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
