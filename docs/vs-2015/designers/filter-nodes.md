---
title: Nodi filtro | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7cae2dc-e9a7-49d4-8be5-58b79868624e
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2789676505588c2041abfd876a228fc456ee3607
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47520144"
---
# <a name="filter-nodes"></a>Nodi del filtro
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [i nodi filtro](https://docs.microsoft.com/visualstudio/designers/filter-nodes).  
  
In Progettazione shader, i nodi filtro trasformano un input, ad esempio, un campione di colore o trama, in un valore di colore figurativo. Questi valori di colori figurativi vengono comunemente usati durante il rendering non fotorealistico o come componenti di altri effetti visivi.  
  
## <a name="filter-node-reference"></a>Riferimento per i nodi filtri  
  
|Nodo|Dettagli|Proprietà|  
|----------|-------------|----------------|  
|**Sfocatura**|Sfoca i pixel in una trama usando una funzione gaussiana.<br /><br /> Ciò consente di ridurre il dettaglio o il rumore di colore in una trama.<br /><br /> **Input:**<br /><br /> `UV`: `float2`<br /> Le coordinate del texel da testare.<br /><br /> **Output:**<br /><br /> `Output`: `float4`<br /> Valore del colore sfocato.|**Trama**<br /> Registro di trama associato al campionatore usato durante la sfocatura.|  
|**Desatura**|Riduce la quantità di colore nel colore specificato.<br /><br /> Quando un colore viene rimosso, il valore del colore si avvicina all'equivalente scala di grigio.<br /><br /> **Input:**<br /><br /> `RGB`: `float3`<br /> Colore da desaturare.<br /><br /> `Percent`: `float`<br /> Percentuale di colore da rimuovere, espresso come valore normalizzato compreso nell'intervallo [0, 1].<br /><br /> **Output:**<br /><br /> `Output`: `float3`<br /> Colore desaturato.|**Luminanza**<br /> Valori assegnati ai componenti del colore rosso, verde e blu.|  
|**Rilevamento bordi**|Rileva i contorni di una trama usando un rilevatore di bordi Canny. I pixel dei bordi vengono restituiti come colore bianco. I pixel che non appartengono ai bordi vengono restituiti come colore nero.<br /><br /> Ciò consente di identificare i bordi di una trama in modo da aggiungere effetti per trattare i pixel dei bordi.<br /><br /> **Input:**<br /><br /> `UV`: `float2`<br /> Le coordinate del texel da testare.<br /><br /> **Output:**<br /><br /> `Output`: `float4`<br /> Bianco se il texel si trova su un bordo. In caso contrario, nero.|**Trama**<br /> Registro di trama associato al campionatore usato durante il rilevamento dei bordi.|  
|**Nitidezza**|Aumenta la nitidezza di una trama.<br /><br /> Ciò consente di evidenziare i particolari in una trama.<br /><br /> **Input:**<br /><br /> `UV`: `float2`<br /> Le coordinate del texel da testare.<br /><br /> **Output:**<br /><br /> `Output`: `float4`<br /> Valore del colore sfocato.|**Trama**<br /> Registro di trama associato al campionatore usato durante la nitidezza.|



