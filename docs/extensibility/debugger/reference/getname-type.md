---
title: GETNAME_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- GETNAME_TYPE
helpviewer_keywords:
- GETNAME_TYPE enumeration
ms.assetid: 2f9f1679-e9e8-4c9c-ac90-aa07bfe69914
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1bdcbc4171c8a481ee0c45456ef5600f5150c6d0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317588"
---
# <a name="getnametype"></a>GETNAME_TYPE
Specifica il tipo di nome di file da recuperare.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_GETNAME_TYPE {
    GN_NAME         = 0,
    GN_FILENAME     = 1,
    GN_BASENAME     = 2,
    GN_MONIKERNAME  = 3,
    GN_URL          = 4,
    GN_TITLE        = 5,
    GN_STARTPAGEURL = 6
};
typedef DWORD GETNAME_TYPE;
```

```csharp
public enum enum_GETNAME_TYPE {
    GN_NAME         = 0,
    GN_FILENAME     = 1,
    GN_BASENAME     = 2,
    GN_MONIKERNAME  = 3,
    GN_URL          = 4,
    GN_TITLE        = 5,
    GN_STARTPAGEURL = 6
};
```

## <a name="fields"></a>Campi
`GN_NAME`\
Specifica un nome descrittivo del documento o del contesto.

`GN_FILENAME`\
Specifica il percorso completo del documento o del contesto.

`GN_BASENAME`\
Specifica un nome di file di base anziché un percorso completo del documento o del contesto.

`GN_MONIKERNAME`\
Specifica un nome univoco del documento o del contesto sotto forma di un moniker.

`GN_URL`\
Specifica il nome dell'URL del documento o del contesto.

`GN_TITLE`\
Specifica un titolo del documento, se presente.

`GN_STARTPAGEURL`\
Ottiene l'URL della pagina iniziale per i processi.

## <a name="remarks"></a>Note
Questi valori vengono passati come parametri per il [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md), [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md), e [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) metodi per specificare il tipo di nome da restituire.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)
- [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)
- [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)
