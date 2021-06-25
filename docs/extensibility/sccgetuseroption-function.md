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
ms.workload:
- vssdk
ms.openlocfilehash: 622abc04609edf410214af6b8acf795f969e2fbc
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901110"
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

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [Codici errore](../extensibility/error-codes.md)
