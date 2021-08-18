---
description: Ottiene un'interfaccia del motore di debug personalizzato.
title: Interfaccia IDebugQueryEngine2::GetEngineInterface | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugQueryEngine2::GetEngineInterface
helpviewer_keywords:
- IDebugQueryEngine2::GetEngineInterface
ms.assetid: ed84aa98-7ec7-48f3-97ae-821090bc3664
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5458ec92e121fcfe954e03a660370ec207d3ba55
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122118631"
---
# <a name="idebugqueryengine2getengineinterface"></a>IDebugQueryEngine2::GetEngineInterface
Ottiene un'interfaccia del motore di debug personalizzato.

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
[out] Restituisce un oggetto che rappresenta il motore di debug (DE) e su cui è possibile eseguire query per qualsiasi altra interfaccia valida associata a un de , ad esempio `IUnknown` [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) o [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md).

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 L'interfaccia risultante deve essere usata con cautela perché la chiamata tramite le interfacce recuperate da questo metodo elude l'elaborazione del gestore di debug della sessione e può causare che SDM si acceda a uno stato non valido o generi errori durante il debug.

## <a name="see-also"></a>Vedi anche
- [IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
