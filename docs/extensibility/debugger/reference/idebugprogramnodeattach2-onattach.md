---
description: Si collega al programma associato o rinvia il processo di connessione al metodo Attach.
title: IDebugProgramNodeAttach2::OnAttach | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0650005ca04b01265f6e675db9426856389235caadfc36bb457280d7fbba1fb6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121402636"
---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
Si collega al programma associato o rinvia il processo di connessione al [metodo](../../../extensibility/debugger/reference/idebugengine2-attach.md) Attach.

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
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se il metodo [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) non deve essere chiamato. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Commenti
 Questo metodo viene chiamato durante il processo di connessione, prima che venga [chiamato](../../../extensibility/debugger/reference/idebugengine2-attach.md) il metodo Attach. Il metodo può eseguire il processo di connessione stesso (nel qual caso questo metodo restituisce ) o posticipare il processo di connessione al metodo `OnAttach` `S_FALSE` `IDebugEngine2::Attach` (il `OnAttach` metodo restituisce `S_OK` ). In entrambi gli eventi, `OnAttach` il metodo può impostare `GUID` l'oggetto del programma di cui si esegue il debug sull'oggetto `GUID` specificato.

## <a name="see-also"></a>Vedi anche
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
