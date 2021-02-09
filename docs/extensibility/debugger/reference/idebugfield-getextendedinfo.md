---
title: 'IDebugField:: GetExtendedInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetExtendedInfo
helpviewer_keywords:
- IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 911556cb615e373d620b496fb31e5d6093b7cc37
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869934"
---
# <a name="idebugfieldgetextendedinfo"></a>IDebugField::GetExtendedInfo
Questo metodo ottiene le informazioni estese su un campo.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetExtendedInfo( 
   REFGUID guidExtendedInfo,
   BYTE**  prgBuffer,
   DWORD*  pdwLen
);
```

```csharp
int GetExtendedInfo(
   ref Guid guidExtendedInfo,
   IntPtr[] prgBuffer,
   ref uint pdwLen
);
```

## <a name="parameters"></a>Parametri
`guidExtendedInfo`\
in Seleziona le informazioni da restituire. I valori validi sono:

|valore|Descrizione|
|-----------|-----------------|
|`guidConstantValue`|Valore come sequenza di byte.|
|`guidConstantType`|Tipo come firma del tipo.|

`prgBuffer`\
out Restituisce le informazioni estese.

`pdwLen`\
[in, out] Restituisce la dimensione, in byte, delle informazioni estese.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Attualmente, questo metodo restituisce solo il tipo o il valore di una costante. Il chiamante deve liberare il buffer restituito in chiamando la `prgBuffer` funzione com `CoTaskMemFree` (C++) o <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> (C#).

## <a name="see-also"></a>Vedi anche
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
