---
description: Questa funzione restituisce funzionalità aggiuntive supportate dal plug-in del controllo del codice sorgente.
title: Funzione SccGetExtendedCapabilities | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ca2f2f77c586c5c71658a8f0cab32385eb3f73d3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073001"
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

in Puntatore al contesto del plug-in del controllo del codice sorgente.

 lSccExCaps

in Flag che specifica una funzionalità estesa per la quale eseguire il test (vedere la tabella del codice delle funzionalità estese nei [flag di funzionalità](../extensibility/capability-flags.md) per i flag possibili).

 pbSupported

out Restituisce un valore diverso da zero ( `TRUE` ) se la funzionalità specificata è supportata; in caso contrario, restituisce zero ( `FALSE` ).

## <a name="return-value"></a>Valore restituito
 Si prevede che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituisca uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|L'operazione Get Capability è stata completata correttamente.|
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|Si è verificato un errore sconosciuto o non specificato.|

## <a name="remarks"></a>Commenti
 Questo metodo viene chiamato su richiesta; ovvero, quando è necessario testare una funzionalità, questo metodo viene chiamato per determinare se tale funzionalità è supportata. Viene specificato un solo flag alla volta.

## <a name="see-also"></a>Vedi anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [Codici di errore](../extensibility/error-codes.md)
- [Flag funzionalità](../extensibility/capability-flags.md)
