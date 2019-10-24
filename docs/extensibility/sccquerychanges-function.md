---
title: Funzione SccQueryChanges | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryChanges
helpviewer_keywords:
- SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 617f07a11f92ab65f079c7d1b41773494e3d0c8b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720858"
---
# <a name="sccquerychanges-function"></a>Funzione SccQueryChanges
Questa funzione enumera un elenco di file specificato, fornendo informazioni sulle modifiche dei nomi per ogni file tramite una funzione di callback.

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccQueryChanges(
   LPVOID           pContext,
   LONG             nFiles,
   LPCSTR*          lpFileNames,
   QUERYCHANGESFUNC pfnCallback,
   LPVOID           pvCallerData
);
```

#### <a name="parameters"></a>Parametri
 pContext

in Puntatore al contesto del plug-in del controllo del codice sorgente.

 nFile

in Numero di file in `lpFileNames` matrice.

 lpFileNames

in Matrice di nomi di file per cui ottenere informazioni.

 pfnCallback

in Funzione di callback da chiamare per ogni nome di file nell'elenco. per informazioni dettagliate, vedere [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) .

 pvCallerData

in Valore che verrà passato senza modifiche alla funzione di callback.

## <a name="return-value"></a>Valore restituito
 Si prevede che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituisca uno dei valori seguenti:

|Value|Descrizione|
|-----------|-----------------|
|SCC_OK|Il processo di query è stato completato correttamente.|
|SCC_E_PROJNOTOPEN|Il progetto non è stato aperto nel controllo del codice sorgente.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di conflitto.|
|SCC_E_NONSPECIFICERROR|Si è verificato un errore non specificato o generale.|

## <a name="remarks"></a>Note
 Le modifiche sottoposte a query sono relative allo spazio dei nomi: in particolare, ridenominazione, aggiunta e rimozione di un file.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)
- [Codici di errore](../extensibility/error-codes.md)