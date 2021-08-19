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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 804afa6f8bdf0bd02ea25ba2fb4639048d2d5bf0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122144496"
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
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Il progetto è stato chiuso correttamente.|
|SCC_E_PROJNOTOPEN|Nessun progetto è attualmente aperto.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|
|SCC_E_NONSPECIFICERROR|Errore non specifico.|

## <a name="remarks"></a>Commenti
 [SccOpenProject viene](../extensibility/sccopenproject-function.md) sempre chiamato prima di questa funzione. Una chiamata a questa funzione viene quindi seguita da una chiamata alla funzione o `SccOpenProject` [a SccUninitialize](../extensibility/sccuninitialize-function.md), che termina completamente la connessione al sistema di controllo del codice sorgente.

## <a name="see-also"></a>Vedi anche
- [Funzioni API plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
