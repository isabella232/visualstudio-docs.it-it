---
title: IDebugProgramPublisher2::UnpublishProgram | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::UnpublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::UnpublishProgram
ms.assetid: 627e7d38-b2ac-4873-9a40-37ff7f47cd1d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0f633b7cd41a9e19179ba5daf22fdd66e9749ad5
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56698651"
---
# <a name="idebugprogrampublisher2unpublishprogram"></a>IDebugProgramPublisher2::UnpublishProgram
Rende non disponibile per eseguire il debug di un programma.

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

#### <a name="parameters"></a>Parametri
 `pDebuggeeInterface`

 [in] Un `IUnknown` interfaccia al programma. Questo è lo stesso valore fornito per il [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) (metodo) e identifica in modo univoco il programma viene rimosso (vale a dire, viene usato come un cookie).

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Per rendere disponibile un programma per i motori di debug e gestione del debug della sessione, usare il [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) (metodo).

## <a name="see-also"></a>Vedere anche
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)