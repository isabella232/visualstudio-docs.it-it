---
title: IDebugObject2::GetICorDebugValue | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugObject2::GetICorDebugValue
helpviewer_keywords:
- IDebugObject2::GetICorDebugValue method
ms.assetid: bcd4355d-3fbe-483f-bb23-a44348323c6a
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cc91846d7ee68ec7381d552c4cb8c1c85128490b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47525556"
---
# <a name="idebugobject2geticordebugvalue"></a>IDebugObject2::GetICorDebugValue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugObject2::GetICorDebugValue](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugobject2-geticordebugvalue).  
  
Ottiene un oggetto di codice gestito che rappresenta il valore associato all'oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetICorDebugValue(  
   IUnknown** ppUnk  
);  
```  
  
```csharp  
int GetICorDebugValue(  
   out object ppUnk  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppUnk`  
 [out] `IUnknown` interfaccia che rappresenta l'alias. Questa interfaccia è possibile eseguire query per il `ICorDebugValue` interfaccia.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il `ICorDebugValue` oggetto è un'interfaccia di Common Language Runtime che rappresenta un valore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)

