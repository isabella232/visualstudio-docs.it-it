---
title: IDebugCanStopEvent2::CanStop | Microsoft Docs
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
- IDebugCanStopEvent2::CanStop
helpviewer_keywords:
- IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 65095961510bd80758cbf94c4d9aa8811f61a9fe
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47531774"
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugCanStopEvent2::CanStop](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugcanstopevent2-canstop).  
  
Notifica al motore di debug (DE) per interrompere in corrispondenza della posizione di codice corrente o semplicemente continuare l'esecuzione o meno.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT CanStop (   
   BOOL fCanStop  
);  
```  
  
```csharp  
int CanStop (   
   int fCanStop  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `fCanStop`  
 [in] Diverso da zero (`TRUE`) se la Germania deve essere interrotta in corrispondenza della posizione di codice corrente; in caso contrario, zero (`FALSE`).  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il ricevitore dell'evento chiama in genere il [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) metodo per determinare il motivo per la Germania desidera arrestare e quindi chiama il `IDebugCanStopEvent2::CanStop` metodo con la risposta appropriata.  
  
 Se si arresta la Germania, invia un evento che descrive il motivo dell'arresto. In genere esistono due eventi che vengono inviati, rappresentata da un'interruzione di utente o un segnale i [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) interfaccia e un evento punto di interruzione rappresentato dal [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) interfaccia.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)

