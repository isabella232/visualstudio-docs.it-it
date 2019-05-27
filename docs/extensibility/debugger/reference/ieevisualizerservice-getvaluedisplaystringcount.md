---
title: IEEVisualizerService::GetValueDisplayStringCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IEEVisualizerService::GetValueDisplayStringCount
- GetValueDisplayStringCount
ms.assetid: d683a833-fbfb-4042-84df-6905124a268a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cbd7bd7655769668ce2a279150f444fd196235fb
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212606"
---
# <a name="ieevisualizerservicegetvaluedisplaystringcount"></a>IEEVisualizerService::GetValueDisplayStringCount
Recupera il numero di stringhe di valori da visualizzare per la proprietà specificata o il campo.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetValueDisplayStringCount (
   DWORD         displayKind,
   IDebugField * propertyOrField,
   ULONG *       pcelt
);
```

```csharp
int GetValueDisplayStringCount (
   uint        displayKind,
   IDebugField propertyOrField,
   out ulong   pcelt
);
```

## <a name="parameters"></a>Parametri
`displayKind`\
[in] Valore di [DisplayKind](../../../extensibility/debugger/reference/displaykind.md) enumerazione.

`propertyOrField`\
[in] Un' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfaccia che rappresenta una proprietà o campo.

`pcelt`\
[out] Restituisce il numero di stringhe di valori da visualizzare.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)