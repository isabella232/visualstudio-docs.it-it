---
title: Funzione GetVstoSolutionMetadata
description: Informazioni su come l'API GetVstoSolutionMetadata supporta l'infrastruttura Office e non deve essere usata direttamente dal codice.
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
ms.openlocfilehash: 14cf1d9ab6c8c3a734caa737b99a5edaededb94f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710101"
---
# <a name="getvstosolutionmetadata-function"></a>Funzione GetVstoSolutionMetadata
  Questa API supporta l'Office e non deve essere usata direttamente dal codice.

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
 Se la funzione ha esito positivo, restituisce **S_OK**. Se la funzione non viene completata, restituisce un codice di errore.
