---
title: Funzione SccBeginBatch . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6c7982d8c8c0d71f8c79e9b808be5453d384882d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701191"
---
# <a name="sccbeginbatch-function"></a>SccBeginBatch (funzione)
Questa funzione avvia una sequenza batch di operazioni di controllo del codice sorgente. [SccEndBatch](../extensibility/sccendbatch-function.md) verrà chiamato per terminare il batch. Questi batch non possono essere annidati.

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccBeginBatch(void);
```

### <a name="parameters"></a>Parametri
 No.

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei seguenti valori:

|valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Batch di operazioni avviato correttamente.|
|SCC_E_UNKNOWNERROR|Errore non specifico.|

## <a name="remarks"></a>Osservazioni
 I batch di controllo del codice sorgente vengono utilizzati per eseguire le stesse operazioni in più progetti o più contesti. I batch possono essere utilizzati per eliminare le finestre di dialogo ridondanti per progetto dall'esperienza utente durante un'operazione in batch. La `SccBeginBatch` funzione e [SccEndBatch](../extensibility/sccendbatch-function.md) vengono utilizzati come coppia di funzioni per indicare l'inizio e la fine di un'operazione. Non possono essere annidati. `SccBeginBatch`imposta un flag che indica che è in corso un'operazione batch.

 Mentre è attiva un'operazione batch, il plug-in del controllo del codice sorgente deve presentare al massimo una finestra di dialogo per qualsiasi domanda all'utente e applicare la risposta da tale finestra di dialogo in tutte le operazioni successive.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [SccEndBatch](../extensibility/sccendbatch-function.md)
