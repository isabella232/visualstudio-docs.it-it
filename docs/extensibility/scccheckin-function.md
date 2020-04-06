---
title: Funzione SccCheckin . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCheckin
helpviewer_keywords:
- SccCheckin function
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a5ba512642e1a63d9d39856f96194d717583d44f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701188"
---
# <a name="scccheckin-function"></a>SccCheckin (funzione)
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

[in] Struttura di contesto del plug-in del controllo del codice sorgente.

 hWnd

[in] Un handle per la finestra dell'IDE che il plug-in SCC può utilizzare come elemento padre per tutte le finestre di dialogo che fornisce.

 nFile

[in] Numero di file selezionati per l'estrazione.

 LpNomidi File

[in] Matrice di nomi di percorso locali completi dei file da archiviare.

 LpCommento

[in] Commento da applicare a ciascuno dei file selezionati da archiviare. Questo parametro è `NULL` se il plug-in del controllo del codice sorgente deve richiedere un commento.

 fOpzioni

[in] Flag di comando, `SCC_KEEP_CHECKEDOUT`0 o .

 PvOpzioni

[in] Opzioni specifiche del plug-in SCC.

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei seguenti valori:

|valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Il file è stato archiviato correttamente.|
|SCC_E_FILENOTCONTROLLED|Il file selezionato non è nel controllo del codice sorgente.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di contesa. È consigliabile eseguire un nuovo tentativo.|
|SCC_E_NONSPECIFICERROR|Errore non specifico. Il file non è stato archiviato.|
|SCC_E_NOTCHECKEDOUT|L'utente non ha estratto il file, quindi non può archiviarlo.|
|SCC_E_CHECKINCONFLICT|Impossibile eseguire l'archiviazione perché:<br /><br /> - Un altro utente `bAutoReconcile` ha effettuato l'accesso in anticipo ed era false.<br /><br /> -oppure-<br /><br /> - L'unione automatica non può essere eseguita (ad esempio, quando i file sono binari).|
|SCC_E_VERIFYMERGE|Il file è stato automaticamente unito ma non è stato archiviato nella verifica dell'utente in sospeso.|
|SCC_E_FIXMERGE|Il file è stato unito automaticamente ma non è stato archiviato a causa di un conflitto di unione che deve essere risolto manualmente.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|
|SCC_I_OPERATIONCANCELED|L'operazione è stata annullata prima del completamento.|
|SCC_I_RELOADFILE|Un file o un progetto deve essere ricaricato.|
|SCC_E_FILENOTEXIST|File locale non trovato.|

## <a name="remarks"></a>Osservazioni
 Il commento si applica a tutti i file archiviati. L'argomento comment `null` può essere una stringa, nel qual caso il plug-in del controllo del codice sorgente può richiedere all'utente una stringa di commento per ogni file.

 È `fOptions` possibile dare all'argomento `SCC_KEEP_CHECKEDOUT` un valore del flag per indicare l'intenzione dell'utente di archiviare il file ed estrarlo nuovamente.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
