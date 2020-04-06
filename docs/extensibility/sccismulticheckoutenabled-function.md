---
title: SccIsMultiCheckoutEnabled (funzione) . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e91eb566a820f4fe11ceb629643e1815dcb87a8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700589"
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

[in] Struttura di contesto del plug-in del controllo del codice sorgente.

 pbMultiCheckout (informazioni in base al sistema

[fuori] Specifica se più estrazioni sono abilitate per questo progetto (diverso da zero significa che sono supportate più estrazioni).

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei seguenti valori:

|valore|Descrizione|
|-----------|-----------------|
|SCC_OK|L'assegno è riuscito.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Errore non specifico.|

## <a name="remarks"></a>Osservazioni
 L'IDE effettua due controlli per determinare se i file possono essere estratti contemporaneamente da più di un utente. In primo luogo, il sistema di controllo del codice sorgente deve supportare più estrazioni. Il plug-in del controllo del codice sorgente può `SCC_CAP_MULTICHECKOUT`specificare questa funzionalità durante l'inizializzazione specificando l'oggetto . Successivamente, come secondo controllo, l'IDE chiama questa funzione per determinare se il progetto corrente supporta più estrazioni. Se per il progetto selezionato sono supportate più estrazioni, `pbMultiCheckout` il plug-in restituisce un codice di esito positivo e imposta su un valore diverso da zero (`TRUE`) o `FALSE`.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
