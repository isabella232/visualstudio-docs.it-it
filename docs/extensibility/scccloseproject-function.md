---
description: Questa funzione chiude un progetto, contrassegnando la fine di una sessione specifica.
title: Funzione SccCloseProject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 859b1ddea99e74cc1c1dec999611e50216c3c98a
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904695"
---
# <a name="scccloseproject-function"></a>Funzione SccCloseProject
Questa funzione chiude un progetto, contrassegnando la fine di una sessione specifica.

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccCloseProject (
   LPVOID pvContext
);
```

### <a name="parameters"></a>Parametri
 pvContext Struttura del contesto del plug-in del controllo del codice sorgente.

## <a name="return-value"></a>Valore restituito
 È previsto che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituirà uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Il progetto è stato chiuso correttamente.|
|SCC_E_PROJNOTOPEN|Nessun progetto è attualmente aperto.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|
|SCC_E_NONSPECIFICERROR|Errore non specifico.|

## <a name="remarks"></a>Commenti
 [SccOpenProject viene](../extensibility/sccopenproject-function.md) sempre chiamato prima di questa funzione. Una chiamata a questa funzione è quindi seguita da una chiamata alla funzione o `SccOpenProject` [a SccUninitialize](../extensibility/sccuninitialize-function.md), che termina completamente la connessione al sistema di controllo del codice sorgente.

## <a name="see-also"></a>Vedere anche
- [Funzioni API plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
