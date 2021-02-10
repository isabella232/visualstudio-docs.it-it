---
title: Funzione SccEndBatch | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 85d49fcd9920c442aa1736f1fb0f3e46ccd4eba0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943049"
---
# <a name="sccendbatch-function"></a>SccEndBatch (funzione)
Questa funzione conclude un batch di operazioni del controllo del codice sorgente. Questi batch non possono essere annidati.

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccEndBatch(void);
```

## <a name="parameters"></a>Parametri
 No.

## <a name="return-value"></a>Valore restituito
 Si prevede che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituisca uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Il batch di operazioni è stato completato correttamente.|
|SCC_E_UNKNOWNERROR|Errore non specifico.|

## <a name="remarks"></a>Commenti
 I batch del controllo del codice sorgente vengono usati per eseguire le stesse operazioni di controllo del codice sorgente tra più progetti o più contesti. I batch possono essere usati per eliminare le finestre di dialogo ridondanti dall'esperienza utente durante un'operazione in batch. [SccBeginBatch](../extensibility/sccbeginbatch-function.md) e la `SccEndBatch` funzione vengono usati come coppia per indicare l'inizio e la fine di un'operazione. Non possono essere annidati.

## <a name="see-also"></a>Vedi anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [SccBeginBatch](../extensibility/sccbeginbatch-function.md)
