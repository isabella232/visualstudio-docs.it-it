---
description: Questa funzione annulla un'operazione di estrazione precedente, ripristinando lo stato del contenuto del file o dei file selezionati prima dell'estrazione.
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
ms.workload:
- vssdk
ms.openlocfilehash: 3a382a112b5a11acc36c52735c949ebef71052ec
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904087"
---
# <a name="sccuncheckout-function"></a>Funzione SccUncheckout
Questa funzione annulla un'operazione di estrazione precedente, ripristinando lo stato del contenuto del file o dei file selezionati prima dell'estrazione. Tutte le modifiche apportate al file dopo l'estrazione vengono perse.

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

 nFile

[in] Numero di file specificati nella `lpFileNames` matrice.

 lpFileNames

[in] Matrice di nomi di percorsi locali completi dei file per i quali annullare un'estrazione.

 fOpzioni

[in] Flag di comando (non usati).

 pvOptions

[in] Opzioni specifiche del plug-in del controllo del codice sorgente.

## <a name="return-value"></a>Valore restituito
 È previsto che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituirà uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|L'estrazione dell'annullamento è stata completata.|
|SCC_E_FILENOTCONTROLLED|Il file selezionato non è sotto il controllo del codice sorgente.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di problemi di connessione. È consigliabile eseguire un nuovo tentativo.|
|SCC_E_NONSPECIFICERROR|Errore non specifico. L'estrazione dell'annullamento non è riuscita.|
|SCC_E_NOTCHECKEDOUT|Il file non è estratto dall'utente.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|
|SCC_E_PROJNOTOPEN|Il progetto non è stato aperto dal controllo del codice sorgente.|
|SCC_I_OPERATIONCANCELED|L'operazione è stata annullata prima del completamento.|

## <a name="remarks"></a>Commenti
 Dopo questa operazione, i flag e verranno entrambi cancellati per i file in cui è stata eseguita `SCC_STATUS_CHECKEDOUT` `SCC_STATUS_MODIFIED` l'estrazione dell'annullamento.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
