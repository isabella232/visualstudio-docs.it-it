---
description: Ottiene le proprietà del programma.
title: Interfaccia IDebugProgram2::GetDebugProperty | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDebugProperty
helpviewer_keywords:
- IDebugProgram2::GetDebugProperty
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e733c57b83cce517bad5680f409abe23ef1432db134276389bbb54880f4328ce
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121338878"
---
# <a name="idebugprogram2getdebugproperty"></a>IDebugProgram2::GetDebugProperty
Ottiene le proprietà del programma.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetDebugProperty( 
   IDebugProperty2** ppProperty
);
```

```csharp
int GetDebugProperty( 
   out IDebugProperty2 ppProperty
);
```

## <a name="parameters"></a>Parametri
`ppProperty`\
[out] Restituisce un [oggetto IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) che rappresenta le proprietà del programma.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Le proprietà restituite da questo metodo sono specifiche del programma. Se il programma deve restituire più di una proprietà, l'oggetto [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) restituito da questo metodo è un contenitore di proprietà aggiuntive e la chiamata al metodo [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) restituisce un elenco di tutte le proprietà.

 Un programma può esporre qualsiasi numero e tipo di proprietà aggiuntive che possono essere descritte tramite `IDebugProperty2` l'interfaccia . Un IDE potrebbe visualizzare le proprietà aggiuntive del programma tramite un'interfaccia utente generica del visualizzatore proprietà.

## <a name="see-also"></a>Vedi anche
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
