---
description: Ottiene le proprietà del programma.
title: 'IDebugProgram2:: GetDebugProperty | Microsoft Docs'
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
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 60e551829a1f424a9bb7f89642f1d692db8d8032
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105075978"
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
out Restituisce un oggetto [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) che rappresenta le proprietà del programma.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Le proprietà restituite da questo metodo sono specifiche del programma. Se il programma deve restituire più di una proprietà, l'oggetto [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) restituito da questo metodo è un contenitore di proprietà aggiuntive e la chiamata al metodo [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) restituisce un elenco di tutte le proprietà.

 Un programma può esporre qualsiasi numero e tipo di proprietà aggiuntive che possono essere descritte tramite l' `IDebugProperty2` interfaccia. Un IDE potrebbe visualizzare le proprietà aggiuntive del programma tramite un'interfaccia utente del Visualizzatore proprietà generica.

## <a name="see-also"></a>Vedi anche
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
