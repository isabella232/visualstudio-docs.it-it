---
title: Funzione SccGetEvents | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetEvents
helpviewer_keywords:
- SccGetEvents function
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4502dd1cdf5cb23f317cd29bee74460c5911482c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965161"
---
# <a name="sccgetevents-function"></a>SccGetEvents (funzione)
Questa funzione recupera un evento di stato in coda.

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccGetEvents (
   LPVOID pvContext,
   LPSTR  lpFileName,
   LPLONG lpStatus,
   LPLONG pnEventsRemaining
);
```

### <a name="parameters"></a>Parametri
 pvContext

in Struttura del contesto del plug-in del controllo del codice sorgente.

 lpFileName

[in, out] Buffer in cui il plug-in del controllo del codice sorgente inserisce il nome file restituito (fino a _MAX_PATH caratteri).

 lpStatus

[in, out] Restituisce il codice di stato (vedere il [codice di stato dei file](../extensibility/file-status-code-enumerator.md) per i valori possibili).

 pnEventsRemaining

[in, out] Restituisce il numero di voci rimaste nella coda dopo la chiamata. Se questo numero è elevato, il chiamante può decidere di chiamare il [SccQueryInfo](../extensibility/sccqueryinfo-function.md) per ottenere tutte le informazioni contemporaneamente.

## <a name="return-value"></a>Valore restituito
 Si prevede che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituisca uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Eventi Get riusciti.|
|SCC_E_OPNOTSUPPORTED|Questa funzione non è supportata.|
|SCC_E_NONSPECIFICERROR|Errore non specifico.|

## <a name="remarks"></a>Commenti
 Questa funzione viene chiamata durante l'elaborazione inattiva per verificare se sono stati apportati aggiornamenti di stato per i file nel controllo del codice sorgente. Il plug-in del controllo del codice sorgente mantiene lo stato di tutti i file che conosce e ogni volta che una modifica dello stato è indicata dal plug-in, lo stato e il file associato vengono archiviati in una coda. Quando `SccGetEvents` viene chiamato il metodo, viene recuperato e restituito il primo elemento della coda. Questa funzione è vincolata a restituire solo le informazioni precedentemente memorizzate nella cache e deve avere un turnaround molto rapido (ovvero, nessuna lettura del disco o richiesta al sistema di controllo del codice sorgente per lo stato); in caso contrario, le prestazioni dell'IDE potrebbero iniziare a peggiorare.

 Se non è presente alcun aggiornamento dello stato per il report, il plug-in del controllo del codice sorgente archivia una stringa vuota nel buffer a cui punta `lpFileName` . In caso contrario, il plug-in archivia il nome del percorso completo del file per il quale sono state modificate le informazioni sullo stato e restituisce il codice di stato appropriato (uno dei valori descritti in dettaglio nel [codice di stato dei file](../extensibility/file-status-code-enumerator.md)).

## <a name="see-also"></a>Vedi anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [Codice di stato file](../extensibility/file-status-code-enumerator.md)
