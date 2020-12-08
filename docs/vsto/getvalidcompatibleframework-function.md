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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 96f536b3ab8e28b87a59a637fcf6dbaadeb21bf7
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845076"
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
