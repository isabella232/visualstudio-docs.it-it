---
title: IDebugQueryEngine2::GetEngineInterface | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugQueryEngine2::GetEngineInterface
helpviewer_keywords:
- IDebugQueryEngine2::GetEngineInterface
ms.assetid: ed84aa98-7ec7-48f3-97ae-821090bc3664
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: af67f4589682cc3c0ecf42653374521c011115c2
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/09/2019
ms.locfileid: "65457520"
---
# <a name="idebugqueryengine2getengineinterface"></a>IDebugQueryEngine2::GetEngineInterface
Ottiene un'interfaccia (DE) del motore di debug personalizzato.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetEngineInterface( 
   IUnknown** ppUnk
);
```

```csharp
int GetEngineInterface( 
   out object ppUnk
);
```

## <a name="parameters"></a>Parametri
 `ppUnk`\

 [out] Restituisce un `IUnknown` oggetto rappresenta il motore di debug (DE), e che possano essere interrogate per qualsiasi altra interfaccia valida associata a un CRI (ad esempio [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) oppure [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)).

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 L'interfaccia risultante deve essere utilizzata con cautela perché la chiamata tramite interfacce recuperate da questo metodo consente di evitare l'elaborazione del gestore di debug della sessione e può comportare il modello SDM entrare in uno stato non valido o la generazione di errori durante il debug.

## <a name="see-also"></a>Vedere anche
- [IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)