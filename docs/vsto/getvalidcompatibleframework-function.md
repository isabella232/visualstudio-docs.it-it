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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8cc16544df224e09724cae8a1f09f72039cb61e5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894495"
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

