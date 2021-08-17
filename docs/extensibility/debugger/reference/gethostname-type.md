---
description: Specifica il tipo di nome host.
title: GETHOSTNAME_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- GETHOSTNAME_TYPE
helpviewer_keywords:
- GETHOSTNAME_TYPE enumeration
ms.assetid: 2be92bea-8133-412b-9015-1833baf16e1b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d16e9b2ce7e8320aeba97856f9beb883ffd5fe5d2504adbff64336007144d655
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121293287"
---
# <a name="gethostname_type"></a>GETHOSTNAME_TYPE
Specifica il tipo di nome host.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_GETHOSTNAME_TYPE {
    GHN_FRIENDLY_NAME = 0,
    GHN_FILE_NAME     = 1
};
typedef DWORD GETHOSTNAME_TYPE;
```

```csharp
public enum enum_GETHOSTNAME_TYPE {
    GHN_FRIENDLY_NAME = 0,
    GHN_FILE_NAME     = 1
};
```

## <a name="fields"></a>Campi
`GHN_FRIENDLY_NAME`\
Specifica un nome descrittivo dell'host.

`GHN_FILE_NAME`\
Specifica un nome file dell'host.

## <a name="remarks"></a>Commenti
Questi valori vengono passati come argomento al [metodo GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) per recuperare un nome host in formati diversi.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)
