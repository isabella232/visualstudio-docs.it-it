---
title: EnsureVSTOComponent (funzione)
description: Informazioni sul modo in cui l'API EnsureVSTOComponent supporta l'infrastruttura Office e non è destinata all'uso diretto dal codice.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a04cfc249efa4640df2b2e4b1c5f4b43ed52ace2
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846116"
---
# <a name="ensurevstocomponent-function"></a>EnsureVSTOComponent (funzione)
  Questa API supporta l'infrastruttura Office e non è destinata all'uso diretto dal codice.

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
