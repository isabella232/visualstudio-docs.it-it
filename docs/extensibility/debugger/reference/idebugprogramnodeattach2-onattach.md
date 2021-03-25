---
description: Si connette al programma associato o rinvia il processo di associazione al metodo di connessione.
title: 'IDebugProgramNodeAttach2:: alleghi | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2::OnAttach
helpviewer_keywords:
- IDebugProgramNodeAttach2::OnAttach
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 334a8e4bdf559e2d39d52a03dcf1a849f73af3e8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087262"
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

## <a name="remarks"></a>Commenti
 Questo metodo viene chiamato durante il processo di associazione, prima che venga chiamato il metodo di [associazione](../../../extensibility/debugger/reference/idebugengine2-attach.md) . Il `OnAttach` metodo può eseguire il processo di associazione stesso (in tal caso, questo metodo restituisce `S_FALSE` ) o rinviare il processo di associazione al `IDebugEngine2::Attach` Metodo (il `OnAttach` metodo restituisce `S_OK` ). In entrambi i casi, il `OnAttach` metodo può impostare l'oggetto `GUID` del programma di cui è in corso il debug nell'oggetto specificato `GUID` .

## <a name="see-also"></a>Vedi anche
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
