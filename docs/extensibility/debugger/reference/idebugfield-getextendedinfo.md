---
title: IDebugField::GetExtendedInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetExtendedInfo
helpviewer_keywords:
- IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fc37cd9cff4956d000441a632f84a6155f9b9586
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212208"
---
# <a name="idebugfieldgetextendedinfo"></a>IDebugField::GetExtendedInfo
Questo metodo ottiene estesi informazioni su un campo.

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
[in] Consente di selezionare le informazioni da restituire. I valori validi sono:

|Value|Descrizione|
|-----------|-----------------|
|`guidConstantValue`|Il valore come una sequenza di byte.|
|`guidConstantType`|Il tipo come una firma di tipo.|

`prgBuffer`\
[out] Restituisce le informazioni estese.

`pdwLen`\
[in, out] Restituisce le dimensioni delle informazioni estese, in byte.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Attualmente, questo metodo restituisce solo il tipo o il valore di una costante. Il chiamante deve liberare il buffer restituito `prgBuffer` chiamando il metodo COM `CoTaskMemFree` funzione (C++) o <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> (c#).

## <a name="see-also"></a>Vedere anche
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)