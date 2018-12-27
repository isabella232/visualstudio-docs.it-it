---
title: Funzione GetVstoSolutionMetadata
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
ms.openlocfilehash: baa5cf48d317da80f78d19a1b72f81824b1bed62
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/20/2018
ms.locfileid: "53647267"
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
  
  