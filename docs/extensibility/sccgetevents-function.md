---
description: Questa funzione recupera un evento di stato in coda.
title: Funzione SccGetEvents | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGetEvents
helpviewer_keywords:
- SccGetEvents function
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 2a5c382b7c7a5bd48d1b2db22a4c0469d0f16b2d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122144444"
---
# <a name="sccgetevents-function"></a>Funzione SccGetEvents
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

[in] Struttura del contesto del plug-in del controllo del codice sorgente.

 lpFileName

[in, out] Buffer in cui il plug-in del controllo del codice sorgente inserisce il nome file restituito (fino a _MAX_PATH caratteri).

 lpStatus

[in, out] Restituisce il codice di stato (vedere [Codice di stato del file](../extensibility/file-status-code-enumerator.md) per i valori possibili).

 pnEventsRemaining

[in, out] Restituisce il numero di voci rimasti nella coda dopo questa chiamata. Se questo numero è elevato, il chiamante può decidere di chiamare [SccQueryInfo](../extensibility/sccqueryinfo-function.md) per ottenere tutte le informazioni contemporaneamente.

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Ottenere gli eventi con esito positivo.|
|SCC_E_OPNOTSUPPORTED|Questa funzione non è supportata.|
|SCC_E_NONSPECIFICERROR|Errore non specifico.|

## <a name="remarks"></a>Commenti
 Questa funzione viene chiamata durante l'elaborazione inattiva per verificare se sono stati esatti aggiornamenti di stato per i file nel controllo del codice sorgente. Il plug-in di controllo del codice sorgente mantiene lo stato di tutti i file di cui è a conoscenza e ogni volta che il plug-in indica una modifica dello stato, lo stato e il file associato vengono archiviati in una coda. Quando `SccGetEvents` viene chiamato , l'elemento principale della coda viene recuperato e restituito. Questa funzione è vincolata a restituire solo le informazioni memorizzate nella cache in precedenza e deve avere un turnaround molto rapido( ovvero nessuna lettura del disco o richiesta dello stato al sistema di controllo del codice sorgente); in caso contrario, le prestazioni dell'IDE potrebbero iniziare a peggiorare.

 Se non è presente alcun aggiornamento dello stato per il report, il plug-in del controllo del codice sorgente archivia una stringa vuota nel buffer a cui punta `lpFileName` . In caso contrario, il plug-in archivia il nome del percorso completo del file per il quale sono state modificate le informazioni sullo stato e restituisce il codice di stato appropriato (uno dei valori dettagliati in Codice di stato [del file](../extensibility/file-status-code-enumerator.md)).

## <a name="see-also"></a>Vedi anche
- [Funzioni API plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [Codice di stato del file](../extensibility/file-status-code-enumerator.md)
