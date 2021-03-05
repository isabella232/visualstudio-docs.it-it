---
description: Quando viene creato il file con estensione exe, a ogni simbolo pubblico (come minimo, ogni funzione globale e simbolo di dati) viene assegnato un tag SymTagPublicSymbol.
title: PublicSymbol | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- data symbols [C++]
- PublicSymbol symbol
- global functions [C++], as public symbols
ms.assetid: f8d33007-302d-4549-9dad-47fb33ea60b7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 02a706a1dc20dd61c43fce62905b2d3ac48f87fd
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161648"
---
# <a name="publicsymbol"></a>PublicSymbol
Quando viene creato il file con estensione exe, a ogni simbolo pubblico (come minimo, ogni funzione globale e simbolo di dati) viene assegnato un `SymTagPublicSymbol` tag.

## <a name="properties"></a>Proprietà
 Nella tabella seguente vengono illustrate le proprietà valide per questo tipo di simbolo.

|Proprietà|Tipo di dati|Descrizione|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Offset parte della posizione; per informazioni dettagliate, vedere l' [enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Parte della sezione della posizione; per informazioni dettagliate, vedere l' [enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_code](../../debugger/debug-interface-access/idiasymbol-get-code.md)|`BOOL`|`TRUE` Se il percorso del simbolo è nel codice.|
|[IDiaSymbol::get_function](../../debugger/debug-interface-access/idiasymbol-get-function.md)|`BOOL`|`TRUE` Se il simbolo è una funzione.|
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|Lunghezza in byte del simbolo.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Simbolo dell'ambito globale.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID del simbolo padre lessicale.|
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|I simboli pubblici hanno posizioni statiche; per informazioni dettagliate, vedere [posizioni dei simboli](../../debugger/debug-interface-access/symbol-locations.md).|
|[IDiaSymbol::get_managed](../../debugger/debug-interface-access/idiasymbol-get-managed.md)|`BOOL`|`TRUE` Se la posizione del simbolo è nel codice gestito.|
|[IDiaSymbol::get_msil](../../debugger/debug-interface-access/idiasymbol-get-msil.md)|`BOOL`|`TRUE` Se il percorso del simbolo è nel codice MSIL (Microsoft Intermediate Language).|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Nome completamente decorato del simbolo.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID di indice del simbolo.|
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Posizione relativa del simbolo all'interno del relativo blocco.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Restituisce `SymTagPublicSymbol` uno dei valori di [enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) .|
|[IDiaSymbol::get_undecoratedName](../../debugger/debug-interface-access/idiasymbol-get-undecoratedname.md)|`BSTR`|Nome del simbolo non decorato.|
|[IDiaSymbol::get_undecoratedNameEx](../../debugger/debug-interface-access/idiasymbol-get-undecoratednameex.md)|`BSTR`|Parte o tutto il nome del simbolo non decorato.|

## <a name="see-also"></a>Vedi anche
- [Gerarchia lessicale dei tipi di simboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [Enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md)
- [Percorsi dei simboli](../../debugger/debug-interface-access/symbol-locations.md)
