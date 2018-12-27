---
title: Funzione GetValidCompatibleFramework
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: b93e0de5f1d8c1d4e93189e7bfee36d44db19319
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/20/2018
ms.locfileid: "53648878"
---
# <a name="getvalidcompatibleframework-function"></a>Funzione GetValidCompatibleFramework
  Questa API supporta l'infrastruttura Office e non è destinata a essere utilizzato direttamente dal codice.  

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
 Se la funzione ha esito positivo, restituisce **S_OK**. Se la funzione ha esito negativo, restituisce un codice di errore.  

