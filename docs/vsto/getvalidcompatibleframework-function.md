---
title: GetValidCompatibleFramework (funzione)
description: Informazioni sul modo in cui l'API GetValidCompatibleFramework supporta l'infrastruttura Office e non è destinata all'uso diretto dal codice.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b089f954c59219461c8e267ee6e88e47015fc794
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860620"
---
# <a name="getvalidcompatibleframework-function"></a>GetValidCompatibleFramework (funzione)
  Questa API supporta l'infrastruttura Office e non è destinata all'uso diretto dal codice.

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
