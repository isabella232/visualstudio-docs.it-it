---
title: Funzione SccUncheckout | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUncheckout
helpviewer_keywords:
- SccUncheckout function
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e35d7287d8fc12100da9ba3b8383d8e92cee73d4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720528"
---
# <a name="sccuncheckout-function"></a>Funzione SccUncheckout
Questa funzione Annulla un'operazione di estrazione precedente, ripristinando in tal modo il contenuto del file o dei file selezionati nello stato precedente all'estrazione. Tutte le modifiche apportate al file dall'estrazione vengono perse.

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

in Struttura del contesto del plug-in del controllo del codice sorgente.

 hWnd

in Handle per la finestra IDE che il plug-in del controllo del codice sorgente può utilizzare come elemento padre per tutte le finestre di dialogo fornite.

 nFile

in Numero di file specificati nella matrice `lpFileNames`.

 lpFileNames

in Matrice di nomi di percorsi locali completi dei file per i quali annullare un'estrazione.

 fOptions

in Flag di comando (non utilizzati).

 pvOptions

in Opzioni specifiche del plug-in del controllo del codice sorgente.

## <a name="return-value"></a>Valore restituito
 Si prevede che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituisca uno dei valori seguenti:

|Value|Descrizione|
|-----------|-----------------|
|SCC_OK|Annullamento dell'estrazione riuscito.|
|SCC_E_FILENOTCONTROLLED|Il file selezionato non è sotto il controllo del codice sorgente.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di conflitto. È consigliabile eseguire un nuovo tentativo.|
|SCC_E_NONSPECIFICERROR|Errore non specifico. Annullamento dell'estrazione non riuscito.|
|SCC_E_NOTCHECKEDOUT|L'utente non ha estratto il file.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|
|SCC_E_PROJNOTOPEN|Il progetto non è stato aperto dal controllo del codice sorgente.|
|SCC_I_OPERATIONCANCELED|L'operazione è stata annullata prima del completamento.|

## <a name="remarks"></a>Note
 Dopo questa operazione, i flag `SCC_STATUS_CHECKEDOUT` e `SCC_STATUS_MODIFIED` verranno cancellati per i file in cui è stata eseguita l'operazione di annullamento.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)