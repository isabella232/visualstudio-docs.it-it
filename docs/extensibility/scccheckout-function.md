---
title: Funzione SccCheckout | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCheckout
helpviewer_keywords:
- SccCheckout function
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e5160a2600a8eb3250702dd0836d812b668a3d1b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333881"
---
# <a name="scccheckout-function"></a>Funzione SccCheckout
Dato un elenco di nomi completi dei file, questa funzione li estrae nell'unità locale. Il commento viene applicata a tutti i file in corso l'estrazione. L'argomento commento può essere un `null` stringa.

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

[in] La struttura del contesto plug-in del controllo origine.

 hWnd

[in] Handle per la finestra dell'IDE che il plug-in del controllo del codice sorgente è possibile utilizzare come padre per le finestre di dialogo che fornisce.

 nFiles

[in] Numero di file selezionati da estrarre.

 lpFileNames

[in] Matrice di nomi di percorso locale completo dei file da estrarre.

 lpComment

[in] Commento da applicare a ognuno dei file selezionati in corso l'estrazione.

 fOptions

[in] Flag di comando (vedere [flag di bit usati da comandi specifici](../extensibility/bitflags-used-by-specific-commands.md)).

 pvOptions

[in] Opzioni specifiche plug-in controllo sorgente.

## <a name="return-value"></a>Valore restituito
 Implementazione di plug-in del controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:

|Value|Descrizione|
|-----------|-----------------|
|SCC_OK|Check-out è stato completato.|
|SCC_E_FILENOTCONTROLLED|Il file selezionato non è incluso nel controllo del codice sorgente.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete. È consigliabile un nuovo tentativo.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|
|SCC_E_NONSPECIFICERROR|Errore non specifico. Il file non è stato estratto.|
|SCC_E_ALREADYCHECKEDOUT|L'utente ha già estratto il file.|
|SCC_E_FILEISLOCKED|Il file è bloccato, che vieta la creazione di nuove versioni.|
|SCC_E_FILEOUTEXCLUSIVE|Un altro utente ha eseguito un'estrazione esclusiva su questo file.|
|SCC_I_OPERATIONCANCELED|L'operazione è stata annullata prima del completamento.|

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in origine controllo](../extensibility/source-control-plug-in-api-functions.md)
- [Flag di bit usati da comandi specifici](../extensibility/bitflags-used-by-specific-commands.md)