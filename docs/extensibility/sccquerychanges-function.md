---
title: Funzione SccQueryChanges | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryChanges
helpviewer_keywords:
- SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ec335d808c287decb75bf759d5a3795d98962579
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80700488"
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

in Numero di file nella `lpFileNames` matrice.

 lpFileNames

in Matrice di nomi di file per cui ottenere informazioni.

 pfnCallback

in Funzione di callback da chiamare per ogni nome di file nell'elenco. per informazioni dettagliate, vedere [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) .

 pvCallerData

in Valore che verrà passato senza modifiche alla funzione di callback.

## <a name="return-value"></a>Valore restituito
 Si prevede che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituisca uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Il processo di query è stato completato correttamente.|
|SCC_E_PROJNOTOPEN|Il progetto non è stato aperto nel controllo del codice sorgente.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di conflitto.|
|SCC_E_NONSPECIFICERROR|Si è verificato un errore non specificato o generale.|

## <a name="remarks"></a>Osservazioni
 Le modifiche sottoposte a query sono relative allo spazio dei nomi: in particolare, ridenominazione, aggiunta e rimozione di un file.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)
- [Codici errore](../extensibility/error-codes.md)
