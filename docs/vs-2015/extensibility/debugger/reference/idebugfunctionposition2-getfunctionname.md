---
title: IDebugFunctionPosition2::GetFunctionName | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugFunctionPosition2::GetFunctionName
helpviewer_keywords:
- IDebugFunctionPosition2::GetFunctionName
ms.assetid: eb7a348e-a7f5-4f25-be68-80482d5482a8
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5871cb606866b8ee0b56eb6ce36da81738704b9f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49931779"
---
# <a name="idebugfunctionposition2getfunctionname"></a>IDebugFunctionPosition2::GetFunctionName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ottiene il nome della funzione a cui fa riferimento questa posizione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetFunctionName(   
   BSTR* pbstrFunctionName  
);  
```  
  
```csharp  
int GetFunctionName(  
   out string pbstrFunctionName  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pbstrFunctionName`  
 [out] Restituisce il nome della funzione.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)

