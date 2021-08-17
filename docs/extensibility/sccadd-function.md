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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 7e8d671483f2e141aa2971fca6a60bdaf433db21d10ce829617dc55c25a3de01
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121388136"
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

 nFiles

[in] Numero di file selezionati da aggiungere al progetto corrente, come specificato nella `lpFileNames` matrice .

 lpFileNames

[in] Matrice di nomi locali completi dei file da aggiungere.

 lpComment

[in] Commento da applicare a tutti i file aggiunti.

 pfOptions

[in] Matrice di flag di comando, fornita per ogni file.

 pvOptions

[in] Opzioni specifiche del plug-in del controllo del codice sorgente.

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|L'operazione di aggiunta è riuscita.|
|SCC_E_FILEALREADYEXISTS|Il file selezionato è già nel controllo del codice sorgente.|
|SCC_E_TYPENOTSUPPORTED|Il tipo di file ,ad esempio binary, non è supportato dal sistema di controllo del codice sorgente.|
|SCC_E_OPNOTSUPPORTED|Il sistema di controllo del codice sorgente non supporta questa operazione.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di problemi di connessione. È consigliabile riprovare.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|
|SCC_E_NONSPECIFICERROR|Errore non specifico; L'aggiunta non viene eseguita.|
|SCC_I_OPERATIONCANCELED|L'operazione è stata annullata prima del completamento.|
|SCC_I_RELOADFILE|È necessario ricaricare un file o un progetto.|
|SCC_E_FILENOTEXIST|File locale non trovato.|

## <a name="remarks"></a>Commenti
 I valori `fOptions` consueti vengono sostituiti da una matrice, `pfOptions` , con una specifica di opzione per ogni `LONG` file. Questo perché il tipo di file può variare da file a file.

> [!NOTE]
> Non è valido specificare entrambe le opzioni e per lo stesso file, ma `SCC_FILETYPE_TEXT` non è possibile `SCC_FILETYPE_BINARY` specificarne nessuna. L'impostazione di nessuno dei due è uguale all'impostazione di , nel qual caso il plug-in del controllo del codice `SCC_FILETYPE_AUTO` sorgente rileva automaticamente il tipo di file.

 Di seguito è riportato l'elenco dei flag usati nella `pfOptions` matrice :

|Opzione|Valore|Significato|
|------------|-----------|-------------|
|SCC_FILETYPE_AUTO|0x00|Il plug-in del controllo del codice sorgente deve rilevare il tipo di file.|
|SCC_FILETYPE_TEXT|0x01|Indica un file di testo ASCII.|
|SCC_FILETYPE_BINARY|0x02|Indica un tipo di file diverso dal testo ASCII.|
|SCC_ADD_STORELATEST|0x04|Archivia solo la copia più recente del file, senza delta.|
|SCC_FILETYPE_TEXT_ANSI|0x08|Considera il file come testo ANSI.|
|SCC_FILETYPE_UTF8|0x10|Considera il file come testo Unicode in formato UTF8.|
|SCC_FILETYPE_UTF16LE|0x20|Considera il file come testo Unicode in formato UTF16 Little Endian.|
|SCC_FILETYPE_UTF16BE|0x40|Considera il file come testo Unicode in formato UTF16 Big Endian.|

## <a name="see-also"></a>Vedi anche
- [Funzioni API plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
