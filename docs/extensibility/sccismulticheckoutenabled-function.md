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
ms.openlocfilehash: 90efd3f727611492b0afe2269b5464ae303d840efe2472e987a5450022117040
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121237761"
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

[out] Specifica se sono abilitate più estrazioni per questo progetto (un valore diverso da zero indica che sono supportate più estrazioni).

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Il controllo ha avuto esito positivo.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Errore non specifico.|

## <a name="remarks"></a>Commenti
 L'IDE esegue due controlli per determinare se i file possono essere estratti simultaneamente da più utenti. In primo luogo, il sistema di controllo del codice sorgente deve supportare più estrazioni. Il plug-in del controllo del codice sorgente può specificare questa funzionalità durante l'inizializzazione specificando `SCC_CAP_MULTICHECKOUT` . Successivamente, come secondo controllo, l'IDE chiama questa funzione per determinare se il progetto corrente supporta o meno più estrazioni. Se sono supportate più estrazioni per il progetto selezionato, il plug-in restituisce un codice di esito positivo e imposta `pbMultiCheckout` su un valore diverso da zero ( ) o `TRUE` `FALSE` .

## <a name="see-also"></a>Vedi anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
