---
title: IDebugQueryEngine2::GetEngineInterface | Microsoft Docs
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
- IDebugQueryEngine2::GetEngineInterface
helpviewer_keywords:
- IDebugQueryEngine2::GetEngineInterface
ms.assetid: ed84aa98-7ec7-48f3-97ae-821090bc3664
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1d8470db2bcb8b4b1d734c7300ae4e3f5d120de1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49811880"
---
# <a name="idebugqueryengine2getengineinterface"></a>IDebugQueryEngine2::GetEngineInterface
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ottiene un'interfaccia (DE) del motore di debug personalizzato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetEngineInterface(   
   IUnknown** ppUnk  
);  
```  
  
```csharp  
int GetEngineInterface(   
   out object ppUnk  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppUnk`  
 [out] Restituisce un `IUnknown` oggetto rappresenta il motore di debug (DE), e che possano essere interrogate per qualsiasi altra interfaccia valida associata a un CRI (ad esempio [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) oppure [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)).  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 L'interfaccia risultante deve essere utilizzata con cautela perché la chiamata tramite interfacce recuperate da questo metodo consente di evitare l'elaborazione del gestore di debug della sessione e può comportare il modello SDM entrare in uno stato non valido o la generazione di errori durante il debug.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)

