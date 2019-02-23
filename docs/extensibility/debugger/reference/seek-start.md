---
title: SEEK_START | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SEEK_START
helpviewer_keywords:
- SEEK_START enumeration
ms.assetid: 55bd8901-626e-428b-a263-23b14417f4c6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e003b74faeb7c6ed165c43380a7c4c6b0520ea0c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56677995"
---
# <a name="seekstart"></a>SEEK_START
Specifica la posizione da cui iniziare la ricerca in un flusso di disassemblaggio.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_SEEK_START { 
   SEEK_START_BEGIN       = 0x0001,
   SEEK_START_END         = 0x0002,
   SEEK_START_CURRENT     = 0x0003,
   SEEK_START_CODECONTEXT = 0x0004,
   SEEK_START_CODELOCID   = 0x0005
};
typedef DWORD SEEK_START;
```

```csharp
public enum enum_SEEK_START { 
   SEEK_START_BEGIN       = 0x0001,
   SEEK_START_END         = 0x0002,
   SEEK_START_CURRENT     = 0x0003,
   SEEK_START_CODECONTEXT = 0x0004,
   SEEK_START_CODELOCID   = 0x0005
};
```

## <a name="members"></a>Membri
 SEEK_START_BEGIN inizia la ricerca all'inizio del documento corrente.

 SEEK_START_END inizia la ricerca alla fine del documento corrente.

 SEEK_START_CURRENT inizia la ricerca in corrispondenza della posizione corrente del documento corrente.

 SEEK_START_CODECONTEXT inizia la ricerca in corrispondenza del contesto di codice specificato del documento corrente.

 SEEK_START_CODELOCID inizia la ricerca nell'identificatore percorso codice specificata. Gli identificatori di percorso di codice vengono ottenuti chiamando [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md).

## <a name="remarks"></a>Note
 Passato come argomento per il [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) (metodo).

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)
- [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)