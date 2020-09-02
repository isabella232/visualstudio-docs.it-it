---
title: 'IDebugProperty2:: GetParent | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetParent
helpviewer_keywords:
- IDebugProperty2::GetParent
ms.assetid: 58780469-fe25-4d84-9187-67940ca0767f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 85c8ac00550c4a8e63cd06bdabf9e794f636129d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538714"
---
# <a name="idebugproperty2getparent"></a>IDebugProperty2::GetParent
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ottiene la proprietà padre di una proprietà.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetParent (   
   IDebugProperty2** ppParent  
);  
```  
  
```csharp  
int GetParent (   
   out IDebugProperty2 ppParent  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppParent`  
 out Restituisce un oggetto [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) che rappresenta l'elemento padre della proprietà.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce il codice errore. Restituisce `S_GETPARENT_NO_PARENT` se non esiste alcun padre.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
