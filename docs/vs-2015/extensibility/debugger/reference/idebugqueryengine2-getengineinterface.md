---
title: 'IDebugQueryEngine2:: GetEngineInterface | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugQueryEngine2::GetEngineInterface
helpviewer_keywords:
- IDebugQueryEngine2::GetEngineInterface
ms.assetid: ed84aa98-7ec7-48f3-97ae-821090bc3664
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 12bdcf9de9731095a224f394cab13f3833f126de
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158117"
---
# <a name="idebugqueryengine2getengineinterface"></a>IDebugQueryEngine2::GetEngineInterface
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ottiene un'interfaccia del motore di debug personalizzato.  
  
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
 out Restituisce un `IUnknown` oggetto che rappresenta il motore di debug (de) e su cui è possibile eseguire query per qualsiasi altra interfaccia valida associata a un de (ad esempio [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) o [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)).  
  
## <a name="return-value"></a>Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.  
  
## <a name="remarks"></a>Osservazioni  
 L'interfaccia risultante deve essere utilizzata con cautela perché la chiamata attraverso le interfacce recuperate da questo metodo aggira l'elaborazione del gestore di debug della sessione e può comportare l'ottenimento di uno stato non valido o la generazione di errori durante il debug.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
