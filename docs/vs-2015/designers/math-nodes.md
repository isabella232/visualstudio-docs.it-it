---
title: Nodi delle operazioni matematiche | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: adc225cc-1cf5-4f7c-9b00-e7ac8450b6b9
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 154f79ab5a90821ee08b7a9e802f1481baae55dc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540925"
---
# <a name="math-nodes"></a>Nodi di matematica
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [nodi di matematica](https://docs.microsoft.com/visualstudio/designers/math-nodes).  
  
Nella finestra di progettazione shader i nodi matematici eseguono operazioni algebriche, logiche, trigonometriche e altre operazioni matematiche.  
  
> [!NOTE]
>  Quando si usano nodi matematici nella finestra di progettazione shader, la promozione del tipo è particolarmente evidente. Per informazioni su come la promozione del tipo influisce sui parametri di input, vedere la sezione "Promozione di input" in [Nodi della finestra di progettazione shader](../designers/shader-designer-nodes.md).  
  
## <a name="math-node-reference"></a>Riferimento per il nodo matematica  
  
|Nodo|Dettagli|Proprietà|  
|----------|-------------|----------------|  
|**Abs**|Calcola il valore assoluto dell'input specificato per ogni componente.<br /><br /> Per ogni componente del valore `X` di input, i valori negativi sono resi positivi in modo che ogni componente del risultato abbia un valore positivo.<br /><br /> **Input:**<br /><br /> `X`: `float`, `float2`, `float3` o `float4`<br /> Valori per i quali determinare il valore assoluto.<br /><br /> `Output:`<br /><br /> `Output`: uguale a `X` di input<br /> Valore assoluto, per componente.|nessuno|  
|**Aggiungi**|Calcola la somma a livello di componente degli input specificati per ogni componente.<br /><br /> Per ogni componente del risultato, i componenti corrispondenti del valore `X` di input e del valore `Y` di input vengono aggiunti insieme.<br /><br /> **Input:**<br /><br /> `X`: `float`, `float2`, `float3` o `float4`<br /> Uno dei valori da sommare.<br /><br /> `Y`: uguale a `X` di input<br /> Uno dei valori da sommare.<br /><br /> **Output:**<br /><br /> `Output`: uguale a `X` di input<br /> La somma, per componente.|nessuno|  
|**Tetto massimo**|Calcola il tetto massimo dell'input specificato per ogni componente.<br /><br /> Il tetto massimo di un valore è l'Integer più piccolo che sia maggiore o uguale al valore.<br /><br /> **Input:**<br /><br /> `X`: `float`, `float2`, `float3` o `float4`<br /> Valori per i quali calcolare il tetto massimo.<br /><br /> **Output:**<br /><br /> `Output`: uguale a `X` di input<br /> Il tetto massimo, per componente.|nessuno|  
|**Morsa**|Fissa ogni componente dell'input specificato a un intervallo predefinito.<br /><br /> Per ogni componente del risultato, i valori al di sotto dell'intervallo definito sono resi uguali al valore minimo dell'intervallo, i valori al di sopra dell'intervallo definito sono resi uguali al valore massimo dell'intervallo e i valori compresi nell'intervallo non vengono modificati.<br /><br /> **Input:**<br /><br /> `X`: `float`, `float2`, `float3` o `float4`<br /> Valori da fissare.<br /><br /> **Output:**<br /><br /> `Output`: uguale a `X` di input<br /> Valore fissato, per ogni componente.|**Max**<br /> Valore massimo dell'intervallo.<br /><br /> **Min**<br /> Valore minimo dell'intervallo.|  
|**Cos**|Calcola il coseno dell'input specificato, espresso in radianti, per ogni componente.<br /><br /> Per ciascun componente del risultato, viene calcolato il coseno del componente corrispondente, fornito in radianti. Il risultato ha componenti con valori compresi nell'intervallo [-1, 1].<br /><br /> **Input:**<br /><br /> `X`: `float`, `float2`, `float3` o `float4`<br /> Valori di cui calcolare il coseno, in radianti.<br /><br /> **Output:**<br /><br /> `Output`: uguale a `X` di input<br /> Il coseno, per componente.|nessuno|  
|**Trasversale**|Calcola il prodotto incrociato dei vettori a tre componenti specificati.<br /><br /> È possibile usare il prodotto incrociato per calcolare la normale di una superficie definita da due vettori.<br /><br /> **Input:**<br /><br /> `X`: `float3`<br /> Vettore di sinistra del prodotto incrociato.<br /><br /> `Y`: `float3`<br /> Vettore di destra del prodotto incrociato.<br /><br /> **Output:**<br /><br /> `Output`: `float3`<br /> Prodotto incrociato.|nessuno|  
|**Distanza**|Calcola la distanza tra i punti specificati.<br /><br /> Il risultato è un valore scalare positivo.<br /><br /> **Input:**<br /><br /> `X`: `float`, `float2`, `float3` o `float4`<br /> Uno dei punti tra cui determinare la distanza.<br /><br /> `Y`: uguale a `X` di input<br /> Uno dei punti tra cui determinare la distanza.<br /><br /> **Output:**<br /><br /> `Output`: uguale a `X` di input<br /> Distanza.|nessuno|  
|**Dividi**|Calcola il quoziente degli input specificati a livello di componente.<br /><br /> Per ciascun componente del risultato, il componente corrispondente del valore `X` di input viene diviso per il componente corrispondente del valore `Y` di input.<br /><br /> **Input:**<br /><br /> `X`: `float`, `float2`, `float3` o `float4`<br /> Valori dividendo.<br /><br /> `Y`: uguale a `X` di input<br /> Valori divisore.<br /><br /> **Output:**<br /><br /> `Output`: uguale a `X` di input<br /> Il quoziente, per componente.|nessuno|  
|**Punto**|Calcola il prodotto scalare dei vettori specificati.<br /><br /> Il risultato è un valore scalare. È possibile usare il prodotto scalare per determinare l'angolo tra due vettori.<br /><br /> **Input:**<br /><br /> `X`: `float`, `float2`, `float3` o `float4`<br /> Uno dei termini.<br /><br /> `Y`: uguale a `X` di input<br /> Uno dei termini.<br /><br /> **Output:**<br /><br /> `Output`: `float`<br /> Prodotto scalare.|nessuno|  
|**Tetto minimo**|Calcola il tetto minimo dell'input specificato per ogni componente.<br /><br /> Per ogni componente del risultato, il valore è l'Integer intero più grande che sia minore o uguale al componente corrispondente dell'input. Ogni componente del risultato è un Integer intero.<br /><br /> **Input:**<br /><br /> `X`: `float`, `float2`, `float3` o `float4`<br /> Valori per i quali calcolare il tetto minimo.<br /><br /> **Output:**<br /><br /> `Output`: uguale a `X` di input<br /> Il tetto minimo, per componente.|nessuno|  
|**Fmod**|Calcola il modulo (resto) degli input specificati a livello di componente.<br /><br /> Per ciascun componente del risultato, un multiplo integrale (numero intero), m, del componente corrispondente del valore `Y` di input viene sottratto dal componente corrispondente del valore `X` di input, lasciando un resto. Il multiplo, m, viene scelto in modo che il resto sia minore del componente corrispondente del valore `Y` di input e abbia lo stesso segno del componente corrispondente del valore `X` di input. Ad esempio, fmod (-3.14, 1,5), è -0.14.<br /><br /> **Input:**<br /><br /> `X`: `float`, `float2`, `float3` o `float4`<br /> Valori dividendo.<br /><br /> `Y`: uguale a `X` di input<br /> Valori divisore.<br /><br /> **Output:**<br /><br /> `Output`: uguale a `X` di input<br /> Il modulo, per componente.|nessuno|  
|**Frac**|Rimuove la parte integrale (numero intero) dell'input specificato per ogni componente.<br /><br /> Per ciascun componente del risultato, la parte integrale del componente corrispondente dell'input viene rimossa, ma la parte frazionaria e il segno vengono mantenuti. Questo valore frazionario rientra nell'intervallo [0, 1). Ad esempio, il valore -3,14 diventa il valore -0,14.<br /><br /> **Input:**<br /><br /> `X`: `float`, `float2`, `float3` o `float4`<br /> Valori per i quali calcolare la parte frazionaria.<br /><br /> **Output:**<br /><br /> `Output`: uguale a `X` di input<br /> La parte frazionaria, per componente.|nessuno|  
|**Lerp**|Interpolazione lineare. Calcola la media ponderata degli input specificati a livello di componente.<br /><br /> Per ciascun componente del risultato, viene calcolata la media ponderata dei componenti corrispondenti dei valori `X` e `Y` di input. Il peso viene fornito da `Percent`, scalare, e viene applicato in modo uniforme a tutti i componenti. È possibile usare questo valore per interpolare tra punti, colori, attributi e altri valori.<br /><br /> **Input:**<br /><br /> `X`: `float`, `float2`, `float3` o `float4`<br /> Valore originario. Se `Percent` è pari a zero, il risultato è uguale all'input.<br /><br /> `Y`: uguale a `X` di input<br /> Valore terminale. Se `Percent` è pari a uno, il risultato è uguale all'input.<br /><br /> `Percent`: `float`<br /> Peso scalare espresso come percentuale della distanza dal valore `X` di input al valore `Y` di input.<br /><br /> **Output:**<br /><br /> `Output`: uguale a `X` di input<br /> Valore collineare con gli input specificati.|nessuno|  
|**Aggiunta multipla**|Calcola il risultato di un'operazione di moltiplicazione e addizione degli input specificati a livello di componente.<br /><br /> Per ciascun componente del risultato, il prodotto dei componenti corrispondenti dei valori `M` e `A` di input viene aggiunto al componente corrispondente del valore `B` di input. Questa sequenza di operazioni è presente in formule comuni, ad esempio nella formula punto-inclinazione di una linea e nella formula per scalare e quindi compensare un input.<br /><br /> **Input:**<br /><br /> `M`: `float`, `float2`, `float3` o `float4`<br /> Uno dei valori da moltiplicare.<br /><br /> `A`: uguale a `M` di input<br /> Uno dei valori da moltiplicare.<br /><br /> `B`: uguale a `M` di input<br /> Valori da aggiungere al prodotto degli altri due input.<br /><br /> **Output:**<br /><br /> `Output`: uguale a `M` di input<br /> Risultato dell'operazione di moltiplicazione e addizione, per componente.|nessuno|  
|**Max**|Calcola il valore massimo degli input specificati a livello di componente.<br /><br /> Per ciascun componente del risultato, viene preso il maggiore dei componenti corrispondenti degli input.<br /><br /> **Input:**<br /><br /> `X`: `float`, `float2`, `float3` o `float4`<br /> Uno dei valori di cui calcolare il massimo.<br /><br /> `Y`: uguale a `X` di input<br /> Uno dei valori di cui calcolare il massimo.<br /><br /> **Output:**<br /><br /> `Output`: uguale a `X` di input<br /> Valore massimo, per componente.|nessuno|  
|**Min**|Calcola il valore minimo degli input specificati a livello di componente.<br /><br /> Per ciascun componente del risultato, viene preso il minore dei componenti corrispondenti degli input.<br /><br /> **Input:**<br /><br /> `X`: `float`, `float2`, `float3` o `float4`<br /> Uno dei valori di cui calcolare il minimo.<br /><br /> `Y`: uguale a `X` di input<br /> Uno dei valori di cui calcolare il minimo.<br /><br /> **Output:**<br /><br /> `Output`: uguale a `X` di input<br /> Valore minimo, per componente.|nessuno|  
|**Per**|Calcola il prodotto degli input specificati a livello di componente.<br /><br /> Per ciascun componente del risultato, i componenti corrispondenti dei valori `X` e `Y` di input vengono moltiplicati insieme.<br /><br /> **Input:**<br /><br /> `X`: `float`, `float2`, `float3` o `float4`<br /> Uno dei valori da moltiplicare.<br /><br /> `Y`: uguale a `X` di input<br /> Uno dei valori da moltiplicare.<br /><br /> **Output:**<br /><br /> `Output`: uguale a `X` di input<br /> Il prodotto, per componente.|nessuno|  
|**Normalizza**|Normalizza il vettore specificato.<br /><br /> Un vettore normalizzato mantiene la direzione del vettore originale, ma non l'ampiezza. È possibile usare i vettori normalizzati per semplificare i calcoli in cui è importante l'ampiezza di un vettore.<br /><br /> **Input:**<br /><br /> `X`: `float2`, `float3` o `float4`<br /> Vettore da normalizzare.<br /><br /> **Output:**<br /><br /> `Output`: uguale a `X` di input<br /> Vettore normalizzato.|nessuno|  
|**Uno meno**|Calcola la differenza tra 1 e l'input specificato per ogni componente.<br /><br /> Per ciascun componente del risultato, il componente corrispondente dell'input viene sottratto da 1.<br /><br /> **Input:**<br /><br /> `X`: `float`, `float2`, `float3` o `float4`<br /> Valori da sottrarre da 1.<br /><br /> **Output:**<br /><br /> `Output`: uguale a `X` di input<br /> Differenza tra 1 e l'input specificato, per componente.|nessuno|  
|**Potenza**|Calcola l'elevamento a potenza degli input specificati a livello di componente.<br /><br /> Per ciascun componente del risultato, il componente corrispondente del valore `X` di input viene elevato alla potenza del componente corrispondente del valore `Y` di input.<br /><br /> **Input:**<br /><br /> `X`: `float`, `float2`, `float3` o `float4`<br /> Valori di base<br /><br /> `Y`: uguale a `X` di input<br /> Valori esponenziali.<br /><br /> **Output:**<br /><br /> `Output`: uguale a `X` di input<br /> Elevamento a potenza, per componente.|nessuno|  
|**Saturazione**|Fissa ogni componente dell'input specificato all'intervallo [0, 1].<br /><br /> È possibile usare questo intervallo per rappresentare le percentuali e altre misurazioni relative nei calcoli. Per ciascun componente del risultato, i valori dei componenti corrispondenti minori di 0 sono resi uguali a 0, i valori maggiori di 1 sono resi uguali a 1 e i valori compresi nell'intervallo non vengono modificati.<br /><br /> **Input:**<br /><br /> `X`: `float`, `float2`, `float3` o `float4`<br /> Valori da saturare.<br /><br /> **Output:**<br /><br /> `Output`: uguale a `X` di input<br /> Valore saturato, per componente.|nessuno|  
|**Seno**|Calcola il seno dell'input specificato, espresso in radianti, per ogni componente.<br /><br /> Per ciascun componente del risultato, viene calcolato il seno del componente corrispondente, fornito in radianti. Il risultato ha componenti con valori compresi nell'intervallo [-1, 1].<br /><br /> **Input:**<br /><br /> `X`: `float`, `float2`, `float3` o `float4`<br /> Valori di cui calcolare il seno, in radianti.<br /><br /> **Output:**<br /><br /> `Output`: uguale a `X` di input<br /> Seno, per componente.|nessuno|  
|**Sqrt**|Calcola la radice quadrata dell'input specificato, per ogni componente.<br /><br /> Per ciascun componente del risultato, viene calcolata la radice quadrata del componente corrispondente.<br /><br /> **Input:**<br /><br /> `X`: `float`, `float2`, `float3` o `float4`<br /> Valori per i quali calcolare la radice quadrata.<br /><br /> **Output:**<br /><br /> `Output`: uguale a `X` di input<br /> Radice quadrata, per componente.|nessuno|  
|**Sottrai**|Calcola la differenza tra gli input specificati a livello di componente.<br /><br /> Per ciascun componente del risultato, il componente corrispondente del valore `Y` di input viene sottratto dal componente corrispondente del valore `X` di input. È possibile usare questo valore per calcolare il vettore che si estende dal primo input al secondo.<br /><br /> **Input:**<br /><br /> `X`: `float`, `float2`, `float3` o `float4`<br /> Valori da cui sottrarre.<br /><br /> `Y`: uguale a `X` di input<br /> Valori da sottrarre all'input `X`.<br /><br /> **Output:**<br /><br /> `Output`: uguale a `X` di input<br /> Differenza, per componente.|nessuno|  
|**Trasforma vettore 3D**|Trasforma il vettore 3D specificato in un altro spazio.<br /><br /> È possibile usare questa operazione per portare punti o vettori in uno spazio comune e poterli usare per eseguire calcoli significativi.<br /><br /> **Input:**<br /><br /> `Vector`: `float3`<br /> Vettore da trasformare.<br /><br /> **Output:**<br /><br /> `Output`: `float3`<br /> Vettore trasformato.|**Da sistema**<br /> Spazio nativo del vettore.<br /><br /> **A sistema**<br /> Spazio in cui trasformare il vettore.|


