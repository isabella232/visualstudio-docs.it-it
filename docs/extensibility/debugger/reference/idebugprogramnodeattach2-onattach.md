---
title: 'IDebugProgramNodeAttach2:: alleghi | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80721880"
---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
Si connette al programma associato o rinvia il processo di associazione al metodo di [connessione](../../../extensibility/debugger/reference/idebugengine2-attach.md) .

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
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se il metodo di [connessione](../../../extensibility/debugger/reference/idebugengine2-attach.md) non deve essere chiamato. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Osservazioni
 Questo metodo viene chiamato durante il processo di associazione, prima che venga chiamato il metodo di [associazione](../../../extensibility/debugger/reference/idebugengine2-attach.md) . Il `OnAttach` metodo può eseguire il processo di associazione stesso (in tal caso, questo metodo restituisce `S_FALSE` ) o rinviare il processo di associazione al `IDebugEngine2::Attach` Metodo (il `OnAttach` metodo restituisce `S_OK` ). In entrambi i casi, il `OnAttach` metodo può impostare l'oggetto `GUID` del programma di cui è in corso il debug nell'oggetto specificato `GUID` .

## <a name="see-also"></a>Vedere anche
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
