---
title: 'IEEVisualizerService:: GetValueDisplayStringCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IEEVisualizerService::GetValueDisplayStringCount
- GetValueDisplayStringCount
ms.assetid: d683a833-fbfb-4042-84df-6905124a268a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 97b06179027549c0bebe83b2b4866e53c8fd9569
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99842261"
---
# <a name="ieevisualizerservicegetvaluedisplaystringcount"></a>IEEVisualizerService::GetValueDisplayStringCount
Recupera il numero di stringhe di valore da visualizzare per la proprietà o il campo specificati.

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
in Valore dell'enumerazione [DisplayKind](../../../extensibility/debugger/reference/displaykind.md) .

`propertyOrField`\
in Interfaccia [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) che rappresenta una proprietà o un campo.

`pcelt`\
out Restituisce il numero di stringhe di valore da visualizzare.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
