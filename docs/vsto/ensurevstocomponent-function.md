---
title: Funzione EnsureVSTOComponent
description: Informazioni su come l'API EnsureVSTOComponent supporta l'infrastruttura Office e non deve essere usata direttamente dal codice.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: c7de049c7388d71078dae1d4a14a1427b78c4cc5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122026447"
---
# <a name="ensurevstocomponent-function"></a>Funzione EnsureVSTOComponent
  Questa API supporta l'Office e non deve essere usata direttamente dal codice.

## <a name="syntax"></a>Sintassi

```csharp
HRESULT EnsureVSTOComponent(
    IVSTProject *pProject
);
```

#### <a name="parameters"></a>Parametri

|Parametro|Descrizione|
|---------------|-----------------|
|*pProject*|Non usare.|

## <a name="return-value"></a>Valore restituito
 Se la funzione ha esito positivo, restituisce **S_OK**. Se la funzione non viene completata, restituisce un codice di errore.
