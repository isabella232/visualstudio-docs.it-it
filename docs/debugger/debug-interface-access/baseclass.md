---
title: BaseClass | Microsoft Docs
description: Trovare informazioni di riferimento sul tipo di simbolo BaseClass. Una classe di base per i simboli di tipo definito dall'utente (UDT) viene identificata da un elemento figlio con un tag SymTagBaseClass.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- user-defined types, base classes
- BaseClass symbol
- base classes, user-defined types
ms.assetid: 9375ca35-cb91-45f5-8903-7344ee4528e8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 11c59ded5e3572eb0573738414f14e2804f4f177
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122129600"
---
# <a name="baseclass"></a>BaseClass
Ogni classe di base per un simbolo di tipo definito dall'utente (UDT) viene identificata da un elemento figlio con un `SymTagBaseClass` tag . La [proprietà IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md) contiene il simbolo per il tipo definito dall'utente sottostante e tutte le proprietà del tipo definito dall'utente sottostante sono disponibili come parte di questo simbolo BaseClass.

## <a name="properties"></a>Proprietà
 La tabella seguente illustra proprietà valide aggiuntive per questo tipo di simbolo.

|Proprietà|Tipo di dati|Descrizione|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|`DWORD`|Modificatore di accesso applicato a questa classe di base. Uno dei valori [CV_access_e Enumeration.](../../debugger/debug-interface-access/cv-access-e.md)|
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|Simbolo della classe contenitore (se presente).|
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|ID del simbolo padre della classe.|
|[IDiaSymbol::get_constructor](../../debugger/debug-interface-access/idiasymbol-get-constructor.md)|`BOOL`|`TRUE` se la classe di base ha un costruttore.|
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` se la classe di base è contrassegnata come const.|
|[IDiaSymbol::get_hasAssignmentOperator](../../debugger/debug-interface-access/idiasymbol-get-hasassignmentoperator.md)|`BOOL`|`TRUE` se la classe di base dispone di un operatore di assegnazione.|
|[IDiaSymbol::get_hasCastOperator](../../debugger/debug-interface-access/idiasymbol-get-hascastoperator.md)|`BOOL`|`TRUE` se la classe di base dispone di un operatore cast.|
|[IDiaSymbol::get_hasNestedTypes](../../debugger/debug-interface-access/idiasymbol-get-hasnestedtypes.md)|`BOOL`|`TRUE` se la classe di base dispone di tipi annidati.|
|[IDiaSymbol::get_indirectVirtualBaseClass](../../debugger/debug-interface-access/idiasymbol-get-indirectvirtualbaseclass.md)|`BOOL`|`TRUE` se la classe di base è indiretta.|
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`DWORD`|Lunghezza di questa classe di base in byte.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Simbolo del compilando contenitore.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID del simbolo padre lessicale.|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Nome della classe di base.|
|[IDiaSymbol::get_nested](../../debugger/debug-interface-access/idiasymbol-get-nested.md)|`BOOL`|`TRUE` se la classe di base è annidata.|
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|`LONG`|Offset del sottooggetto che rappresenta la classe di base all'interno della struttura .|
|[IDiaSymbol::get_overloadedOperator](../../debugger/debug-interface-access/idiasymbol-get-overloadedoperator.md)|`BOOL`|`TRUE` se la classe di base contiene operatori di overload.|
|[IDiaSymbol::get_packed](../../debugger/debug-interface-access/idiasymbol-get-packed.md)|`BOOL`|`TRUE` se la classe di base è di tipo pack.|
|[IDiaSymbol::get_scoped](../../debugger/debug-interface-access/idiasymbol-get-scoped.md)|`BOOL`|`TRUE` se la classe di base viene visualizzata in un ambito non globale.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID indice del simbolo.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Restituisce `SymTagBaseClass` (uno dei [valori dell'enumerazione SymTagEnum).](../../debugger/debug-interface-access/symtagenum.md)|
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Simbolo per il tipo definito dall'utente [della classe di](../../debugger/debug-interface-access/udt.md)base.|
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|ID del simbolo del tipo.|
|[IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)|`DWORD`|Valore [dell'enumerazione UdtKind](../../debugger/debug-interface-access/udtkind.md).|
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` se la classe base non è allineata.|
|[IDiaSymbol::get_virtualBaseClass](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseclass.md)|`BOOL`|`TRUE` se la classe di base è virtuale.|
|[IDiaSymbol::get_virtualBaseDispIndex](../../debugger/debug-interface-access/idiasymbol-get-virtualbasedispindex.md)|`DWORD`|Indice nella tabella di spostamento della base virtuale.|
|[IDiaSymbol::get_virtualBasePointerOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbasepointeroffset.md)|`LONG`|Offset del puntatore di base virtuale.|
|[IDiaSymbol::get_virtualBaseTableType](../../debugger/debug-interface-access/idiasymbol-get-virtualbasetabletype.md)|`IDiaSymbol*`|Tipo del puntatore della tabella di base virtuale.|
|[IDiaSymbol::get_virtualTableShape](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshape.md)|`IDiaSymbol*`|Simbolo che descrive il tipo di tabella virtuale per questa classe di base.|
|[IDiaSymbol::get_virtualTableShapeId](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshapeid.md)|`DWORD`|ID del simbolo della forma della tabella virtuale.|
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` se la classe di base è contrassegnata come volatile.|

## <a name="see-also"></a>Vedi anche
- [Gerarchia di classi dei tipi di simboli](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)
- [UDT](../../debugger/debug-interface-access/udt.md)