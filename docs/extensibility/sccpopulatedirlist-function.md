---
title: Funzione SccPopulateDirList | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: eac3973bf28a14340b720a51fc291b914822f3d1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836917"
---
# <a name="sccpopulatedirlist-function"></a>Funzione SccPopulateDirList
Questa funzione determina quali directory e, facoltativamente, i file vengono archiviati nel controllo del codice sorgente, dato un elenco di directory da esaminare.

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccPopulateDirList(
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

in Puntatore al contesto del plug-in del controllo del codice sorgente.

 nDirs

in Numero di percorsi di directory nella `lpDirPaths` matrice.

 lpDirPaths

in Matrice di percorsi di directory da esaminare.

 pfnPopulate

in Funzione di callback da chiamare per ogni percorso di directory e (facoltativamente) nomefile in `lpDirPaths` (vedere [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) per informazioni dettagliate).

 pvCallerData

in Valore che deve essere passato senza modifiche alla funzione di callback.

 fOptions

in Combinazione di valori che controllano il modo in cui vengono elaborate le directory. vedere la sezione "flag PopulateDirList" di [flag utilizzata da comandi specifici](../extensibility/bitflags-used-by-specific-commands.md) per i valori possibili.

## <a name="return-value"></a>Valore restituito
 Si prevede che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituisca uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|L'operazione è stata completata.|
|SCC_E_UNKNOWNERROR|Si è verificato un errore.|

## <a name="remarks"></a>Commenti
 Solo le directory e (facoltativamente) i nomi di file effettivamente presenti nel repository del controllo del codice sorgente vengono passati alla funzione di callback.

## <a name="see-also"></a>Vedi anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [Flag di bit usati da comandi specifici](../extensibility/bitflags-used-by-specific-commands.md)
- [POPLISTFUNC](../extensibility/popdirlistfunc.md)
- [Codici errore](../extensibility/error-codes.md)
