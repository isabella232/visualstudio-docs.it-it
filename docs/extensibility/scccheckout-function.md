---
title: Funzione SccCheckout . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCheckout
helpviewer_keywords:
- SccCheckout function
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ed809e33a80bf2903c88550e97b28b1e0178bcd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701098"
---
# <a name="scccheckout-function"></a>SccCheckout (funzione)
Dato un elenco di nomi di file completi, questa funzione li estrae nell'unità locale. Il commento si applica a tutti i file estratti. L'argomento comment `null` può essere una stringa.

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

[in] Struttura di contesto del plug-in del controllo del codice sorgente.

 hWnd

[in] Un handle per la finestra dell'IDE che il plug-in del controllo del codice sorgente può utilizzare come elemento padre per tutte le finestre di dialogo che fornisce.

 nFile

[in] Numero di file selezionati per l'estrazione.

 LpNomidi File

[in] Matrice di nomi di percorso locali completi dei file da estrarre.

 LpCommento

[in] Commento da applicare a ciascuno dei file selezionati da estrarre.

 fOpzioni

[in] Flag di comando (vedere [Flag di bit utilizzati da comandi specifici).](../extensibility/bitflags-used-by-specific-commands.md)

 PvOpzioni

[in] Opzioni specifiche del plug-in del controllo del codice sorgente.

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei seguenti valori:

|valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Il check-out è andato a buon fine.|
|SCC_E_FILENOTCONTROLLED|Il file selezionato non è nel controllo del codice sorgente.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di contesa. È consigliabile eseguire un nuovo tentativo.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|
|SCC_E_NONSPECIFICERROR|Errore non specifico. Il file non è stato estratto.|
|SCC_E_ALREADYCHECKEDOUT|L'utente ha già estratto il file.|
|SCC_E_FILEISLOCKED|Il file è bloccato, vietando la creazione di nuove versioni.|
|SCC_E_FILEOUTEXCLUSIVE|Un altro utente ha fatto un checkout esclusivo su questo file.|
|SCC_I_OPERATIONCANCELED|L'operazione è stata annullata prima del completamento.|

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [Flag di bit utilizzati da comandi specifici](../extensibility/bitflags-used-by-specific-commands.md)
