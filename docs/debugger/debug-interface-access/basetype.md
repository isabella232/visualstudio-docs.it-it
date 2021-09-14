---
title: BaseType | Microsoft Docs
description: Trovare informazioni di riferimento sul tipo di simbolo BaseType (SymTagBaseType) nell'SDK Visual Studio di accesso all'interfaccia di debug.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- BaseType symbol [DIA SDK]
ms.assetid: 2f9e22e6-8360-496a-ac6b-17a5a56b0c46
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 6afb4b2bfd99a8f944ab0d5d3d2a27e2c521371f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630756"
---
# <a name="basetype"></a>BaseType
I tipi di base sono identificati dai `SymTagBaseType` simboli.

## <a name="properties"></a>Proprietà
 La tabella seguente illustra proprietà valide aggiuntive per questo tipo di simbolo.

|Proprietà|Tipo di dati|Descrizione|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)|`DWORD`|Uno dei valori dell'enumerazione [BasicType](../../debugger/debug-interface-access/basictype.md).|
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` se il tipo di base è contrassegnato come const.|
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`LONGLONG`|Dimensione, in byte, del tipo di base.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Simbolo dell'oggetto [Compiland che lo racchiude.](../../debugger/debug-interface-access/compiland.md)|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID del simbolo padre lessicale.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID indice del simbolo.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Restituisce `SymTagBaseType` (uno dei [valori dell'enumerazione SymTagEnum).](../../debugger/debug-interface-access/symtagenum.md)|
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` se il tipo di base non è allineato.|
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` se il tipo di base è contrassegnato come volatile.|

## <a name="see-also"></a>Vedi anche
- [Enumerazione BasicType](../../debugger/debug-interface-access/basictype.md)
- [Gerarchia di classi dei tipi di simboli](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)