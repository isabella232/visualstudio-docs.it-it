---
title: 'IDebugProgram2:: GetDebugProperty | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDebugProperty
helpviewer_keywords:
- IDebugProgram2::GetDebugProperty
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 33bc10aadf25eb95414cc5fd334c572b2f270429
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722889"
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

## <a name="remarks"></a>Osservazioni
 Le proprietà restituite da questo metodo sono specifiche del programma. Se il programma deve restituire più di una proprietà, l'oggetto [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) restituito da questo metodo è un contenitore di proprietà aggiuntive e la chiamata al metodo [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) restituisce un elenco di tutte le proprietà.

 Un programma può esporre qualsiasi numero e tipo di proprietà aggiuntive che possono essere descritte tramite l' `IDebugProperty2` interfaccia. Un IDE potrebbe visualizzare le proprietà aggiuntive del programma tramite un'interfaccia utente del Visualizzatore proprietà generica.

## <a name="see-also"></a>Vedere anche
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
