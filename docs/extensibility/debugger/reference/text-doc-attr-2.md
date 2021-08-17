---
description: Descrive gli attributi di un documento.
title: TEXT_DOC_ATTR_2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TEXT_DOC_ATTR_2
helpviewer_keywords:
- TEXT_DOC_ATTR_2 enumeration
ms.assetid: 2333b33b-042b-4ac6-9ebe-e66f95f52f51
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c479f67850af2701f68324e2270cb26e73b84458e0da5f399df0b1b26430b234
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121432982"
---
# <a name="text_doc_attr_2"></a>TEXT_DOC_ATTR_2
Descrive gli attributi di un documento.

## <a name="syntax"></a>Sintassi

```cpp
typedef DWORD TEXT_DOC_ATTR_2;
const TEXT_DOC_ATTR_2 TEXT_DOC_ATTR_READONLY_2 = 0x00000001;
```

```csharp
public const uint TEXT_DOC_ATTR_READONLY_2 = 0x00000001;
```

## <a name="members"></a>Members
 `TEXT_DOC_ATTR_READONLY_2`\
 Indica che il documento è di sola lettura.

## <a name="remarks"></a>Commenti

> [!NOTE]
> Questo valore non è effettivamente definito nell'assembly per C#. È invece necessario copiare la definizione nel file di origine.

 Passato come argomento al [metodo onUpdateDocumentAttributes.](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)
