---
description: Questa funzione avvia una sequenza batch di operazioni di controllo del codice sorgente.
title: Funzione SccBeginBatch | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: fc1d78840915899181046d3e1bfb19d554751c1a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122144600"
---
# <a name="sccbeginbatch-function"></a>Funzione SccBeginBatch
Questa funzione avvia una sequenza batch di operazioni di controllo del codice sorgente. [SccEndBatch](../extensibility/sccendbatch-function.md) verrà chiamato per terminare il batch. Questi batch potrebbero non essere annidati.

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccBeginBatch(void);
```

### <a name="parameters"></a>Parametri
 No.

## <a name="return-value"></a>Valore restituito
 È previsto che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituirà uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Batch di operazioni avviato correttamente.|
|SCC_E_UNKNOWNERROR|Errore non specifico.|

## <a name="remarks"></a>Commenti
 I batch di controllo del codice sorgente vengono usati per eseguire le stesse operazioni in più progetti o più contesti. I batch possono essere usati per eliminare le finestre di dialogo ridondanti per progetto dall'esperienza utente durante un'operazione in batch. La `SccBeginBatch` funzione e [SccEndBatch](../extensibility/sccendbatch-function.md) vengono usate come coppia di funzioni per indicare l'inizio e la fine di un'operazione. Non possono essere annidati. `SccBeginBatch` imposta un flag che indica che è in corso un'operazione batch.

 Mentre è in corso un'operazione batch, il plug-in del controllo del codice sorgente deve presentare al massimo una finestra di dialogo per qualsiasi domanda all'utente e applicare la risposta da tale finestra di dialogo a tutte le operazioni successive.

## <a name="see-also"></a>Vedi anche
- [Funzioni API plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [SccEndBatch](../extensibility/sccendbatch-function.md)
