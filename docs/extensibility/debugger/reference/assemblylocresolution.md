---
title: ASSEMBLYLOCRESOLUTION . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ASSEMBLYLOCRESOLUTION
helpviewer_keywords:
- ASSEMBLYLOCRESOLUTION enumeration
ms.assetid: 0bcfe85c-5f37-4a9d-bf2b-141acd96ad67
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cbd015408cbefd1861f6e795447a5302efabb0dc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738145"
---
# <a name="assemblylocresolution"></a>ASSEMBLYLOCRESOLUTION
Specifica dove si trova un assieme.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_ASSEMBLYLOCRESOLUTION {
    ALR_NAME      = 0x0,
    ALR_USERDIR   = 0x1,
    ALR_SHAREDDIR = 0x2,
    ALR_REMOTEDIR = 0x4,
};
typedef DWORD ASSEMBLYLOCRESOLUTION;
```

```csharp
public enum enum_ASSEMBLYLOCRESOLUTION {
    ALR_NAME      = 0x0,
    ALR_USERDIR   = 0x1,
    ALR_SHAREDDIR = 0x2,
    ALR_REMOTEDIR = 0x4,
};
```

## <a name="fields"></a>Campi
`ALR_NAME`\
L'assembly si trova nello spazio dei nomi corrente.

`ALR_USERDIR`\
L'assembly si trova in una directory utente.

`ALR_SHAREDDIR`\
L'assembly si trova nella directory condivisa.

`ALR_REMOTEDIR`\
L'assembly si trova in una directory remota.

## <a name="remarks"></a>Osservazioni
Questi valori vengono restituiti dai metodi [ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md) e [GetManagedViewerCreationData.](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)

Questi valori possono essere `OR` combinati con l'operazione.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)
- [GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)
