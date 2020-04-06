---
title: Funzione SccAdd . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAdd
helpviewer_keywords:
- SccAdd function
ms.assetid: 545268f3-8e83-446a-a398-1a9db9e866e8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 23a6226b0d3cc2441a509c16b2e4672a766f3329
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701305"
---
# <a name="sccadd-function"></a>SccAdd (funzione)
Questa funzione aggiunge nuovi file al sistema di controllo del codice sorgente.

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccAdd(
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LPCSTR    lpComment,
   LONG*     pfOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Parametri
 pvContext

[in] Struttura di contesto del plug-in del controllo del codice sorgente.

 hWnd

[in] Un handle per la finestra dell'IDE che il plug-in del controllo del codice sorgente può utilizzare come elemento padre per tutte le finestre di dialogo che fornisce.

 nFile

[in] Numero di file selezionati per essere aggiunti al `lpFileNames` progetto corrente come indicato nella matrice.

 LpNomidi File

[in] Matrice di nomi locali completi dei file da aggiungere.

 LpCommento

[in] Commento da applicare a tutti i file aggiunti.

 PfOpzioni (Opzioni)

[in] Matrice di flag di comando, fornita in base al file.

 PvOpzioni

[in] Opzioni specifiche del plug-in del controllo del codice sorgente.

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei seguenti valori:

|valore|Descrizione|
|-----------|-----------------|
|SCC_OK|L'operazione di aggiunta ha avuto esito positivo.|
|SCC_E_FILEALREADYEXISTS|Il file selezionato è già nel controllo del codice sorgente.|
|SCC_E_TYPENOTSUPPORTED|Il tipo del file ( ad esempio, binario) non è supportato dal sistema di controllo del codice sorgente.|
|SCC_E_OPNOTSUPPORTED|Il sistema di controllo del codice sorgente non supporta questa operazione.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di contesa. È consigliabile eseguire un nuovo tentativo.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|
|SCC_E_NONSPECIFICERROR|Errore non specifico; aggiungere non eseguita.|
|SCC_I_OPERATIONCANCELED|L'operazione è stata annullata prima del completamento.|
|SCC_I_RELOADFILE|Un file o un progetto deve essere ricaricato.|
|SCC_E_FILENOTEXIST|File locale non trovato.|

## <a name="remarks"></a>Osservazioni
 I `fOptions` soliti sono sostituiti `pfOptions`qui da `LONG` una matrice, , con una specifica di opzione per file. Questo perché il tipo di file può variare da file a file.

> [!NOTE]
> Non è possibile `SCC_FILETYPE_TEXT` specificare entrambe le `SCC_FILETYPE_BINARY` opzioni per lo stesso file, ma non è possibile specificare nessuna delle due. L'impostazione di `SCC_FILETYPE_AUTO`nessuna delle due impostazioni equivale all'impostazione, nel qual caso il plug-in del controllo del codice sorgente rileva automaticamente il tipo di file.

 Di seguito è riportato `pfOptions` l'elenco dei flag utilizzati nella matrice:

|Opzione|valore|Significato|
|------------|-----------|-------------|
|SCC_FILETYPE_AUTO|0x00|Il plug-in del controllo del codice sorgente deve rilevare il tipo di file.|
|SCC_FILETYPE_TEXT|0x01|Indica un file di testo ASCII.|
|SCC_FILETYPE_BINARY|0x02|Indica un tipo di file diverso dal testo ASCII.|
|SCC_ADD_STORELATEST|0x04|Memorizza solo la copia più recente del file, senza delta.|
|SCC_FILETYPE_TEXT_ANSI|0x08|Considera il file come testo ANSI.|
|SCC_FILETYPE_UTF8|0x10|Considera il file come testo Unicode in formato UTF8.|
|SCC_FILETYPE_UTF16LE|0x20|Considera il file come testo Unicode in formato UTF16 Little Endian.|
|SCC_FILETYPE_UTF16BE|0x40|Considera il file come testo Unicode in formato UTF16 Big Endian.|

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
