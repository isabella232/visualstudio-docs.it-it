---
title: Funzione SccUncheckout . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUncheckout
helpviewer_keywords:
- SccUncheckout function
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4317133b2f215e0f9af447e5c042785561231f63
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700242"
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

[in] Struttura di contesto del plug-in del controllo del codice sorgente.

 hWnd

[in] Un handle per la finestra dell'IDE che il plug-in del controllo del codice sorgente può utilizzare come elemento padre per tutte le finestre di dialogo che fornisce.

 nFile

[in] Numero di file `lpFileNames` specificati nella matrice.

 LpNomidi File

[in] Matrice di nomi di percorso locali completi di file per i quali annullare un'estrazione.

 fOpzioni

[in] Flag di comando (non utilizzati).

 PvOpzioni

[in] Opzioni specifiche del plug-in del controllo del codice sorgente.

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei seguenti valori:

|valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Annullamento dell'estrazione riuscito.|
|SCC_E_FILENOTCONTROLLED|Il file selezionato non è nel controllo del codice sorgente.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di contesa. È consigliabile eseguire un nuovo tentativo.|
|SCC_E_NONSPECIFICERROR|Errore non specifico. Annullamento dell'estrazione non riuscita.|
|SCC_E_NOTCHECKEDOUT|L'utente non ha estratto il file.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|
|SCC_E_PROJNOTOPEN|Il progetto non è stato aperto dal controllo del codice sorgente.|
|SCC_I_OPERATIONCANCELED|L'operazione è stata annullata prima del completamento.|

## <a name="remarks"></a>Osservazioni
 Dopo questa operazione, i `SCC_STATUS_CHECKEDOUT` flag e `SCC_STATUS_MODIFIED` verranno entrambi cancellati per i file in cui è stata eseguita l'annullamento dell'estrazione.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
