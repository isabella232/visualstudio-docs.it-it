---
title: Funzione EnsureVSTOComponent
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
ms.openlocfilehash: 39dcdcc5e3b8e6e5bc5834e7e05ea22516d8c7e6
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/20/2018
ms.locfileid: "53648613"
---
# <a name="ensurevstocomponent-function"></a>Funzione EnsureVSTOComponent
  Questa API supporta l'infrastruttura Office e non è destinata a essere utilizzato direttamente dal codice.  
  
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
 Se la funzione ha esito positivo, restituisce **S_OK**. Se la funzione ha esito negativo, restituisce un codice di errore.  
  
  