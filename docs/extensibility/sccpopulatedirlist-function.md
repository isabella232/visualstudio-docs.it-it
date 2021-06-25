---
description: Questa funzione determina quali directory e (facoltativamente) i file vengono archiviati nel controllo del codice sorgente, dato un elenco di directory da esaminare.
title: Funzione SccPopulateDirList | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bf2620ff42106be7c858c5104dbf9cb2521252ab
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902358"
---
# <a name="sccpopulatedirlist-function"></a>Funzione SccPopulateDirList
Questa funzione determina quali directory e (facoltativamente) i file vengono archiviati nel controllo del codice sorgente, dato un elenco di directory da esaminare.

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

[in] Puntatore al contesto del plug-in del controllo del codice sorgente.

 nDirs

[in] Numero di percorsi di directory nella `lpDirPaths` matrice.

 lpDirPaths

[in] Matrice di percorsi di directory da esaminare.

 pfnPopulate

[in] Funzione di callback da chiamare per ogni percorso di directory e (facoltativamente) nome file in (per informazioni dettagliate, `lpDirPaths` [vedere POPDIRLISTFUNC).](../extensibility/popdirlistfunc.md)

 pvCallerData

[in] Valore da passare invariato alla funzione di callback.

 fOpzioni

[in] Combinazione di valori che controllano la modalità di elaborazione delle directory (vedere la sezione "Flag PopulateDirList" di [Bitflags Usati](../extensibility/bitflags-used-by-specific-commands.md) da comandi specifici per i valori possibili).

## <a name="return-value"></a>Valore restituito
 È previsto che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituirà uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|L'operazione è stata completata correttamente.|
|SCC_E_UNKNOWNERROR|Si è verificato un errore.|

## <a name="remarks"></a>Commenti
 Solo le directory e (facoltativamente) i nomi di file effettivamente presenti nel repository del controllo del codice sorgente vengono passati alla funzione di callback.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [Flag di bit usati da comandi specifici](../extensibility/bitflags-used-by-specific-commands.md)
- [POPLISTFUNC](../extensibility/popdirlistfunc.md)
- [Codici errore](../extensibility/error-codes.md)
