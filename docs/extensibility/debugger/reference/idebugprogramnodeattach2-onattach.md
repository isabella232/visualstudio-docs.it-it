---
title: IDebugProgramNodeAttach2::OnAttach Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2::OnAttach
helpviewer_keywords:
- IDebugProgramNodeAttach2::OnAttach
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dfb8a39af3c030dadddcb148a79a96b57f20e183
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721880"
---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
Si connette al programma associato o rinvia il processo di collegamento al metodo [Attach.](../../../extensibility/debugger/reference/idebugengine2-attach.md)

## <a name="syntax"></a>Sintassi

```cpp
HRESULT OnAttach(
   [in] REFGUID guidProgramId
);
```

```csharp
int OnAttach(
   ref Guid guidProgramId
};
```

## <a name="parameters"></a>Parametri
`guidProgramId`\
[in] `GUID` da assegnare al programma associato.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se il [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) metodo non deve essere chiamato. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Osservazioni
 Questo metodo viene chiamato durante il processo di collegamento, prima di [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) metodo viene chiamato. Il `OnAttach` metodo può eseguire il processo di collegamento `S_FALSE`stesso (nel qual caso, questo `OnAttach` metodo `S_OK`restituisce ) o rinviare il processo di collegamento al `IDebugEngine2::Attach` metodo (il metodo restituisce ). In entrambi i `OnAttach` casi, `GUID` il metodo può impostare l'oggetto del programma sottoposto a debug sull'oggetto specificato. `GUID`

## <a name="see-also"></a>Vedere anche
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
