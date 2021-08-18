---
description: Questa funzione recupera un'ampia gamma di opzioni specifiche dell'utente.
title: Funzione SccGetUserOption | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGetUserOption
helpviewer_keywords:
- SccGetUserOption function
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: c8262d971d1eb9f161693ad86fc1878d29353a79
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122028670"
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

[in] Puntatore al contesto del plug-in del controllo del codice sorgente.

 nOption

[in] Opzione da recuperare (vedere la sezione Osservazioni per le opzioni possibili).

 lpVal

[out] Valore associato all'opzione.

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|L'opzione è stata recuperata correttamente.|
|SCC_E_OPNOTSUPPORTED|L'opzione non è supportata.|
|SCC_E_NONSPECIFICERROR|Si è verificato un errore non specificato.|

## <a name="remarks"></a>Commenti
 Questo comando supporta le opzioni seguenti:

|Opzione utente|Descrizione|
|-----------------|-----------------|
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Determina se l'utente vuole estrarre la versione locale dei file. `lpVal` è assegnato `SCC_USEROPT_COLV_YES` (l'utente vuole estrarre i file locali) o `SCC_USEROPT_COLV_NO` .|

## <a name="see-also"></a>Vedi anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [Codici errore](../extensibility/error-codes.md)
