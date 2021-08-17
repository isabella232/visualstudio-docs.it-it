---
description: Rende un programma non disponibile per il debug.
title: IDebugProgramPublisher2::UnpublishProgram | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::UnpublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::UnpublishProgram
ms.assetid: 627e7d38-b2ac-4873-9a40-37ff7f47cd1d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6e51d327f8b5a6963a87c13aa7c19b2d6ab297b0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122071353"
---
# <a name="idebugprogrampublisher2unpublishprogram"></a>IDebugProgramPublisher2::UnpublishProgram
Rende un programma non disponibile per il debug.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT UnpublishProgram(
   IUnknown* pDebuggeeInterface
);
```

```csharp
int UnpublishProgram(
   object pDebuggeeInterface
);
```

## <a name="parameters"></a>Parametri
`pDebuggeeInterface`\
[in] Interfaccia `IUnknown` per il programma. Si tratta dello stesso valore fornito al metodo [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) e identifica in modo univoco il programma da rimuovere, ovvero viene usato come cookie.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Per rendere disponibile un programma per i motori di debug e la gestione del debug di sessione, usare il [metodo PublishProgram.](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)

## <a name="see-also"></a>Vedi anche
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)
