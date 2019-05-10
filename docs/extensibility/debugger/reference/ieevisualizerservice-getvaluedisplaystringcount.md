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
ms.openlocfilehash: e401e009cd4119704e72dec09614ec013aa9eee0
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2019
ms.locfileid: "65223556"
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