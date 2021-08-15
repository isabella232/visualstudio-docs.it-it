---
description: Questa funzione restituisce funzionalità aggiuntive supportate dal plug-in del controllo del codice sorgente.
title: Funzione SccGetExtendedCapabilities | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 986a5f33b4b2476cc327b5e2e4b287f1e29cc5d95487d61ace6ebf22e9d23916
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121321051"
---
# <a name="sccgetextendedcapabilities-function"></a>Funzione SccGetExtendedCapabilities
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

[in] Puntatore al contesto del plug-in del controllo del codice sorgente.

 lSccExCaps

[in] Flag che specifica una funzionalità estesa per la quale eseguire il test. Per i flag possibili, vedere la tabella Extended [Capability](../extensibility/capability-flags.md) Code in Flag di funzionalità.

 pbSupported

[out] Restituisce un valore diverso da zero ( `TRUE` ) se la funzionalità specificata è supportata; in caso contrario, restituisce zero ( `FALSE` ).

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|L'operazione get capability è stata completata correttamente.|
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|Si è verificato un errore sconosciuto o non specificato.|

## <a name="remarks"></a>Commenti
 Questo metodo viene chiamato su richiesta. quando è necessario testare una funzionalità, questo metodo viene chiamato per determinare se tale funzionalità è supportata. Viene specificato un solo flag alla volta.

## <a name="see-also"></a>Vedi anche
- [Funzioni API plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [Codici di errore](../extensibility/error-codes.md)
- [Flag di funzionalità](../extensibility/capability-flags.md)
