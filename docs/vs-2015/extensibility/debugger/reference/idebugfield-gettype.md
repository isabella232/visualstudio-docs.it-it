---
title: 'IDebugField:: GetType | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugField::GetType
helpviewer_keywords:
- IDebugField::GetType method
ms.assetid: b3cdec9f-ef7b-44d0-a775-d17ef7eae968
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d076b97ac777a56befdfa7d60a56361906ea3965
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148940"
---
# <a name="idebugfieldgettype"></a>IDebugField::GetType
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questo metodo ottiene il tipo di campo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetType(   
   IDebugField** ppType  
);  
```  
  
```csharp  
int GetType(  
   out IDebugField ppType  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppType`  
 out Restituisce il tipo di campo come un altro oggetto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .  
  
## <a name="return-value"></a>Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
