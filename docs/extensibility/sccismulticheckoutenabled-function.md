---
description: Questa funzione controlla se il plug-in del controllo del codice sorgente consente più estrazioni in un file.
title: Funzione SccIsMultiCheckoutEnabled | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: fc46414d5f48dac38c9f457f5f70ccb90698507e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122110150"
---
# <a name="sccismulticheckoutenabled-function"></a>Funzione SccIsMultiCheckoutEnabled
Questa funzione controlla se il plug-in del controllo del codice sorgente consente più estrazioni in un file.

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccIsMultiCheckoutEnabled(
   LPVOID pContext,
   LPBOOL pbMultiCheckout
);
```

#### <a name="parameters"></a>Parametri
 pContext

[in] Struttura del contesto del plug-in del controllo del codice sorgente.

 pbMultiCheckout

[out] Specifica se sono abilitate più estrazioni per questo progetto (il valore diverso da zero indica che sono supportate più estrazioni).

## <a name="return-value"></a>Valore restituito
 È previsto che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituirà uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Il controllo ha avuto esito positivo.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Errore non specifico.|

## <a name="remarks"></a>Commenti
 L'IDE esegue due controlli per determinare se i file possono essere estratti contemporaneamente da più utenti. In primo luogo, il sistema di controllo del codice sorgente deve supportare più estrazioni. Il plug-in del controllo del codice sorgente può specificare questa funzionalità durante l'inizializzazione specificando `SCC_CAP_MULTICHECKOUT` . Successivamente, come secondo controllo, l'IDE chiama questa funzione per determinare se il progetto corrente supporta o meno più estrazioni. Se sono supportate più estrazioni per il progetto selezionato, il plug-in restituisce un codice di esito positivo e imposta su un valore diverso da `pbMultiCheckout` zero ( ) o `TRUE` `FALSE` .

## <a name="see-also"></a>Vedi anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
