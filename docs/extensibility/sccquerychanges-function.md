---
description: Questa funzione enumera un determinato elenco di file, fornendo informazioni sulle modifiche dei nomi per ogni file tramite una funzione di callback.
title: Funzione SccQueryChanges | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccQueryChanges
helpviewer_keywords:
- SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f93ed14671995502356ae4a19664b14bbd32ce7b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900473"
---
# <a name="sccquerychanges-function"></a>Funzione SccQueryChanges
Questa funzione enumera un determinato elenco di file, fornendo informazioni sulle modifiche dei nomi per ogni file tramite una funzione di callback.

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccQueryChanges(
   LPVOID           pContext,
   LONG             nFiles,
   LPCSTR*          lpFileNames,
   QUERYCHANGESFUNC pfnCallback,
   LPVOID           pvCallerData
);
```

#### <a name="parameters"></a>Parametri
 pContext

[in] Puntatore al contesto del plug-in del controllo del codice sorgente.

 nFiles

[in] Numero di file nella `lpFileNames` matrice.

 lpFileNames

[in] Matrice di nomi di file su cui ottenere informazioni.

 pfnCallback

[in] Funzione di callback da chiamare per ogni nome di file nell'elenco.Per informazioni dettagliate, vedere [QUERYCHANGESFUNC.](../extensibility/querychangesfunc.md)

 pvCallerData

[in] Valore che verrà passato invariato alla funzione di callback.

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Il processo di query è stato completato correttamente.|
|SCC_E_PROJNOTOPEN|Il progetto non è stato aperto nel controllo del codice sorgente.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di problemi di connessione.|
|SCC_E_NONSPECIFICERROR|Si è verificato un errore generale o non specificato.|

## <a name="remarks"></a>Commenti
 Le modifiche di cui viene eseguita la query riguardano lo spazio dei nomi : in particolare, la ridenominazione, l'aggiunta e la rimozione di un file.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)
- [Codici errore](../extensibility/error-codes.md)
