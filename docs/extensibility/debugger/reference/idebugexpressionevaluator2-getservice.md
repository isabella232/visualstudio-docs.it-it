---
title: IDebugExpressionEvaluator2::GetService | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugExpressionEvaluator2::GetService
- GetService
ms.assetid: f8988a9e-9d18-42af-84a7-55f41e9adf63
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fa07c11f6d7bc0cbbac2f55158012d7ce78a0e1d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49936693"
---
# <a name="idebugexpressionevaluator2getservice"></a>IDebugExpressionEvaluator2::GetService
Recupera un oggetto servizio dato il relativo identificatore univoco.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetService (  
   GUID        uid,  
   IUnknown ** ppService  
);  
```  
  
```csharp  
int GetService (  
   Guid       uid,  
   out object ppService  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `uid`  
 [in] Identificatore univoco del servizio da recuperare.  
  
 `ppService`  
 [out] Restituisce un oggetto che rappresenta il servizio.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Ciò può essere utilizzato da un analizzatore di espressioni di terze parti per ottenere servizi dall'analizzatore di espressioni di un altro. Questo metodo, ad esempio, potrebbe essere utilizzato per ottenere l'interfaccia per il servizio Visualizzatore dall'analizzatore di espressioni predefinito. Analizzatori di espressioni di terze parti sono improbabile che devono implementare questa interfaccia.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)