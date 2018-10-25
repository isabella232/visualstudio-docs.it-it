---
title: IDebugProgramNode2::GetHostMachineName_V7 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramNode2::GetHostMachineName
helpviewer_keywords:
- IDebugProgramNode2::GetHostMachineName_V7
- IDebugProgramNode2::GetHostMachineNameIDebugProgramNode2::GetHostMachineName
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9ed7eb9c98ad8da45a50af79918480e74d76779e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49908548"
---
# <a name="idebugprogramnode2gethostmachinenamev7"></a>IDebugProgramNode2::GetHostMachineName_V7

> [!Note]
> DEPRECATO. NON USARE.

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

#### <a name="parameters"></a>Parametri

`pbstrHostMachineName`  
[out] Restituisce il nome del computer in cui viene eseguito il programma.

## <a name="return-value"></a>Valore restituito

Un'implementazione deve sempre restituire `E_NOTIMPL`.

## <a name="remarks"></a>Note

> [!WARNING]
> A partire da Visual Studio 2005, questo metodo non viene più usato e deve sempre restituire `E_NOTIMPL`.

## <a name="see-also"></a>Vedere anche

[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)