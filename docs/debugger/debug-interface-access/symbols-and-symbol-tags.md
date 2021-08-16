---
description: Le informazioni di debug su un programma compilato vengono archiviate nel file di database di programma (con estensione pdb) come simboli accessibili tramite le API DIA (Debug Interface Access) SDK.
title: Simboli e tag di simboli | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 4cbb8592a9597c81c6ef83c952e4f0572a776339eaa1c039574beb34209e7dc7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121379625"
---
# <a name="symbols-and-symbol-tags"></a>Simboli e relativi tag
Le informazioni di debug su un programma compilato vengono archiviate nel file di database di programma (con estensione pdb) come simboli accessibili tramite le API DIA (Debug Interface Access) SDK. Tutti i simboli hanno [una proprietà IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) [e una proprietà IDiaSymbol::get_symIndexId.](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md) La `symTag` proprietà indica il tipo di simbolo definito dall'enumerazione [SymTagEnum.](../../debugger/debug-interface-access/symtagenum.md) La `symIndexId` proprietà è un valore che contiene `DWORD` l'identificatore univoco per ogni istanza di un simbolo.

 I simboli hanno anche proprietà che possono specificare informazioni aggiuntive sul simbolo, nonché riferimenti ad altri simboli, in genere un [oggetto IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md) o [IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md). Quando si esegue una query su una proprietà che contiene un riferimento, il riferimento viene restituito come [oggetto IDiaSymbol.](../../debugger/debug-interface-access/idiasymbol.md) Tali proprietà vengono sempre associate a un'altra proprietà con lo stesso nome ma con suffisso "Id", ad esempio [IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md) e [IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md). Le tabelle in [Posizioni simboli](../../debugger/debug-interface-access/symbol-locations.md), [Gerarchia lessicale](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)dei tipi di simboli e Gerarchia di classi dei tipi di simboli delineano le proprietà per ognuno dei diversi tipi di simboli. [](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md) Queste proprietà possono contenere informazioni rilevanti su o riferimenti ad altri simboli. Poiché le proprietà sono semplicemente identificatori ordinali numerici delle relative proprietà `*Id` correlate, vengono omesse da altre discussioni. Vengono indicati solo dove necessario per il chiarimento dei parametri.

 Quando si tenta di accedere alla proprietà , se non si verifica alcun errore e alla proprietà del simbolo è stato assegnato un valore, il metodo "get" della proprietà restituisce `S_OK` . Il valore restituito `S_FALSE` indica che la proprietà non è valida per il simbolo corrente.

## <a name="in-this-section"></a>Contenuto della sezione

[Percorsi dei simboli](../../debugger/debug-interface-access/symbol-locations.md)

Descrive i diversi tipi di posizioni che un simbolo può avere.

[Gerarchia lessicale dei tipi di simboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)

Descrive i tipi di simboli che formano gerarchie lessicali, ad esempio file, moduli e funzioni.

[Gerarchia di classi dei tipi di simboli](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)

Descrive i tipi di simboli che corrispondono a diversi elementi del linguaggio, ad esempio classi, matrici e tipi restituiti di funzione.

## <a name="see-also"></a>Vedi anche

- [Debug Interface Access SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)
