---
title: Simboli e relativi tag | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK]
ms.assetid: 2ee3a262-cda6-48bf-b799-a37edde6c8b8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 69d2f5c2182f32a95ca95d24c5319b164f27f1ae
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="symbols-and-symbol-tags"></a>Simboli e relativi tag
Informazioni di debug di un programma compilato viene archiviate nel file di database (con estensione pdb) programma come simboli che sono accessibili utilizzando le API di SDK eseguire il Debug Interface Access (DIA). Tutti i simboli sono un [idiasymbol:: Get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) e [idiasymbol:: Get_symindexid](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md) proprietà. Il `symTag` proprietà indica il tipo di simbolo definito per il [SymTagEnum (enumerazione)](../../debugger/debug-interface-access/symtagenum.md) enumerazione. Il `symIndexId` proprietà è un `DWORD` valore che contiene l'identificatore univoco per ogni istanza di un simbolo.  
  
 Anche i simboli hanno proprietà che è possibile specificare ulteriori informazioni sui simboli, nonché i riferimenti ad altri simboli, spesso un [idiasymbol:: Get_lexicalparent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md) o [idiasymbol:: Get_classparent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md). Quando si esegue la query di una proprietà che contiene un riferimento, il riferimento viene restituito come un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) oggetto. Tali proprietà sono sempre associato a un'altra proprietà con lo stesso nome ma suffisso con "Id", ad esempio, [idiasymbol:: Get_lexicalparentid](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md) e [idiasymbol:: Get_classparentid](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md). Le tabelle in [percorsi dei simboli](../../debugger/debug-interface-access/symbol-locations.md), [gerarchia lessicale dei tipi di simboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md), e [classe gerarchia dei tipi di simboli](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md) descrive le proprietà per tutti i tipi diversi di simboli. Queste proprietà possono avere le informazioni o riferimenti ad altri simboli. Poiché il `*Id` le proprietà sono identificatori ordinale semplicemente numerici delle relative proprietà correlate, vengono omessi da ulteriori discussioni. Vengono definite solo quando necessario per i dettagli di parametro.  
  
 Quando si tenta di accedere alla proprietà, se si verifica alcun errore e la proprietà simbolo è stata assegnata un valore, la proprietà "get" restituisce `S_OK`. Valore restituito di `S_FALSE` indica che la proprietà non è valida per il simbolo corrente.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Percorsi dei simboli](../../debugger/debug-interface-access/symbol-locations.md)  
 Descrive i diversi tipi di percorsi che può avere un simbolo.  
  
 [Gerarchia lessicale dei tipi di simboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)  
 Descrive i tipi di simboli che formano lessicale gerarchie, ad esempio file, i moduli e funzioni.  
  
 [Gerarchia di classi dei tipi di simboli](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)  
 Descrive i tipi di simboli che corrispondono agli elementi del linguaggio diversi come tipi restituiti di funzione, matrici e le classi.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug Interface Access SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)