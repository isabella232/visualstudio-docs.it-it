---
description: Questa funzione archivia i file estratti in precedenza nel sistema di controllo del codice sorgente, archiviando le modifiche e creando una nuova versione.
title: Funzione SccCheckin | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccCheckin
helpviewer_keywords:
- SccCheckin function
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 57871318596335544c518b948ec93680b07f6335
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122144587"
---
# <a name="scccheckin-function"></a>Funzione SccCheckin
Questa funzione archivia i file estratti in precedenza nel sistema di controllo del codice sorgente, archiviando le modifiche e creando una nuova versione. Questa funzione viene chiamata con un conteggio e una matrice di nomi dei file da archiviare.

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccCheckin (
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPSTR*    lpFileNames,
   LPCSTR    lpComment,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Parametri
 pvContext

[in] Struttura del contesto del plug-in del controllo del codice sorgente.

 hWnd

[in] Handle per la finestra IDE che il plug-in SCC può usare come elemento padre per qualsiasi finestra di dialogo fornita.

 nFile

[in] Numero di file selezionati da archiviare.

 lpFileNames

[in] Matrice di nomi di percorsi locali completi dei file da archiviare.

 lpComment

[in] Commento da applicare a ogni file selezionato archiviato. Questo parametro è `NULL` se il plug-in del controllo del codice sorgente deve richiedere un commento.

 fOpzioni

[in] Flag di comando, 0 o `SCC_KEEP_CHECKEDOUT` .

 pvOptions

[in] Opzioni specifiche del plug-in SCC.

## <a name="return-value"></a>Valore restituito
 È previsto che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituirà uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Il file è stato archiviato correttamente.|
|SCC_E_FILENOTCONTROLLED|Il file selezionato non è sotto il controllo del codice sorgente.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di problemi di connessione. È consigliabile eseguire un nuovo tentativo.|
|SCC_E_NONSPECIFICERROR|Errore non specifico. Il file non è stato archiviato.|
|SCC_E_NOTCHECKEDOUT|L'utente non ha estratto il file, pertanto non può archiviarlo.|
|SCC_E_CHECKINCONFLICT|Non è stato possibile eseguire il checkin perché:<br /><br /> - Un altro utente ha archiviato in anticipo ed `bAutoReconcile` è stato false.<br /><br /> -oppure-<br /><br /> - Non è possibile eseguire l'unione automatica, ad esempio quando i file sono binari.|
|SCC_E_VERIFYMERGE|Il file è stato unito automaticamente, ma non è stata archiviata la verifica utente in sospeso.|
|SCC_E_FIXMERGE|Il file è stato unito automaticamente ma non è stato archiviato a causa di un conflitto di unione che deve essere risolto manualmente.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|
|SCC_I_OPERATIONCANCELED|L'operazione è stata annullata prima del completamento.|
|SCC_I_RELOADFILE|È necessario ricaricare un file o un progetto.|
|SCC_E_FILENOTEXIST|Impossibile trovare il file locale.|

## <a name="remarks"></a>Commenti
 Il commento si applica a tutti i file archiviati. L'argomento comment può essere una stringa, nel qual caso il plug-in del controllo del codice sorgente può richiedere all'utente una stringa di commento `null` per ogni file.

 All'argomento può essere assegnato un valore del flag per indicare la finalità dell'utente di archiviare il file e `fOptions` `SCC_KEEP_CHECKEDOUT` di estrarlo di nuovo.

## <a name="see-also"></a>Vedi anche
- [Funzioni API plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
