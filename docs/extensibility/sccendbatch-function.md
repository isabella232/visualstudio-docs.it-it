---
description: Questa funzione conclude un batch di operazioni di controllo del codice sorgente.
title: Funzione SccEndBatch | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: a608f05cada958a56f3fb5403793c70f5ece5ba9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122124425"
---
# <a name="sccendbatch-function"></a>Funzione SccEndBatch
Questa funzione conclude un batch di operazioni di controllo del codice sorgente. Questi batch potrebbero non essere annidati.

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccEndBatch(void);
```

## <a name="parameters"></a>Parametri
 No.

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Il batch di operazioni è stato completato correttamente.|
|SCC_E_UNKNOWNERROR|Errore non specifico.|

## <a name="remarks"></a>Commenti
 I batch di controllo del codice sorgente vengono usati per eseguire le stesse operazioni di controllo del codice sorgente in più progetti o più contesti. I batch possono essere usati per eliminare le finestre di dialogo ridondanti dall'esperienza utente durante un'operazione in batch. [SccBeginBatch e](../extensibility/sccbeginbatch-function.md) la funzione vengono usati come coppia per indicare `SccEndBatch` l'inizio e la fine di un'operazione. Non possono essere annidati.

## <a name="see-also"></a>Vedi anche
- [Funzioni API plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [SccBeginBatch](../extensibility/sccbeginbatch-function.md)
