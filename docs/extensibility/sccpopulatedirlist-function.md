---
title: SccPopulateDirList (funzione) . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ac1c51ac694acadd2efb0cd7d1c5a3f1d66ebc1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700559"
---
# <a name="sccpopulatedirlist-function"></a>Funzione SccPopulateDirList
Questa funzione determina quali directory e (facoltativamente) i file vengono archiviati nel controllo del codice sorgente, dato un elenco di directory da esaminare.

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccPopulateDirList(
   LPVOID        pContext,
   LONG          nDirs,
   LPCSTR*       lpDirPaths,
   POPDIRLISTFUNCpfnPopulate,
   LPVOID        pvCallerData,
   LONG          fOptions
);
```

#### <a name="parameters"></a>Parametri
 pContext

[in] Puntatore di contesto del plug-in del controllo del codice sorgente.

 nDirs (informazioni in stato infondi)

[in] Numero di percorsi `lpDirPaths` di directory nella matrice.

 LpDirPeri

[in] Matrice di percorsi di directory da esaminare.

 pfnPop

[in] Funzione di callback da chiamare per ogni percorso `lpDirPaths` di directory e (facoltativamente) nome file in (vedere [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) per i dettagli).

 pvCallerData (informazioni in fibra con i dati)

[in] Valore che deve essere passato invariato alla funzione di callback.

 fOpzioni

[in] Combinazione di valori che controllano la modalità di elaborazione delle directory (vedere la sezione "Flag PopOfrList" di Flag di [bit utilizzati da comandi specifici](../extensibility/bitflags-used-by-specific-commands.md) per i valori possibili).

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei seguenti valori:

|valore|Descrizione|
|-----------|-----------------|
|SCC_OK|L'operazione è stata completata correttamente.|
|SCC_E_UNKNOWNERROR|Si è verificato un errore.|

## <a name="remarks"></a>Osservazioni
 Solo le directory e (facoltativamente) i nomi di file effettivamente presenti nel repository del controllo del codice sorgente vengono passati alla funzione di callback.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [Flag di bit usati da comandi specifici](../extensibility/bitflags-used-by-specific-commands.md)
- [POPLISTFUNC](../extensibility/popdirlistfunc.md)
- [Codici di errore](../extensibility/error-codes.md)
