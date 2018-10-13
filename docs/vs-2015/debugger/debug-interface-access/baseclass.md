---
title: BaseClass | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- user-defined types, base classes
- BaseClass symbol
- base classes, user-defined types
ms.assetid: 9375ca35-cb91-45f5-8903-7344ee4528e8
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 86da35d23af05b318bcecf950064e5d8de23df0a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49242086"
---
# <a name="baseclass"></a>BaseClass
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ogni classe di base per un simbolo tipo definito dall'utente (UDT) è identificato da un elemento figlio con un `SymTagBaseClass` tag. Il [Get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md) proprietà contiene il simbolo per il tipo definito dall'utente sottostante e tutte le proprietà del tipo sottostante in questione sono disponibili come parte di questo simbolo BaseClass.  
  
## <a name="properties"></a>Proprietà  
 Nella tabella seguente mostra ulteriori proprietà valida per questo tipo di simbolo.  
  
|Proprietà|Tipo di dati|Descrizione|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|`DWORD`|Modificatore di accesso applicate a questa classe di base. Uno dei [enumerazione CV_access_e](../../debugger/debug-interface-access/cv-access-e.md) valori.|  
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|Simbolo della classe contenitore (se presente).|  
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|ID del simbolo classe padre.|  
|[IDiaSymbol::get_constructor](../../debugger/debug-interface-access/idiasymbol-get-constructor.md)|`BOOL`|`TRUE` Se la classe di base ha un costruttore.|  
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` Se la classe di base è contrassegnata come const.|  
|[IDiaSymbol::get_hasAssignmentOperator](../../debugger/debug-interface-access/idiasymbol-get-hasassignmentoperator.md)|`BOOL`|`TRUE` Se la classe base ha un operatore di assegnazione.|  
|[IDiaSymbol::get_hasCastOperator](../../debugger/debug-interface-access/idiasymbol-get-hascastoperator.md)|`BOOL`|`TRUE` Se la classe base ha un operatore cast.|  
|[IDiaSymbol::get_hasNestedTypes](../../debugger/debug-interface-access/idiasymbol-get-hasnestedtypes.md)|`BOOL`|`TRUE` Se la classe di base include i tipi annidati.|  
|[IDiaSymbol::get_indirectVirtualBaseClass](../../debugger/debug-interface-access/idiasymbol-get-indirectvirtualbaseclass.md)|`BOOL`|`TRUE` Se la classe base indiretta.|  
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`DWORD`|Lunghezza di questa classe di base in byte.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Simbolo di compilando l'inclusione.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID del simbolo lessicale padre.|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Nome della classe di base.|  
|[IDiaSymbol::get_nested](../../debugger/debug-interface-access/idiasymbol-get-nested.md)|`BOOL`|`TRUE` Se la classe di base è annidata.|  
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|`LONG`|Offset del sotto-oggetto che rappresenta la classe base all'interno della struttura.|  
|[IDiaSymbol::get_overloadedOperator](../../debugger/debug-interface-access/idiasymbol-get-overloadedoperator.md)|`BOOL`|`TRUE` Se la classe di base dispone di tutti gli operatori di overload.|  
|[IDiaSymbol::get_packed](../../debugger/debug-interface-access/idiasymbol-get-packed.md)|`BOOL`|`TRUE` Se la classe di base verrà compressi.|  
|[IDiaSymbol::get_scoped](../../debugger/debug-interface-access/idiasymbol-get-scoped.md)|`BOOL`|`TRUE` Se la classe di base viene visualizzato in un ambito non globali.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID di indice del simbolo.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Restituisce `SymTagBaseClass` (uno dei [enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) valori).|  
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Il simbolo per la classe di base [UDT](../../debugger/debug-interface-access/udt.md).|  
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|ID di simbolo del tipo.|  
|[IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)|`DWORD`|Un valore compreso il [enumerazione UdtKind](../../debugger/debug-interface-access/udtkind.md).|  
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` Se la classe di base non è allineata.|  
|[IDiaSymbol::get_virtualBaseClass](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseclass.md)|`BOOL`|`TRUE` Se la classe di base è virtuale.|  
|[IDiaSymbol::get_virtualBaseDispIndex](../../debugger/debug-interface-access/idiasymbol-get-virtualbasedispindex.md)|`DWORD`|Indice nella tabella di spostamento di base virtuale.|  
|[IDiaSymbol::get_virtualBasePointerOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbasepointeroffset.md)|`LONG`|Offset del puntatore a base virtuale.|  
|[IDiaSymbol::get_virtualBaseTableType](../../debugger/debug-interface-access/idiasymbol-get-virtualbasetabletype.md)|`IDiaSymbol*`|Il tipo dell'indicatore di misura della tabella di base virtuale.|  
|[IDiaSymbol::get_virtualTableShape](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshape.md)|`IDiaSymbol*`|Il simbolo che descrive il tipo della tabella virtuale per questa classe di base.|  
|[IDiaSymbol::get_virtualTableShapeId](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshapeid.md)|`DWORD`|ID del simbolo a forma di tabella virtuale.|  
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` Se la classe di base è contrassegnata come volatile.|  
  
## <a name="see-also"></a>Vedere anche  
 [Gerarchia delle classi dei tipi di simboli](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [UDT](../../debugger/debug-interface-access/udt.md)



