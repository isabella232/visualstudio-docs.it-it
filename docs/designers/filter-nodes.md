---
title: Nodi del filtro
description: Informazioni sui nodi filtro, che trasformano un input come un campione di colore o trama in un valore di colore figurativo, nella finestra di progettazione shader.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: f7cae2dc-e9a7-49d4-8be5-58b79868624e
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-designers
ms.workload:
- multiple
ms.openlocfilehash: 8af162b4e2ff81cab74bc364e85c965d6f5c0004c5b1e7959b5afc9f9faf5e5c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121390823"
---
# <a name="filter-nodes"></a>Nodi del filtro

In Progettazione shader, i nodi filtro trasformano un input, ad esempio, un campione di colore o trama, in un valore di colore figurativo. Questi valori di colori figurativi vengono comunemente usati durante il rendering non fotorealistico o come componenti di altri effetti visivi.

## <a name="filter-node-reference"></a>Riferimento per i nodi filtri

|Nodo|Dettagli|Proprietà|
|----------|-------------|----------------|
|**Sfocatura**|Sfoca i pixel in una trama usando una funzione gaussiana.<br /><br /> Ciò consente di ridurre il dettaglio o il rumore di colore in una trama.<br /><br /> **Input:**<br /><br /> `UV`: `float2`<br /> Le coordinate del texel da testare.<br /><br /> **Output:**<br /><br /> `Output`: `float4`<br /> Valore del colore sfocato.|**Trama**<br /> Registro di trama associato al campionatore usato durante la sfocatura.|
|**Desatura**|Riduce la quantità di colore nel colore specificato.<br /><br /> Quando un colore viene rimosso, il valore del colore si avvicina all'equivalente scala di grigio.<br /><br /> **Input:**<br /><br /> `RGB`: `float3`<br /> Colore da desaturare.<br /><br /> `Percent`: `float`<br /> Percentuale di colore da rimuovere, espresso come valore normalizzato compreso nell'intervallo [0, 1].<br /><br /> **Output:**<br /><br /> `Output`: `float3`<br /> Colore desaturato.|**Luminanza**<br /> Valori assegnati ai componenti del colore rosso, verde e blu.|
|**Rilevamento bordi**|Rileva i contorni di una trama usando un rilevatore di bordi Canny. I pixel dei bordi vengono restituiti come colore bianco. I pixel che non appartengono ai bordi vengono restituiti come colore nero.<br /><br /> Ciò consente di identificare i bordi di una trama in modo da aggiungere effetti per trattare i pixel dei bordi.<br /><br /> **Input:**<br /><br /> `UV`: `float2`<br /> Le coordinate del texel da testare.<br /><br /> **Output:**<br /><br /> `Output`: `float4`<br /> Bianco se il texel si trova su un bordo. In caso contrario, nero.|**Trama**<br /> Registro di trama associato al campionatore usato durante il rilevamento dei bordi.|
|**Nitidezza**|Aumenta la nitidezza di una trama.<br /><br /> Ciò consente di evidenziare i particolari in una trama.<br /><br /> **Input:**<br /><br /> `UV`: `float2`<br /> Le coordinate del texel da testare.<br /><br /> **Output:**<br /><br /> `Output`: `float4`<br /> Valore del colore sfocato.|**Trama**<br /> Registro di trama associato al campionatore usato durante la nitidezza.|