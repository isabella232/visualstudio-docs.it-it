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
ms.openlocfilehash: 4d50b321f96b6759d95a6d923222e5e0a92b2ee3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66338465"
---
# <a name="sccuncheckout-function"></a>Funzione SccUncheckout
Questa funzione Annulla un'operazione di estrazione precedente, ripristinando in questo modo il contenuto del file selezionato o dei file lo stato precedente l'estrazione. Tutte le modifiche apportate al file dopo l'estrazione andranno perdute.

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

[in] La struttura del contesto plug-in del controllo origine.

 hWnd

[in] Handle per la finestra dell'IDE che il plug-in del controllo del codice sorgente è possibile utilizzare come padre per le finestre di dialogo che fornisce.

 nFiles

[in] Numero di file specificato per il `lpFileNames` matrice.

 lpFileNames

[in] Matrice di nomi di percorso locale completo dei file per il quale annullare un'estrazione.

 fOptions

[in] Flag di comando (non usato).

 pvOptions

[in] Opzioni specifiche plug-in controllo sorgente.

## <a name="return-value"></a>Valore restituito
 Implementazione di plug-in del controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:

|Value|Descrizione|
|-----------|-----------------|
|SCC_OK|Annullamento estrazione riuscito.|
|SCC_E_FILENOTCONTROLLED|Il file selezionato non è incluso nel controllo del codice sorgente.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete. È consigliabile un nuovo tentativo.|
|SCC_E_NONSPECIFICERROR|Errore non specifico. Annulla estrazione non è riuscita.|
|SCC_E_NOTCHECKEDOUT|L'utente non è disponibile il file estratto.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|
|SCC_E_PROJNOTOPEN|Il progetto non è stato aperto dal controllo del codice sorgente.|
|SCC_I_OPERATIONCANCELED|L'operazione è stata annullata prima del completamento.|

## <a name="remarks"></a>Note
 Dopo questa operazione, il `SCC_STATUS_CHECKEDOUT` e `SCC_STATUS_MODIFIED` flag verranno cancellati per i file in cui è stato eseguito l'annullamento dell'estrazione.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)