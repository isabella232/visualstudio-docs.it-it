---
description: Questa funzione chiude un progetto, contrassegnando la fine di una sessione specifica.
title: Funzione SccCloseProject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 05dbf0552242bdc1a21ec6dd81a592711f50f391
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085637"
---
# <a name="scccloseproject-function"></a>SccCloseProject (funzione)
Questa funzione chiude un progetto, contrassegnando la fine di una sessione specifica.

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccCloseProject (
   LPVOID pvContext
);
```

### <a name="parameters"></a>Parametri
 pvContext la struttura del contesto del plug-in del controllo del codice sorgente.

## <a name="return-value"></a>Valore restituito
 Si prevede che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituisca uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Il progetto è stato chiuso correttamente.|
|SCC_E_PROJNOTOPEN|Nessun progetto attualmente aperto.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|
|SCC_E_NONSPECIFICERROR|Errore non specifico.|

## <a name="remarks"></a>Commenti
 [SccOpenProject](../extensibility/sccopenproject-function.md) viene sempre chiamato prima della funzione. Una chiamata a questa funzione è seguita da una chiamata alla `SccOpenProject` funzione o a [SccUninitialize](../extensibility/sccuninitialize-function.md), che termina la connessione al sistema di controllo del codice sorgente completamente.

## <a name="see-also"></a>Vedi anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
