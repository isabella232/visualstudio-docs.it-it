---
title: IDebugProgramNode2::GetHostMachineName_V7 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetHostMachineName
helpviewer_keywords:
- IDebugProgramNode2::GetHostMachineName_V7
- IDebugProgramNode2::GetHostMachineNameIDebugProgramNode2::GetHostMachineName
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a8c328c83ebe52f842b1990debe07aed3fd764c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722089"
---
# <a name="idebugprogramnode2gethostmachinename_v7"></a>IDebugProgramNode2::GetHostMachineName_V7

> [!Note]
> Deprecato. NON UTILIZZARE.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetHostMachineName_V7 (
   BSTR* pbstrHostMachineName
);
```

```csharp
int GetHostMachineName_V7 (
   out string pbstrHostMachineName
);
```

## <a name="parameters"></a>Parametri

`pbstrHostMachineName`\
[fuori] Restituisce il nome della macchina in cui è in esecuzione il programma.

## <a name="return-value"></a>Valore restituito

Un'implementazione `E_NOTIMPL`deve sempre restituire .

## <a name="remarks"></a>Osservazioni

> [!WARNING]
> A partire da Visual Studio 2005, questo metodo `E_NOTIMPL`non viene più utilizzato e deve sempre restituire .

## <a name="see-also"></a>Vedere anche

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
