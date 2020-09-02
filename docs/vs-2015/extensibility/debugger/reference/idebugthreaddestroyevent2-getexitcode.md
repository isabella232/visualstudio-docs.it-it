---
title: 'IDebugThreadDestroyEvent2:: GetExitCode | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugThreadDestroyEvent2::GetExitCode
helpviewer_keywords:
- IDebugThreadDestroyEvent2::GetExitCode
ms.assetid: 8bf47a17-f811-4d9b-bcea-7488908830ff
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 93829c194e228309535f89f3ce39187e66e03ba6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62555684"
---
# <a name="idebugthreaddestroyevent2getexitcode"></a>IDebugThreadDestroyEvent2::GetExitCode
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ottiene il codice di uscita per un thread.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetExitCode (   
   DWORD* pdwExit  
);  
```  
  
```csharp  
int GetExitCode (   
   out uint pdwExit  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pdwExit`  
 out Restituisce il codice di uscita del thread.  
  
## <a name="return-value"></a>Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)
