---
title: Funzione SccCheckin | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCheckin
helpviewer_keywords:
- SccCheckin function
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a68b03f594ad686f2b3e23aab52cabfe4fa5d92a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952109"
---
# <a name="scccheckin-function"></a>SccCheckin (funzione)
Questa funzione archivia i file precedentemente estratti nel sistema di controllo del codice sorgente, archiviando le modifiche e creando una nuova versione. Questa funzione viene chiamata con un conteggio e una matrice di nomi dei file da archiviare.

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

in Struttura del contesto del plug-in del controllo del codice sorgente.

 hWnd

in Handle per la finestra IDE che il plug-in SCC può utilizzare come elemento padre per tutte le finestre di dialogo fornite.

 nFile

in Numero di file selezionati da archiviare.

 lpFileNames

in Matrice di nomi di percorso locale completi dei file da archiviare.

 lpComment

in Commento da applicare a ognuno dei file selezionati che vengono archiviati. Questo parametro è `NULL` se il plug-in del controllo del codice sorgente deve richiedere un commento.

 fOptions

in Flag di comando, ovvero 0 o `SCC_KEEP_CHECKEDOUT` .

 pvOptions

in Opzioni specifiche del plug-in SCC.

## <a name="return-value"></a>Valore restituito
 Si prevede che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituisca uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Il file è stato archiviato correttamente.|
|SCC_E_FILENOTCONTROLLED|Il file selezionato non è sotto il controllo del codice sorgente.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di conflitto. È consigliabile eseguire un nuovo tentativo.|
|SCC_E_NONSPECIFICERROR|Errore non specifico. Il file non è stato archiviato.|
|SCC_E_NOTCHECKEDOUT|L'utente non ha estratto il file, quindi non può archiviarlo.|
|SCC_E_CHECKINCONFLICT|Impossibile eseguire l'archiviazione perché:<br /><br /> -Un altro utente ha eseguito l'check-in avanti e il valore `bAutoReconcile` è false.<br /><br /> -oppure-<br /><br /> -Non è possibile eseguire l'Unione automatica (ad esempio, quando i file sono binari).|
|SCC_E_VERIFYMERGE|Il file è stato sottoposto a merge automatico ma non è stato archiviato per la verifica degli utenti in sospeso.|
|SCC_E_FIXMERGE|Il file è stato unito automaticamente ma non è stato archiviato a causa di un conflitto di merge che deve essere risolto manualmente.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|
|SCC_I_OPERATIONCANCELED|Operazione annullata prima del completamento.|
|SCC_I_RELOADFILE|È necessario ricaricare un file o un progetto.|
|SCC_E_FILENOTEXIST|Il file locale non è stato trovato.|

## <a name="remarks"></a>Commenti
 Il commento si applica a tutti i file in fase di verifica. L'argomento comment può essere una `null` stringa, nel qual caso il plug-in del controllo del codice sorgente può richiedere all'utente una stringa di commento per ogni file.

 All' `fOptions` argomento può essere assegnato un valore del `SCC_KEEP_CHECKEDOUT` flag per indicare l'intento dell'utente di controllare il file ed estrarlo di nuovo.

## <a name="see-also"></a>Vedi anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
