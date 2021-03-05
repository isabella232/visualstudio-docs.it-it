---
description: Questa funzione avvia una sequenza di batch di operazioni del controllo del codice sorgente.
title: Funzione SccBeginBatch | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b52b82919b10e58772343aee42cb8723b10d6ca3
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221652"
---
# <a name="sccbeginbatch-function"></a>SccBeginBatch (funzione)
Questa funzione avvia una sequenza di batch di operazioni del controllo del codice sorgente. Il [SccEndBatch](../extensibility/sccendbatch-function.md) verrà chiamato per terminare il batch. Questi batch non possono essere annidati.

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccBeginBatch(void);
```

### <a name="parameters"></a>Parametri
 No.

## <a name="return-value"></a>Valore restituito
 Si prevede che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituisca uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Il batch di operazioni è stato avviato correttamente.|
|SCC_E_UNKNOWNERROR|Errore non specifico.|

## <a name="remarks"></a>Commenti
 I batch del controllo del codice sorgente vengono usati per eseguire le stesse operazioni in più progetti o in più contesti. I batch possono essere usati per eliminare le finestre di dialogo per progetto ridondanti dall'esperienza utente durante un'operazione in batch. La `SccBeginBatch` funzione e [SccEndBatch](../extensibility/sccendbatch-function.md) vengono usati come coppia di funzioni per indicare l'inizio e la fine di un'operazione. Non possono essere annidati. `SccBeginBatch` imposta un flag che indica che è in corso un'operazione batch.

 Mentre è attiva un'operazione batch, il plug-in del controllo del codice sorgente deve presentare al massimo una finestra di dialogo per qualsiasi domanda all'utente e applicare la risposta da tale finestra di dialogo in tutte le operazioni successive.

## <a name="see-also"></a>Vedi anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [SccEndBatch](../extensibility/sccendbatch-function.md)
