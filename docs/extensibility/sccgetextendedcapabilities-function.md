---
title: SccGetExtendedCapabilities (funzione) . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5247f2de7ffc63db7235f915c72b3274b8fee5f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700729"
---
# <a name="sccgetextendedcapabilities-function"></a>SccGetExtendedCapabilities (funzione)
Questa funzione restituisce funzionalità aggiuntive supportate dal plug-in del controllo del codice sorgente.

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

[in] Puntatore di contesto del plug-in del controllo del codice sorgente.

 lSccExCaps

[in] Flag che specifica una funzionalità estesa per la quale eseguire il test (vedere la tabella Codice funzionalità estesa in [Flag di capacità](../extensibility/capability-flags.md) per i possibili flag).

 pbSupportato

[fuori] Restituisce diverso`TRUE`da zero ( ) se la funzionalità specificata è supportata; in caso contrario, restituisce zero (`FALSE`).

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei seguenti valori:

|valore|Descrizione|
|-----------|-----------------|
|SCC_OK|L'operazione get capability è stata completata correttamente.|
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|Si è verificato un errore sconosciuto o non specificato.|

## <a name="remarks"></a>Osservazioni
 Questo metodo viene chiamato su richiesta; vale a dire, quando è necessario testare una funzionalità, questo metodo viene chiamato per determinare se tale funzionalità è supportata. Viene specificato un solo flag alla volta.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [Codici di errore](../extensibility/error-codes.md)
- [Flag di capacità](../extensibility/capability-flags.md)
