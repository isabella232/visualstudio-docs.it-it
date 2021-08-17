---
description: Specifica le informazioni da recuperare su un oggetto IDebugField.
title: FIELD_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_INFO_FIELDS
helpviewer_keywords:
- FIELD_INFO_FIELDS enumeration
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 03b89d7337888033b2a2ce02e71d37a1340a4580
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122073032"
---
# <a name="field_info_fields"></a>FIELD_INFO_FIELDS
Specifica le informazioni da recuperare su un [oggetto IDebugField.](../../../extensibility/debugger/reference/idebugfield.md)

## <a name="syntax"></a>Sintassi

```cpp
enum enum_FIELD_INFO_FIELDS { 
    FIF_FULLNAME  = 0x0001,
    FIF_NAME      = 0x0002,
    FIF_TYPE      = 0x0004,
    FIF_MODIFIERS = 0x0008,
    FIF_ALL       = 0xffffffff,
    FIF_NONE      = 0x0000
};
typedef DWORD FIELD_INFO_FIELDS;
```

```csharp
public enum enum_FIELD_INFO_FIELDS {
    FIF_FULLNAME  = 0x0001,
    FIF_NAME      = 0x0002,
    FIF_TYPE      = 0x0004,
    FIF_MODIFIERS = 0x0008,
    FIF_ALL       = 0xffffffff,
    FIF_NONE      = 0x0000
};
```

## <a name="fields"></a>Campi
`FIF_FULLNAME`\
Inizializzare/usare `bstrFullName` il campo nella [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) struttura .

`FIF_NAME`\
Inizializzare/usare `bstrName` il campo nella struttura `FIELD_INFO` .

`FIF_TYPE`\
Inizializzare/usare `bstrType` il campo nella struttura `FIELD_INFO` .

`FIF_MODIFIERS`\
Inizializzare/usare `bstrModifiers` il campo nella struttura `FIELD_INFO` .

## <a name="remarks"></a>Commenti
Questi valori vengono passati anche come argomento al [metodo GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) per specificare i campi della struttura FIELD_INFO da inizializzare. [](../../../extensibility/debugger/reference/field-info.md)

Questi valori vengono usati anche nel membro della struttura per indicare `dwFields` quali campi vengono usati e `FIELD_INFO` validi.

Questi flag possono essere combinati con un oggetto bit per `OR` bit.

## <a name="requirements"></a>Requisiti
Intestazione: sh.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
