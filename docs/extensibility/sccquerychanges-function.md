---
title: Funzione SccQueryChanges . Documenti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700488"
---
# <a name="sccquerychanges-function"></a>Funzione SccQueryChanges
Questa funzione enumera un determinato elenco di file, fornendo informazioni sulle modifiche dei nomi per ogni file tramite una funzione di callback.

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

[in] Puntatore di contesto del plug-in del controllo del codice sorgente.

 nFile

[in] Numero di `lpFileNames` file nell'array.

 LpNomidi File

[in] Matrice di nomi di file per cui ottenere informazioni.

 pfnCallback

[in] Funzione di callback da chiamare per ogni nome di file nell'elenco (vedere [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) per i dettagli).

 pvCallerData (informazioni in fibra con i dati)

[in] Valore che verrà passato invariato alla funzione di callback.

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei seguenti valori:

|valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Il processo di query è stato completato correttamente.|
|SCC_E_PROJNOTOPEN|Il progetto non è stato aperto nel controllo del codice sorgente.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di contesa.|
|SCC_E_NONSPECIFICERROR|Si è verificato un errore non specificato o generale.|

## <a name="remarks"></a>Osservazioni
 Le modifiche sottoposte a query sono destinate allo spazio dei nomi, in particolare, la ridenominazione, l'aggiunta e la rimozione di un file.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)
- [Codici di errore](../extensibility/error-codes.md)
