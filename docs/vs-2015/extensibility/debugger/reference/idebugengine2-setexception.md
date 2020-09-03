---
title: 'IDebugEngine2:: seexception | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetException
helpviewer_keywords:
- IDebugEngine2::SetException
ms.assetid: e6f5ec48-09e8-4b9b-9dc9-55f8d883f1b7
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1a7001b502d3d0296ab35d3753c7c2ac0ddc5623
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195968"
---
# <a name="idebugengine2setexception"></a>IDebugEngine2::SetException
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Specifica il modo in cui il motore di debug (DE) deve gestire un'eccezione specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT SetException(   
   EXCEPTION_INFO* pException  
);  
```  
  
```csharp  
int SetException(   
   EXCEPTION_INFO[] pException  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pException`  
 in Struttura [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) che descrive l'eccezione e come eseguirne il debug.  
  
## <a name="return-value"></a>Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.  
  
## <a name="remarks"></a>Osservazioni  
 È possibile che venga richiesto all'utente di arrestare il programma che genera un'eccezione al primo tentativo, alla seconda possibilità o non a tutti.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
