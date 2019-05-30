---
title: Funzione SccGetUserOption | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetUserOption
helpviewer_keywords:
- SccGetUserOption function
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eabf9cfc9d878d4d12096c8d264e8ee332031adf
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353646"
---
# <a name="sccgetuseroption-function"></a>Funzione SccGetUserOption
Questa funzione recupera un'ampia gamma di opzioni specifiche dell'utente.

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccGetUserOption(
   LPVOID pContext,
   LONG nOption,
   LPLONG lpVal
);
```

#### <a name="parameters"></a>Parametri
 pContext

[in] Il puntatore di contesto del plug-in controllo di origine.

 nOption

[in] Opzione da recuperare (per le opzioni possibili, vedere la sezione Osservazioni).

 lpVal

[out] Valore associato all'opzione.

## <a name="return-value"></a>Valore restituito
 Implementazione di plug-in del controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:

|Value|Descrizione|
|-----------|-----------------|
|SCC_OK|Opzione è stato recuperato correttamente.|
|SCC_E_OPNOTSUPPORTED|Opzione non è supportata.|
|SCC_E_NONSPECIFICERROR|Si è verificato un errore non specificato.|

## <a name="remarks"></a>Note
 Le opzioni seguenti sono supportate da questo comando:

|Opzione User|Descrizione|
|-----------------|-----------------|
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Determina se l'utente desidera estrarre la versione locale dei file. `lpVal` viene assegnato `SCC_USEROPT_COLV_YES` (utente desidera estrarre i file locali) o `SCC_USEROPT_COLV_NO`.|

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [Codici di errore](../extensibility/error-codes.md)