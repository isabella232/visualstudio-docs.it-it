---
title: SccGetEvents (funzione) . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetEvents
helpviewer_keywords:
- SccGetEvents function
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 91b3debf0e686ceece3048cf3d92b629e3359edd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700812"
---
# <a name="sccgetevents-function"></a>SccGetEvents (funzione)SccGetEvents function
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

[in] Struttura di contesto del plug-in del controllo del codice sorgente.

 LpNomeFile

[in, out] Buffer in cui il plug-in del controllo del codice sorgente inserisce il nome del file restituito (fino a _MAX_PATH caratteri).

 lpStatus (Stato

[in, out] Restituisce il codice di stato (vedere [Codice di stato file](../extensibility/file-status-code-enumerator.md) per i valori possibili).

 pnEventiRimanenti

[in, out] Restituisce il numero di voci rimaste nella coda dopo questa chiamata. Se questo numero è elevato, il chiamante può decidere di chiamare [SccQueryInfo](../extensibility/sccqueryinfo-function.md) per ottenere tutte le informazioni contemporaneamente.

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei seguenti valori:

|valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Ottenere gli eventi riusciti.|
|SCC_E_OPNOTSUPPORTED|Questa funzione non è supportata.|
|SCC_E_NONSPECIFICERROR|Errore non specifico.|

## <a name="remarks"></a>Osservazioni
 Questa funzione viene chiamata durante l'elaborazione inattiva per verificare se sono stati visualizzati aggiornamenti di stato per i file nel controllo del codice sorgente. Il plug-in del controllo del codice sorgente mantiene lo stato di tutti i file che conosce e ogni volta che una modifica di stato viene rilevata dal plug-in, lo stato e il file associato vengono archiviati in una coda. Quando `SccGetEvents` viene chiamato, l'elemento superiore della coda viene recuperato e restituito. Questa funzione è vincolata a restituire solo informazioni memorizzate nella cache in precedenza e deve avere un turnaround molto rapido (vale a dire, nessuna lettura del disco o chiedere lo stato al sistema di controllo del codice sorgente); in caso contrario, le prestazioni dell'IDE potrebbero iniziare a peggiorare.

 Se non è presente alcun aggiornamento dello stato da segnalare, il plug-in del controllo del codice sorgente archivia una stringa vuota nel buffer a `lpFileName`cui punta . In caso contrario, il plug-in archivia il nome del percorso completo del file per il quale sono state modificate le informazioni sullo stato e restituisce il codice di stato appropriato (uno dei valori descritti in [Codice di stato del file](../extensibility/file-status-code-enumerator.md)).

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [Codice di stato del file](../extensibility/file-status-code-enumerator.md)
