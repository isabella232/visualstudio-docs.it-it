---
title: Simboli e tag dei simboli | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK]
ms.assetid: 2ee3a262-cda6-48bf-b799-a37edde6c8b8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 12f1927e4290ff9d008eff9f497c9d570d9d44f8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99862283"
---
# <a name="symbols-and-symbol-tags"></a>Simboli e relativi tag
Le informazioni di debug relative a un programma compilato vengono archiviate nel file di database di programma (con estensione pdb) come simboli accessibili tramite le API SDK di debug Interface Access (DIA). Tutti i simboli hanno un valore [IDiaSymbol:: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) e una proprietà [IDiaSymbol:: get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md) . La `symTag` proprietà indica il tipo di simbolo definito dall'enumerazione [SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) . La `symIndexId` proprietà è un `DWORD` valore che contiene l'identificatore univoco per ogni istanza di un simbolo.

 I simboli hanno anche proprietà che possono specificare informazioni aggiuntive sul simbolo, oltre a riferimenti ad altri simboli, in genere [IDiaSymbol:: get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md) o [IDiaSymbol:: get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md). Quando si esegue una query su una proprietà che contiene un riferimento, il riferimento viene restituito come oggetto [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) . Tali proprietà sono sempre abbinate a un'altra proprietà con lo stesso nome ma con suffisso "ID", ad esempio [IDiaSymbol:: get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md) e [IDiaSymbol:: get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md). Le tabelle nelle [posizioni dei simboli](../../debugger/debug-interface-access/symbol-locations.md), nella [Gerarchia lessicale dei tipi di simboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)e nella [gerarchia di classi dei tipi di](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md) simboli delineano le proprietà di ognuno dei diversi tipi di simboli. Queste proprietà possono contenere informazioni rilevanti su o riferimenti ad altri simboli. Poiché le `*Id` proprietà sono semplicemente identificatori ordinali numerici delle proprietà correlate, vengono omesse da ulteriori discussioni. Viene fatto riferimento solo quando necessario per la chiarificazione dei parametri.

 Quando si tenta di accedere alla proprietà, se non si verifica alcun errore e alla proprietà Symbol è stato assegnato un valore, il metodo "Get" della proprietà restituisce `S_OK` . Un valore restituito di `S_FALSE` indica che la proprietà non è valida per il simbolo corrente.

## <a name="in-this-section"></a>Contenuto della sezione

[Percorsi dei simboli](../../debugger/debug-interface-access/symbol-locations.md)

Vengono descritti i diversi tipi di località che possono essere presenti in un simbolo.

[Gerarchia lessicale dei tipi di simboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)

Vengono descritti i tipi di simboli che formano gerarchie lessicali, ad esempio file, moduli e funzioni.

[Gerarchia di classi dei tipi di simboli](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)

Descrive i tipi di simboli che corrispondono a elementi di linguaggio diversi, ad esempio classi, matrici e tipi restituiti della funzione.

## <a name="see-also"></a>Vedi anche

- [Debug Interface Access SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)