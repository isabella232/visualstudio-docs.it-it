---
title: Funzione SccGetExtendedCapabilities | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa6a067a0b9e8358f503228dbc53e20586b84468
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353661"
---
# <a name="sccgetextendedcapabilities-function"></a>Funzione SccGetExtendedCapabilities
Questa funzione restituisce funzionalità aggiuntive supportate dal controllo del codice sorgente del plug-in.

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccGetExtendedCapabilities(
   LPVOID pContext,
   LONG lSccExCaps,
   LPBOOL pbSupported
);
```

### <a name="parameters"></a>Parametri
 pContext

[in] Il puntatore di contesto del plug-in controllo di origine.

 lSccExCaps

[in] Un flag che specifica una funzionalità estesa per cui eseguire il test (vedere la tabella codice esteso di funzionalità nella [flag di funzionalità](../extensibility/capability-flags.md) per i possibili flag).

 pbSupported

[out] Restituisce diverso da zero (`TRUE`) se la funzionalità specificata è supportata; in caso contrario, restituisce zero (`FALSE`).

## <a name="return-value"></a>Valore restituito
 Implementazione di plug-in del controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:

|Value|Descrizione|
|-----------|-----------------|
|SCC_OK|L'operazione get funzionalità completata correttamente.|
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|Si è verificato un errore sconosciuto o non specificato.|

## <a name="remarks"></a>Note
 Questo metodo viene chiamato su richiesta. ovvero quando una funzionalità deve essere testata, questo metodo viene chiamato per determinare se la funzionalità è supportata. Viene specificato il flag solo una alla volta.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in origine controllo](../extensibility/source-control-plug-in-api-functions.md)
- [Codici di errore](../extensibility/error-codes.md)
- [Flag funzionalità](../extensibility/capability-flags.md)