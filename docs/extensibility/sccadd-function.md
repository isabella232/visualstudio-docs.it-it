---
description: Questa funzione aggiunge nuovi file al sistema di controllo del codice sorgente.
title: Funzione SccAdd | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccAdd
helpviewer_keywords:
- SccAdd function
ms.assetid: 545268f3-8e83-446a-a398-1a9db9e866e8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7f73a91f7f801ca89a633f1722e0c4d1183fb3dc
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904851"
---
# <a name="sccadd-function"></a>Funzione SccAdd
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

[in] Struttura del contesto del plug-in del controllo del codice sorgente.

 hWnd

[in] Handle per la finestra IDE che il plug-in del controllo del codice sorgente può usare come elemento padre per qualsiasi finestra di dialogo fornita.

 nFile

[in] Numero di file selezionati da aggiungere al progetto corrente, come specificato nella `lpFileNames` matrice.

 lpFileNames

[in] Matrice di nomi locali completi di file da aggiungere.

 lpComment

[in] Commento da applicare a tutti i file aggiunti.

 pfOptions

[in] Matrice di flag di comando, forniti per ogni file.

 pvOptions

[in] Opzioni specifiche del plug-in del controllo del codice sorgente.

## <a name="return-value"></a>Valore restituito
 È previsto che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituirà uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|L'operazione di aggiunta è stata completata.|
|SCC_E_FILEALREADYEXISTS|Il file selezionato è già in fase di controllo del codice sorgente.|
|SCC_E_TYPENOTSUPPORTED|Il tipo di file , ad esempio binario, non è supportato dal sistema di controllo del codice sorgente.|
|SCC_E_OPNOTSUPPORTED|Il sistema di controllo del codice sorgente non supporta questa operazione.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di problemi di connessione. È consigliabile eseguire un nuovo tentativo.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|
|SCC_E_NONSPECIFICERROR|Errore non specifico. aggiunta non eseguita.|
|SCC_I_OPERATIONCANCELED|L'operazione è stata annullata prima del completamento.|
|SCC_I_RELOADFILE|È necessario ricaricare un file o un progetto.|
|SCC_E_FILENOTEXIST|Impossibile trovare il file locale.|

## <a name="remarks"></a>Commenti
 I valori `fOptions` usuali vengono sostituiti in questo caso da una `pfOptions` matrice, , con una `LONG` specifica di opzione per ogni file. Questo perché il tipo di file può variare da file a file.

> [!NOTE]
> Non è possibile specificare entrambe `SCC_FILETYPE_TEXT` le opzioni e per lo stesso file, ma non è possibile `SCC_FILETYPE_BINARY` specificarne nessuna. L'impostazione di non corrisponde all'impostazione , nel qual caso il plug-in del controllo del codice sorgente rileva `SCC_FILETYPE_AUTO` automaticamente il tipo di file.

 Di seguito è riportato l'elenco dei flag usati nella `pfOptions` matrice:

|Opzione|Valore|Significato|
|------------|-----------|-------------|
|SCC_FILETYPE_AUTO|0x00|Il plug-in del controllo del codice sorgente deve rilevare il tipo di file.|
|SCC_FILETYPE_TEXT|0x01|Indica un file di testo ASCII.|
|SCC_FILETYPE_BINARY|0x02|Indica un tipo di file diverso dal testo ASCII.|
|SCC_ADD_STORELATEST|0x04|Archivia solo la copia più recente del file, senza delta.|
|SCC_FILETYPE_TEXT_ANSI|0x08|Considera il file come testo ANSI.|
|SCC_FILETYPE_UTF8|0x10|Considera il file come testo Unicode in formato UTF8.|
|SCC_FILETYPE_UTF16LE|0x20|Considera il file come testo Unicode in formato Utf16 Little Endian.|
|SCC_FILETYPE_UTF16BE|0x40|Considera il file come testo Unicode in formato Big Endian UTF16.|

## <a name="see-also"></a>Vedere anche
- [Funzioni API plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
