---
description: Specifica il tipo di informazioni sui simboli da recuperare.
title: SYMBOL_SEARCH_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SYMBOL_SEARCH_INFO_FIELDS
helpviewer_keywords:
- SYMBOL_SEARCH_INFO_FIELDS enumeration
ms.assetid: bce35af0-722d-46d4-afa6-eaae598c51ff
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 16c9ea9aebd562a88963bfd1f23aac3805c095a6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122102974"
---
# <a name="symbol_search_info_fields"></a>SYMBOL_SEARCH_INFO_FIELDS
Specifica il tipo di informazioni sui simboli da recuperare.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_SYMBOL_SEARCH_INFO_FIELDS
{
   SSIF_NONE                = 0x00000000,
   SSIF_VERBOSE_SEARCH_INFO = 0x00000001
};
typedef DWORD SYMBOL_SEARCH_INFO_FIELDS;
```

```csharp
public enum enum_SYMBOL_SEARCH_INFO_FIELDS
{
   SSIF_NONE                = 0x00000000,
   SSIF_VERBOSE_SEARCH_INFO = 0x00000001
};

```

## <a name="fields"></a>Campi
 `SSIF_NONE`\
 Indica che non sono presenti flag

 `SSIF_VERBOSE_SEARCH_INFO`\
 Restituisce tutti i percorsi di ricerca usati per la ricerca dei simboli

## <a name="remarks"></a>Commenti
 Questi flag vengono passati come parametro al [metodo GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) per determinare la quantità di informazioni restituite.

> [!NOTE]
> Attualmente è `SSIF_VERBOSE_SEARCH_INFO` supportato solo e deve essere specificato come parametro per `dwFlags` `IDebugModule3::GetSymbolInfo` . Tutti gli altri valori restituiscono un errore.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)
