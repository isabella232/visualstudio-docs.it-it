---
title: Proprietà IDebugProgramPublisher2::UnpublishProgram . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::UnpublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::UnpublishProgram
ms.assetid: 627e7d38-b2ac-4873-9a40-37ff7f47cd1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1fa3d111559a2c82fe36def202e5c1cf120c5202
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721594"
---
# <a name="idebugprogrampublisher2unpublishprogram"></a>IDebugProgramPublisher2::UnpublishProgram
Rende non disponibile un programma per il debug.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT UnpublishProgram(
   IUnknown* pDebuggeeInterface
);
```

```csharp
int UnpublishProgram(
   object pDebuggeeInterface
);
```

## <a name="parameters"></a>Parametri
`pDebuggeeInterface`\
[in] Un'interfaccia `IUnknown` al programma. Si tratta dello stesso valore fornito per il [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) metodo e identifica in modo univoco il programma da rimuovere (vale a dire, viene utilizzato come cookie).

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Per rendere un programma disponibile per i motori di debug e il gestore di debug delle sessioni, utilizzare il [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) metodo.

## <a name="see-also"></a>Vedere anche
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)
