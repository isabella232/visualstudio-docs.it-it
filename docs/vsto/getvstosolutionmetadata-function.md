---
title: Funzione GetVstoSolutionMetadata
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d7714e78e897e6c8b391a6c30e9a548671ce80c4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62796041"
---
# <a name="getvstosolutionmetadata-function"></a>Funzione GetVstoSolutionMetadata
  Questa API supporta l'infrastruttura Office e non è destinata a essere utilizzato direttamente dal codice.

## <a name="syntax"></a>Sintassi

```csharp
HRESULT WINAPI GetVstoSolutionMetadata(
    LPCWSTR lpwszSolutionMetadataKey,
    ISolutionMetadata** ppSolutionInfo
);
```

### <a name="parameters"></a>Parametri

|Parametro|Descrizione|
|---------------|-----------------|
|*lpwszSolutionMetadataKey*|Non usare.|
|*ppSolutionInfo*|Non usare.|

## <a name="return-value"></a>Valore restituito
 Se la funzione ha esito positivo, restituisce **S_OK**. Se la funzione ha esito negativo, restituisce un codice di errore.
