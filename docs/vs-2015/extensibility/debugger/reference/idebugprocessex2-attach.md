---
title: IDebugProcessEx2::Attach | Microsoft Docs
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
- IDebugProcessEx2::Attach
helpviewer_keywords:
- IDebugProcessEx2::Attach method
ms.assetid: f3334ed7-39bf-4d02-a338-36f567b9b287
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 118b86193d9241744d5faae3719ad53a593537f4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49830537"
---
# <a name="idebugprocessex2attach"></a>IDebugProcessEx2::Attach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questo metodo indica il processo a una sessione è ora il debug del processo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT Attach(   
   IDebugSession2* pSession  
);  
```  
  
```csharp  
int Attach(  
   IDebugSession2 pSession  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pSession`  
 [in] Un valore che identifica in modo univoco la sessione di connessione a questo processo.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 L'interfaccia passato `pSession` deve essere considerata solo come un cookie, un valore che identifica in modo univoco la gestione del debug sessione connessione a questo processo; nessuno dei metodi nell'interfaccia specificata sono funzionali.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)

