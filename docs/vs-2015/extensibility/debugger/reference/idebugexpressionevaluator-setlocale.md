---
title: IDebugExpressionEvaluator::SetLocale | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::SetLocale
helpviewer_keywords:
- IDebugExpressionEvaluator::SetLocale method
ms.assetid: d3d2027d-74e2-4ae6-bcc7-59d12f873b7c
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 730a105b12016ea031bdb4753da009223a5d39f5
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/15/2019
ms.locfileid: "62540524"
---
# <a name="idebugexpressionevaluatorsetlocale"></a>IDebugExpressionEvaluator::SetLocale
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questo metodo imposta la lingua da utilizzare per creare risultati stampabili.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT SetLocale(   
   WORD wLangID  
);  
```  
  
```csharp  
int SetLocale(  
   ushort wLangID  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `wLangID`  
 [in] L'identificatore di lingua.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo può essere chiamato più volte mentre l'analizzatore di espressioni (EE) viene caricato, in modo che l'analizzatore di Espressioni deve essere in grado di cambiare la lingua in tempo reale. L'analizzatore di Espressioni Usa le impostazioni locali per restituire messaggi di errore e le stringhe nel linguaggio appropriato.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
