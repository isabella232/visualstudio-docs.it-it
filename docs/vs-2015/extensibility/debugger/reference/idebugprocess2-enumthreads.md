---
title: IDebugProcess2::EnumThreads | Microsoft Docs
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
- IDebugProcess2::EnumThreads
helpviewer_keywords:
- IDebugProcess2::EnumThreads
ms.assetid: 05677385-7a7f-4545-8438-af00dde85db0
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 30fb71dbb1fa6edbce9201cd757dd96f401f1e5e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47528780"
---
# <a name="idebugprocess2enumthreads"></a>IDebugProcess2::EnumThreads
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugProcess2::EnumThreads](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprocess2-enumthreads).  
  
Recupera un elenco di tutti i thread in esecuzione nel processo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT EnumThreads(  
   IEnumDebugThreads2** ppEnum  
);  
```  
  
```csharp  
int EnumThreads(  
   out IEnumDebugThreads2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppEnum`  
 [out] Restituisce un [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md) oggetto che contiene un elenco di tutti i thread in tutti i programmi nel processo.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo enumera i thread in esecuzione in ciascun programma e quindi le combina in una vista di processo dei thread. Un singolo thread possono essere eseguite in più programmi; Questo metodo enumera solo una volta tale thread.  
  
 Questo metodo presenta un elenco di thread del processo senza duplicati. In caso contrario, per enumerare i thread in esecuzione in un particolare programma, usare il [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) (metodo).  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)

