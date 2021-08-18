---
description: Enumera i valori validi dei flag di eliminazione programma.
title: PROGRAM_DESTROY_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- PROGRAM_DESTROY_FLAGS enumeration
ms.assetid: be00d4a3-d5b8-4159-b632-64577f534883
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: eb1562bec3b3699d8c9b208245aa27d7c8c7558050ca307c8b0211455038a53a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121448572"
---
# <a name="program_destroy_flags"></a>PROGRAM_DESTROY_FLAGS
Enumera i valori validi dei flag di eliminazione programma.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_PPROGRAM_DESTROY_FLAGS
{
   PROGRAM_DESTROY_CONTINUE_DEBUGGING = 0x1
};
typedef DWORD PROGRAM_DESTROY_FLAGS;
```

```csharp
public enum enum_PPROGRAM_DESTROY_FLAGS
{
   PROGRAM_DESTROY_CONTINUE_DEBUGGING = 0x1
};
```

## <a name="fields"></a>Campi
 `PROGRAM_DESTROY_CONTINUE_DEBUGGING`\
 Eliminare il programma, ma continuare a eseguire il debug.

## <a name="remarks"></a>Commenti
 L'enumerazione viene restituita [dal metodo GetFlags.](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)

## <a name="requirements"></a>Requisiti
 Intestazione: Msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)
