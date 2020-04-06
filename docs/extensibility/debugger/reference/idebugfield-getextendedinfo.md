---
title: Proprietà IDebugField::GetExtendedInfo . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetExtendedInfo
helpviewer_keywords:
- IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dc414dd57e86149e38d7c85d11252eb93efced51
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728870"
---
# <a name="idebugfieldgetextendedinfo"></a>IDebugField::GetExtendedInfo
Questo metodo ottiene informazioni estese su un campo.

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
[in] Seleziona le informazioni da restituire. I valori validi sono:

|valore|Descrizione|
|-----------|-----------------|
|`guidConstantValue`|Valore come sequenza di byte.|
|`guidConstantType`|Tipo come firma del tipo.|

`prgBuffer`\
[fuori] Restituisce le informazioni estese.

`pdwLen`\
[in, out] Restituisce la dimensione delle informazioni estese, in byte.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Attualmente, questo metodo restituisce solo il tipo o il valore di una costante. Il chiamante deve liberare `prgBuffer` il buffer `CoTaskMemFree` restituito chiamando la funzione <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> di COM (C ) o (C ) o (C ) o (C ) .

## <a name="see-also"></a>Vedere anche
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
