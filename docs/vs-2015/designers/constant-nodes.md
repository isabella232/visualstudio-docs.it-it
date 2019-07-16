---
title: Nodi delle costanti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 2c798a50-a2d7-459b-9879-ad4ad8290c9b
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d38a4f8a182562c11dbb742cb26392218edfd981
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68162651"
---
# <a name="constant-nodes"></a>Nodi costanti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nella modalità di progettazione shader, i nodi delle costanti rappresentano valori letterali e attributi vertice interpolati nei calcoli di pixel shader. Poiché gli attributi vertice sono interpolati, e quindi sono diversi per ogni pixel, a ogni istanza di pixel shader viene assegnata una versione della costante diversa. In questo modo ogni pixel ha un aspetto univoco.  
  
## <a name="vertex-attribute-interpolation"></a>Interpolazione degli attributi vertice  
 L'immagine di una scena 3D in un gioco o in un'app viene creata mediante la trasformazione matematica di un numero di oggetti, che sono definiti da vertici, attributi vertice e definizioni di primitive, in pixel sullo schermo. Tutte le informazioni necessarie per dare al pixel un aspetto univoco vengono specificate tramite gli attributi vertice, che vengono combinati insieme in base alla prossimità del pixel ai diversi vertici che costituiscono la *primitiva*. Una primitiva è un elemento di base del rendering, vale a dire una semplice forma, come ad esempio un punto, una linea o un triangolo. Un pixel che è molto vicino a uno solo dei vertici riceve le costanti che sono pressoché identiche a tale vertice, ma un pixel equidistante da tutti i vertici di una primitiva riceve le costanti che sono la media di tali vertici. Nella programmazione grafica, le costanti che i pixel ricevono vengono dette *interpolate*. Specificare dati di costanti ai pixel con questa modalità consente di ottenere una qualità visiva ottimale e allo stesso tempo ridurre il footprint di memoria e i requisiti di larghezza di banda.  
  
 Anche se ogni istanza del pixel shader riceve un solo set di valori costanti che non sono modificabili, istanze del pixel shader diverse ricevano set di dati costanti diversi. Questa progettazione consente a un programma di shader di produrre un output di colore diverso per ogni pixel nella primitiva.  
  
## <a name="constant-node-reference"></a>Riferimento per i nodi delle costanti  
  
|Nodo|Dettagli|Properties|  
|----------|-------------|----------------|  
|**Vettore fotocamera**|Vettore che si estende dal pixel corrente alla fotocamera nello spazio globale.<br /><br /> È possibile usare questo valore per calcolare i riflessi nello spazio globale.<br /><br /> **Output**<br /><br /> `Output`: `float3`<br /> Vettore dal pixel corrente alla fotocamera.|Nessuna|  
|**Costante colore**|Un valore costante di colore.<br /><br /> **Output**<br /><br /> `Output`: `float4`<br /> Valore di colore.|**Output**<br /> Valore di colore.|  
|**Costante**|Un valore scalare costante.<br /><br /> **Output**<br /><br /> `Output`: `float`<br /> Valore scalare.|**Output**<br /> Valore scalare.|  
|**Costante 2D**|Una costante di vettore a due componenti.<br /><br /> **Output**<br /><br /> `Output`: `float2`<br /> Valore di vettore.|**Output**<br /> Valore di vettore.|  
|**Costante 3D**|Una costante di vettore a tre componenti.<br /><br /> **Output**<br /><br /> `Output`: `float3`<br /> Valore di vettore.|**Output**<br /> Valore di vettore.|  
|**Costante 4D**|Una costante di vettore a quattro componenti.<br /><br /> **Output**<br /><br /> `Output`: `float4`<br /> Valore di colore.|**Output**<br /> Valore di vettore.|  
|**Posizione normalizzata**|La posizione del pixel corrente, espressa in coordinate dispositivo normalizzate.<br /><br /> Le coordinate x e y hanno valori compresi nell'intervallo [-1, 1], la coordinata z ha un valore compreso nell'intervallo [0, 1], e il componente w contiene il valore della profondità punti nello spazio di visualizzazione. W non è normalizzato.<br /><br /> **Output**<br /><br /> `Output`: `float4`<br /> La posizione del pixel corrente.|Nessuna|  
|**Colore punto**|Il colore con riflessione diffusa del pixel corrente, ovvero una combinazione del colore del materiale con riflessione diffusa e degli attributi vertice del colore.<br /><br /> **Output**<br /><br /> `Output`: `float4`<br /> Colore con riflessione diffusa del pixel corrente.|Nessuna|  
|**Profondità punto**|La profondità del pixel corrente nello spazio di visualizzazione.<br /><br /> **Output**<br /><br /> `Output`: `float`<br /> La profondità del pixel corrente.|Nessuna|  
|**Profondità punto normalizzato**|La profondità del pixel corrente, espressa in coordinate dispositivo normalizzate.<br /><br /> Il risultato è un valore compreso nell'intervallo [0, 1].<br /><br /> **Output**<br /><br /> `Output`: `float`<br /> La profondità del pixel corrente.|Nessuna|  
|**Posizione schermo**|La posizione del pixel corrente, espressa in coordinate dello schermo.<br /><br /> Le coordinate dello schermo dipendono dal riquadro di visualizzazione corrente. I componenti x e y contengono le coordinate dello schermo, il componente z contiene il valore della profondità normalizzata in un intervallo di [0, 1], e il componente w contiene il valore della profondità nello spazio di visualizzazione.<br /><br /> **Output**<br /><br /> `Output`: `float4`<br /> La posizione del pixel corrente.|Nessuna|  
|**Normale superficie**|La normale alla superficie del pixel corrente nello spazio dell'oggetto.<br /><br /> È possibile usare questo valore per calcolare i contributi dell'illuminazione e i riflessi nello spazio dell'oggetto.<br /><br /> **Output**<br /><br /> `Output`: `float3`<br /> La normale alla superficie del pixel corrente.|Nessuna|  
|**Vettore fotocamera spazio tangente**|Vettore che si estende dal pixel corrente alla fotocamera nello spazio tangente.<br /><br /> È possibile usare questo valore per calcolare i riflessi nello spazio tangente.<br /><br /> **Output**<br /><br /> `Output`: `float3`<br /> Vettore dal pixel corrente alla fotocamera.|Nessuna|  
|**Direzione luce spazio tangente**|Vettore che definisce la direzione in cui la luce è diffusa da una sorgente di luce nello spazio tangente del pixel corrente.<br /><br /> È possibile usare questo valore per calcolare l'illuminazione e i contributi speculari nello spazio tangente.<br /><br /> **Output:**<br /><br /> `Output`: `float3`<br /> Il vettore dal pixel corrente a una sorgente di luce.|Nessuna|  
|**Normale globale**|La normale alla superficie del pixel corrente nello spazio globale.<br /><br /> È possibile usare questo valore per calcolare i contributi dell'illuminazione e i riflessi nello spazio globale.<br /><br /> **Output**<br /><br /> `Output`: `float3`<br /> La normale alla superficie del pixel corrente.|Nessuna|  
|**Posizione globale**|Posizione del pixel corrente nello spazio globale.<br /><br /> **Output**<br /><br /> `Output`: `float4`<br /> La posizione del pixel corrente.|Nessuna|
