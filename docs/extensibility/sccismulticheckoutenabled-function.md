---
title: Funzione SccIsMultiCheckoutEnabled | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dd8fb5439ac68200ba1a3bbf3af665595528173e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721075"
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

in Struttura del contesto del plug-in del controllo del codice sorgente.

 pbMultiCheckout

out Specifica se sono abilitate più estrazioni per questo progetto (valore diverso da zero indica che sono supportate più estrazioni).

## <a name="return-value"></a>Valore restituito
 Si prevede che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituisca uno dei valori seguenti:

|Value|Descrizione|
|-----------|-----------------|
|SCC_OK|Il controllo è stato completato correttamente.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Errore non specifico.|

## <a name="remarks"></a>Note
 L'IDE esegue due controlli per determinare se i file possono essere estratti simultaneamente da più di un utente. In primo luogo, il sistema di controllo del codice sorgente deve supportare più estrazioni. Il plug-in del controllo del codice sorgente può specificare questa funzionalità durante l'inizializzazione specificando la `SCC_CAP_MULTICHECKOUT`. Successivamente, come secondo controllo, l'IDE chiama questa funzione per determinare se il progetto corrente supporta più estrazioni. Se per il progetto selezionato sono supportate più estrazioni, il plug-in restituisce un codice di esito positivo e imposta `pbMultiCheckout` su un valore diverso da zero (`TRUE`) o `FALSE`.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)