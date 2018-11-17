---
title: Specificare quando e dove applicare un'annotazione | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- _Group_
- _At_
- _When_
- _At_buffer_
ms.assetid: 8e4f4f9c-5dfa-4835-87df-ecd1698fc650
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f149f483f29f4dafb29d0f7fed16a9bf93a59b78
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51754287"
---
# <a name="specifying-when-and-where-an-annotation-applies"></a>Specificare dove e quando applicare un'annotazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando un'annotazione condizionale, potrebbe essere necessario altre annotazioni per specificare che per l'analizzatore.  Ad esempio, se una funzione dispone di una variabile che può essere sincrone o asincrone, il comportamento della funzione come indicato di seguito: nel caso sincrono sempre alla fine ha esito positivo, ma nel caso asincrono segnala un errore se potrebbe non riuscire immediatamente. Quando la funzione viene chiamata in modo sincrono, controllando il valore di risultato non fornisce alcun valore per l'analizzatore di codice perché potrebbe non avere restituita.  Tuttavia, quando la funzione viene chiamata in modo asincrono e il risultato della funzione non è selezionato, può verificarsi un errore grave. In questo esempio illustra una situazione in cui è possibile usare il `_When_` annotazione, descritto più avanti in questo articolo, abilitare il controllo.  
  
## <a name="structural-annotations"></a>Annotazioni strutturali  
 Per controllare quando e dove applicano le annotazioni, utilizzare le seguenti annotazioni strutturale.  
  
|Annotazione|Descrizione|  
|----------------|-----------------|  
|`_At_(expr, anno-list)`|`expr` è un'espressione che produce un lvalue. Le annotazioni in `anno-list` vengono applicati all'oggetto denominato da `expr`. Per ciascuna annotazione in `anno-list`, `expr` viene interpretato nelle precondizioni se l'annotazione viene interpretata nella condizione preliminare, e nella postcondizione se l'annotazione nella post condizione.|  
|`_At_buffer_(expr, iter, elem-count, anno-list)`|`expr` è un'espressione che produce un lvalue. Le annotazioni in `anno-list` vengono applicati all'oggetto denominato da `expr`. Per ciascuna annotazione in `anno-list`, `expr` viene interpretato nelle precondizioni se l'annotazione viene interpretata nella precondizione, e nella postcondizione se l'annotazione nella post condizione.<br /><br /> `iter` è il nome di una variabile con ambito di annotazione (comprende `anno-list`). `iter` tipo implicito è `long`. Le variabili denominate in modo identico in qualsiasi ambito di inclusione sono nascosti dalla versione di valutazione.<br /><br /> `elem-count` è un'espressione che restituisce un numero intero.|  
|`_Group_(anno-list)`|Le annotazioni in `anno-list` sono tutti considerati per avere qualsiasi qualificatore di cui si applica l'annotazione di gruppo che viene applicata a ciascuna annotazione.|  
|`_When_(expr, anno-list)`|`expr` è un'espressione che può essere convertita in `bool`. Quando è diverso da zero (`true`), le annotazioni vengono specificate in `anno-list` sono considerati applicabile.<br /><br /> Per impostazione predefinita, per ciascuna annotazione in `anno-list`, `expr` viene interpretato come utilizza i valori di input se l'annotazione è una precondizione, usando i valori di output se l'annotazione è una post-condizione. Per ignorare l'impostazione predefinita, è possibile usare il `_Old_` intrinseco quando si valuta una post-condizione di per indicare che i valori di input devono essere utilizzati. **Nota:** annotazioni diverse potrebbero essere abilitate come conseguenza usando `_When_` se si specifica un valore modificabile, ovvero, ad esempio, `*pLength`, ovvero è complessa, poiché il risultato valutato del `expr` in precondizione può differire dal relativo valutato comportare postcondizione.|  
  
## <a name="see-also"></a>Vedere anche  
 [Uso delle annotazioni SAL per ridurre i difetti del codice C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Informazioni su SAL](../code-quality/understanding-sal.md)   
 [Annotazione di parametri di funzione e valori restituiti](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Annotazione del comportamento (funzione)](../code-quality/annotating-function-behavior.md)   
 [Annotazioni di struct e classi](../code-quality/annotating-structs-and-classes.md)   
 [Annotazione del comportamento di blocco](../code-quality/annotating-locking-behavior.md)   
 [Funzioni intrinseche](../code-quality/intrinsic-functions.md)   
 [Suggerimenti ed esempi](../code-quality/best-practices-and-examples-sal.md)



