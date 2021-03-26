---
description: Questa funzione recupera un'ampia gamma di opzioni specifiche dell'utente.
title: Funzione SccGetUserOption | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetUserOption
helpviewer_keywords:
- SccGetUserOption function
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 262a15069f840c048f574396d5a7ec076760d77e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063955"
---
# <a name="sccgetuseroption-function"></a>Funzione SccGetUserOption
Questa funzione recupera un'ampia gamma di opzioni specifiche dell'utente.

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccGetUserOption(
   LPVOID pContext,
   LONG nOption,
   LPLONG lpVal
);
```

#### <a name="parameters"></a>Parametri
 pContext

in Puntatore al contesto del plug-in del controllo del codice sorgente.

 nOption

in Opzione da recuperare (vedere le note per le possibili opzioni).

 lpVal

out Valore associato all'opzione.

## <a name="return-value"></a>Valore restituito
 Si prevede che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituisca uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|L'opzione è stata recuperata correttamente.|
|SCC_E_OPNOTSUPPORTED|L'opzione non è supportata.|
|SCC_E_NONSPECIFICERROR|Si è verificato un errore non specificato.|

## <a name="remarks"></a>Commenti
 Questo comando supporta le opzioni seguenti:

|Opzione utente|Descrizione|
|-----------------|-----------------|
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Determina se l'utente desidera estrarre la versione locale dei file. `lpVal` viene assegnato `SCC_USEROPT_COLV_YES` (l'utente desidera estrarre i file locali) o `SCC_USEROPT_COLV_NO` .|

## <a name="see-also"></a>Vedi anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [Codici errore](../extensibility/error-codes.md)
