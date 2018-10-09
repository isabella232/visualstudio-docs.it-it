---
title: I simboli e relativi tag | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
- symbols [DIA SDK]
ms.assetid: 2ee3a262-cda6-48bf-b799-a37edde6c8b8
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 04dfbe961b122ded6ddb5ff19d70091ba6c408c0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47527411"
---
# <a name="symbols-and-symbol-tags"></a>Simboli e relativi tag
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [simboli e relativi tag](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/symbols-and-symbol-tags).  
  
Informazioni di debug su un programma compilato viene archiviate nel file di database (con estensione pdb) di programma come simboli che sono accessibili tramite le API di SDK eseguire il Debug Interface Access (DIA). Tutti i simboli sono una [Get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) e una [Get_symindexid](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md) proprietà. Il `symTag` proprietà indica il tipo di simbolo in base il [enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) enumerazione. Il `symIndexId` proprietà è un `DWORD` valore che contiene l'identificatore univoco per ogni istanza di un simbolo.  
  
 I simboli hanno anche proprietà che è possibile specificare altre informazioni sui simboli, nonché i riferimenti agli altri simboli, in genere un [Get_lexicalparent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md) o [Get_classparent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md). Quando si esegue la query di una proprietà che contiene un riferimento, il riferimento viene restituito come un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) oggetto. Tali proprietà sono sempre associate a un'altra proprietà con lo stesso nome ma con suffisso con "Id", ad esempio, [Get_lexicalparentid](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md) e [Get_classparentid](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md). Le tabelle nel [percorsi di simboli](../../debugger/debug-interface-access/symbol-locations.md), [gerarchia lessicale dei tipi di simboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md), e [classe gerarchia dei tipi di simboli](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md) descrive le proprietà per ognuno dei diversi tipi di simboli. Queste proprietà possono essere presenti le informazioni o riferimenti agli altri simboli. Poiché il `*Id` proprietà sono identificatori ordinale semplicemente numerici delle relative proprietà correlate, vengono omessi da altre discussioni. Vengono definiti solo se necessario per i dettagli di parametro.  
  
 Quando si tenta di accedere alla proprietà, se si verifica alcun errore e la proprietà simbolo è stata assegnata un valore, la proprietà "get" restituzione del metodo `S_OK`. Valore restituito di `S_FALSE` indica che la proprietà non è valida per il simbolo corrente.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Percorsi dei simboli](../../debugger/debug-interface-access/symbol-locations.md)  
 Descrive i diversi tipi di percorsi che può avere un simbolo.  
  
 [Gerarchia lessicale dei tipi di simboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)  
 Descrive i tipi di simboli che formano le gerarchie lessicali, ad esempio file, moduli e funzioni.  
  
 [Gerarchia di classi dei tipi di simboli](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)  
 Descrive i tipi di simboli che corrispondono agli elementi del linguaggio diverse, ad esempio classi, matrici e funzioni restituiscono tipi.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug Interface Access SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)


