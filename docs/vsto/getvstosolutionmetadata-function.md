---
title: GetVstoSolutionMetadata (funzione)
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
ms.openlocfilehash: aebbedaab7e7ac342f6d6ace191d820f6a0c8090
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85520185"
---
# <a name="getvstosolutionmetadata-function"></a>GetVstoSolutionMetadata (funzione)
  Questa API supporta l'infrastruttura Office e non è destinata all'uso diretto dal codice.

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
