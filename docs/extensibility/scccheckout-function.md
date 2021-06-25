---
description: Dato un elenco di nomi di file completi, questa funzione li estrazione nell'unità locale.
title: Funzione SccCheckout | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccCheckout
helpviewer_keywords:
- SccCheckout function
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 72d36ccaf5c6dcddb6730f52b0ce1c3074c605a7
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904721"
---
# <a name="scccheckout-function"></a>Funzione SccCheckout
Dato un elenco di nomi di file completi, questa funzione li estrazione nell'unità locale. Il commento si applica a tutti i file estratti. L'argomento comment può essere una `null` stringa.

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccCheckout (
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LPCSTR    lpComment,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Parametri
 pvContext

[in] Struttura del contesto del plug-in del controllo del codice sorgente.

 hWnd

[in] Handle per la finestra IDE che il plug-in del controllo del codice sorgente può usare come elemento padre per qualsiasi finestra di dialogo fornita.

 nFiles

[in] Numero di file selezionati per l'estrazione.

 lpFileNames

[in] Matrice di nomi di percorsi locali completi dei file da estrazione.

 lpComment

[in] Commento da applicare a ognuno dei file selezionati estratti.

 fOptions

[in] Flag di comando (vedere [Flag di bit usati da comandi specifici).](../extensibility/bitflags-used-by-specific-commands.md)

 pvOptions

[in] Opzioni specifiche del plug-in del controllo del codice sorgente.

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|L'estrazione è riuscita.|
|SCC_E_FILENOTCONTROLLED|Il file selezionato non è sotto il controllo del codice sorgente.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di problemi di connessione. È consigliabile riprovare.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|
|SCC_E_NONSPECIFICERROR|Errore non specifico. Il file non è stato estratto.|
|SCC_E_ALREADYCHECKEDOUT|Il file è già estratto dall'utente.|
|SCC_E_FILEISLOCKED|Il file è bloccato e impedisce la creazione di nuove versioni.|
|SCC_E_FILEOUTEXCLUSIVE|Un altro utente ha eseguito un'estrazione esclusiva su questo file.|
|SCC_I_OPERATIONCANCELED|L'operazione è stata annullata prima del completamento.|

## <a name="see-also"></a>Vedere anche
- [Funzioni API plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [Flag di bit usati da comandi specifici](../extensibility/bitflags-used-by-specific-commands.md)
