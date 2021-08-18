---
title: Funzione GetValidCompatibleFramework
description: Informazioni su come l'API GetValidCompatibleFramework supporta l'infrastruttura Office e non deve essere usata direttamente dal codice.
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
ms.openlocfilehash: a0e13e1ea1eda0e0768a1982b56bd7eeb496a1a2fc49ee9a2be64ad8e47dc0ea
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121424190"
---
# <a name="getvalidcompatibleframework-function"></a>Funzione GetValidCompatibleFramework
  Questa API supporta l'Office e non deve essere usata direttamente dal codice.

## <a name="syntax"></a>Sintassi

```csharp
HRESULT WINAPI GetValidCompatibleFramework(
    LPCWSTR lpwszCompatibleFrameworksXML,
    BSTR* pbstrValidFrameworkTag
);
```

### <a name="parameters"></a>Parametri

|Parametro|Descrizione|
|---------------|-----------------|
|*lpwszCompatibleFrameworksXML*|Non usare.|
|*pbstrValidFrameworkTag*|Non usare.|

## <a name="return-value"></a>Valore restituito
 Se la funzione ha esito positivo, restituisce **S_OK**. Se la funzione non viene completata, restituisce un codice di errore.
