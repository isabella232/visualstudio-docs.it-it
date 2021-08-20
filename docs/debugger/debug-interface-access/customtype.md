---
title: CustomType | Microsoft Docs
description: Trovare informazioni di riferimento sul tipo di simbolo CustomType (SymTagCustomType) nell'SDK Visual Studio di accesso all'interfaccia di debug.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CustomType symbol
ms.assetid: 1b66bc0a-7979-416f-bf7f-e5df91584c91
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 4caaa6094c15cc3f51cb3a0c6f3341781d4036f5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122058995"
---
# <a name="customtype"></a>CustomType
I tipi definiti dal fornitore (tipi specifici del compilatore) sono identificati da un `SymTagCustomType` simbolo.

## <a name="properties"></a>Proprietà
 La tabella seguente illustra proprietà valide aggiuntive per questo tipo di simbolo.

|Proprietà|Tipo di dati|Descrizione|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_oemId](../../debugger/debug-interface-access/idiasymbol-get-oemid.md)|`DWORD`|Identificatore dell'OEM.|
|[IDiaSymbol::get_oemSymbolId](../../debugger/debug-interface-access/idiasymbol-get-oemsymbolid.md)|`DWORD`|ID interno dell'OEM.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID indice del simbolo.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Restituisce `SymTagCustomType` (uno dei [valori dell'enumerazione SymTagEnum).](../../debugger/debug-interface-access/symtagenum.md)|
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Primo tipo a cui fa riferimento il simbolo del tipo personalizzato.|
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|ID del simbolo del tipo.|
|[IDiaSymbol::get_types](../../debugger/debug-interface-access/idiasymbol-get-types.md)|`IDiaSymbol**`|Matrice di tutti i tipi a cui fa riferimento il simbolo di tipo personalizzato.|

## <a name="see-also"></a>Vedi anche
- [Gerarchia di classi dei tipi di simboli](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)