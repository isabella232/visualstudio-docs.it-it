---
title: Funzione SccEndBatch . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51fe7e0bc0d417ffa182fbc68fd2779ed0b625d9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700917"
---
# <a name="sccendbatch-function"></a>SccEndBatch (funzione)
Questa funzione conclude un batch di operazioni di controllo del codice sorgente. Questi batch non possono essere annidati.

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccEndBatch(void);
```

## <a name="parameters"></a>Parametri
 No.

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei seguenti valori:

|valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Batch di operazioni concluse con successo.|
|SCC_E_UNKNOWNERROR|Errore non specifico.|

## <a name="remarks"></a>Osservazioni
 I batch di controllo del codice sorgente vengono utilizzati per eseguire le stesse operazioni di controllo del codice sorgente in più progetti o più contesti. I batch possono essere utilizzati per eliminare le finestre di dialogo ridondanti dall'esperienza utente durante un'operazione in batch. [SccBeginBatch](../extensibility/sccbeginbatch-function.md) e `SccEndBatch` la funzione vengono utilizzati come coppia per indicare l'inizio e la fine di un'operazione. Non possono essere annidati.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [SccBeginBatch](../extensibility/sccbeginbatch-function.md)
