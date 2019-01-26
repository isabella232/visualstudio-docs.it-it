---
title: Funzione GetValidCompatibleFramework
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
ms.openlocfilehash: 79b97867a3a5c87f1e208d93efacea711ba71efc
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54869307"
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
