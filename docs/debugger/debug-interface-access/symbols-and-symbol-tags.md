---
title: Simboli e tag dei simboli | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK]
ms.assetid: 2ee3a262-cda6-48bf-b799-a37edde6c8b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5d2281a82926dabfde88b8d4bb9096f0e9624211
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738523"
---
# <a name="symbols-and-symbol-tags"></a>Simboli e relativi tag
Le informazioni di debug relative a un programma compilato vengono archiviate nel file di database di programma (con estensione pdb) come simboli accessibili tramite le API SDK di debug Interface Access (DIA). Tutti i simboli hanno una proprietà [IDiaSymbol:: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) e [IDiaSymbol:: get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md) . La proprietà `symTag` indica il tipo di simbolo definito dall'enumerazione [SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) . La proprietà `symIndexId` è un valore `DWORD` che contiene l'identificatore univoco per ogni istanza di un simbolo.

 I simboli hanno anche proprietà che possono specificare informazioni aggiuntive sul simbolo, oltre a riferimenti ad altri simboli, in genere [IDiaSymbol:: get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md) o [IDiaSymbol:: get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md). Quando si esegue una query su una proprietà che contiene un riferimento, il riferimento viene restituito come oggetto [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) . Tali proprietà sono sempre abbinate a un'altra proprietà con lo stesso nome ma con suffisso "ID", ad esempio [IDiaSymbol:: get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md) e [IDiaSymbol:: get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md). Le tabelle nelle [posizioni dei simboli](../../debugger/debug-interface-access/symbol-locations.md), nella [Gerarchia lessicale dei tipi di simboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)e nella [gerarchia di classi dei tipi di](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md) simboli delineano le proprietà di ognuno dei diversi tipi di simboli. Queste proprietà possono contenere informazioni rilevanti su o riferimenti ad altri simboli. Poiché le proprietà `*Id` sono semplicemente identificatori ordinali numerici delle proprietà correlate, vengono omesse da ulteriori discussioni. Viene fatto riferimento solo quando necessario per la chiarificazione dei parametri.

 Quando si tenta di accedere alla proprietà, se non si verifica alcun errore e alla proprietà Symbol è stato assegnato un valore, il metodo "Get" della proprietà restituisce `S_OK`. Un valore restituito di `S_FALSE` indica che la proprietà non è valida per il simbolo corrente.

## <a name="in-this-section"></a>Contenuto della sezione

[Percorsi dei simboli](../../debugger/debug-interface-access/symbol-locations.md)

Vengono descritti i diversi tipi di località che possono essere presenti in un simbolo.

[Gerarchia lessicale dei tipi di simboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)

Vengono descritti i tipi di simboli che formano gerarchie lessicali, ad esempio file, moduli e funzioni.

[Gerarchia di classi dei tipi di simboli](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)

Descrive i tipi di simboli che corrispondono a elementi di linguaggio diversi, ad esempio classi, matrici e tipi restituiti della funzione.

## <a name="see-also"></a>Vedere anche

- [Debug Interface Access SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)