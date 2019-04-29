---
title: Funzione SccPopulateDirList | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a74d6008db15cc8cd89daf4882d8952006dc547d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62433084"
---
# <a name="sccpopulatedirlist-function"></a>Funzione SccPopulateDirList
Questa funzione determina le directory e, facoltativamente, i file vengono archiviati nel controllo del codice sorgente, dato un elenco di directory da esaminare.

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

[in] Il puntatore di contesto del plug-in controllo di origine.

 nDirs

[in] Numero di percorsi di directory nella `lpDirPaths` matrice.

 lpDirPaths

[in] Matrice di percorsi di directory da esaminare.

 pfnPopulate

[in] Funzione di callback da chiamare per ogni nome del file nel percorso di directory e (facoltativamente) `lpDirPaths` (vedere [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) per informazioni dettagliate).

 pvCallerData

[in] Valore che deve essere passato alla funzione di callback invariato.

 fOptions

[in] Una combinazione di valori che controllano il modo in cui vengono elaborate le directory (vedere la sezione "PopulateDirList flags" [flag di bit usati da comandi specifici](../extensibility/bitflags-used-by-specific-commands.md) per i valori possibili).

## <a name="return-value"></a>Valore restituito
 Implementazione di plug-in del controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:

|Value|Descrizione|
|-----------|-----------------|
|SCC_OK|L'operazione è stata completata.|
|SCC_E_UNKNOWNERROR|Si è verificato un errore.|

## <a name="remarks"></a>Note
 Solo le directory e, facoltativamente, i nomi di file che sono effettivamente nel repository del controllo del codice sorgente vengono passati alla funzione di callback.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [Flag di bit usati da comandi specifici](../extensibility/bitflags-used-by-specific-commands.md)
- [POPLISTFUNC](../extensibility/popdirlistfunc.md)
- [Codici di errore](../extensibility/error-codes.md)