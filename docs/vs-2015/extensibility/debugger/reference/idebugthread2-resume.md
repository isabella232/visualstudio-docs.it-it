---
title: 'IDebugThread2:: Resume | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugThread2::Resume
helpviewer_keywords:
- IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5bdec7338864926187b3d5056ffd2f2c4e1d7824
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152988"
---
# <a name="idebugthread2resume"></a>IDebugThread2::Resume
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Riprende l'esecuzione di un thread.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT Resume (   
   DWORD *pdwSuspendCount  
);  
```  
  
```csharp  
int Resume (   
   out uint pdwSuspendCount  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pdwSuspendCount`  
 out Restituisce il conteggio di sospensione dopo l'operazione di ripresa.  
  
## <a name="return-value"></a>Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.  
  
## <a name="remarks"></a>Osservazioni  
 Ogni chiamata a questo metodo decrementa il conteggio di sospensione fino a quando non raggiunge 0, a quel punto, l'esecuzione viene ripresa. Questo numero di Sospendi viene visualizzato nella finestra debug **thread** .  
  
 Per ogni chiamata a questo metodo, deve essere presente una chiamata precedente al metodo [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md) . Il conteggio di sospensione determina il numero di volte in `IDebugThread2::Suspend` cui il metodo è stato chiamato finora.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Sospendi](../../../extensibility/debugger/reference/idebugthread2-suspend.md)
