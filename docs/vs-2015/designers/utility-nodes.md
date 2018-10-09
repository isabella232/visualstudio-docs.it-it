---
title: Nodi di utilità | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff732221-b731-424c-ad5b-82ef5f21dff5
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: fa242e6c2f609c8ac6214fcbd20d210f7c794b77
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526798"
---
# <a name="utility-nodes"></a>Nodi utilità
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [nodi di utilità](https://docs.microsoft.com/visualstudio/designers/utility-nodes).  
  
Nella finestra di progettazione shader, i nodi di utilità rappresentano utili e comuni calcoli dello shader che non rientrano nelle altre categorie. Alcuni nodi di utilità eseguono operazioni semplici come aggiungere vettori o scegliere i risultati in modo condizionale, mentre altri eseguono operazioni complesse come calcolare i contributi dell'illuminazione in base a modelli comuni di illuminazione.  
  
## <a name="utility-node-reference"></a>Riferimento per i nodi di utilità  
  
|Nodo|Dettagli|Proprietà|  
|----------|-------------|----------------|  
|**Aggiungi vettore**|Crea un vettore aggiungendo gli input specificati.<br /><br /> **Input:**<br /><br /> `Vector`: `float`, `float2` o `float3`<br /> Valori a cui aggiungere gli input.<br /><br /> `Value to Append`: `float`<br /> Valore da accodare.<br /><br /> **Output:**<br /><br /> `Output`: `float2`, `float3` o `float4` in base al tipo di input `Vector`<br /> Nuovo vettore.|nessuno|  
|**Fresnel**|Calcola la caduta Fresnel in base alla normale alla superficie specificata.<br /><br /> Il valore di caduta Fresnel indica quanto sia vicina la coincidenza della normale alla superficie del pixel corrente al vettore di visualizzazione. Quando i vettori sono allineati, il risultato della funzione è 0; il risultato aumenta man mano che i vettori sono meno simili e raggiunge il massimo quando i vettori sono ortogonali. È possibile usare questo valore per ottenere un effetto più o meno apparente in base alla relazione tra l'orientamento del pixel corrente e della camera.<br /><br /> **Input:**<br /><br /> `Surface Normal`: `float3`<br /> Normale alla superficie del pixel corrente, definita nello spazio tangente del pixel corrente. È possibile usare questa impostazione per intervenire sulla normale alla superficie apparente, come nel mapping di normali.<br /><br /> **Output:**<br /><br /> `Output`: `float`<br /> Riflesso del pixel corrente.|**Esponente**<br /> Esponente usato per calcolare la caduta Fresnel.|  
|**Se**|Per ogni componente, sceglie in modo condizionale uno di tre possibili risultati. La condizione viene definita dalla relazione tra altri due input specificati.<br /><br /> Per ciascun componente del risultato, viene scelto il componente corrispondente di uno dei tre possibili risultati, in base alla relazione tra i componenti corrispondenti dei primi due input.<br /><br /> **Input:**<br /><br /> `X`: `float`, `float2`, `float3` o `float4`<br /> Valore di sinistra da confrontare.<br /><br /> `Y`: stesso tipo dell'input `X`<br /> Valore di destra da confrontare.<br /><br /> `X > Y`: stesso tipo dell'input `X`<br /> Valori che vengono scelti quando `X` è maggiore di `Y`.<br /><br /> `X = Y`: stesso tipo dell'input `X`<br /> Valori che vengono scelti quando `X` è uguale a `Y`.<br /><br /> `X < Y`: stesso tipo dell'input `X`<br /> Valori che vengono scelti quando `X` è minore di `Y`.<br /><br /> **Output:**<br /><br /> `Output`: `float3`<br /> Risultato scelto, per componente.|nessuno|  
|**Lambert**|Calcola il colore del pixel corrente in base al modello di illuminazione Lambert, usando la normale alla superficie specificata.<br /><br /> Questo colore è la somma del colore ambientale e dei contributi di illuminazione con riflessione diffusa sotto l'illuminazione diretta. Il colore ambientale si avvicina al contributo totale di illuminazione indiretta, ma risulta piatto e opaco senza l'ausilio di illuminazione aggiuntiva. L'illuminazione con riflessione diffusa agevola l'aggiunta di forma e profondità a un oggetto.<br /><br /> **Input:**<br /><br /> `Surface Normal`: `float3`<br /> Normale alla superficie del pixel corrente, definita nello spazio tangente del pixel corrente. È possibile usare questa impostazione per intervenire sulla normale alla superficie apparente, come nel mapping di normali.<br /><br /> `Diffuse Color`: `float3`<br /> Colore con riflessione diffusa del pixel corrente, in genere il **Colore punto**. Se non viene fornito alcun input, il valore predefinito è bianco.<br /><br /> **Output:**<br /><br /> `Output`: `float3`<br /> Colore con riflessione diffusa del pixel corrente.|nessuno|  
|**Mascheramento vettore**|Nasconde i componenti del vettore specificato.<br /><br /> È possibile usare questo valore per rimuovere canali di colore specifici da un valore di colore o per evitare un effetto su componenti specifici nei calcoli successivi.<br /><br /> **Input:**<br /><br /> `Vector`: `float4`<br /> Vettore da nascondere.<br /><br /> **Output:**<br /><br /> `Output`: `float4`<br /> Vettore nascosto.|**Rosso / X**<br /> **False** per nascondere il componente rosso (x); in caso contrario **True**.<br /><br /> **Verde / Y**<br /> **False** per nascondere il componente verde (y); in caso contrario **True**.<br /><br /> **Blu / Z**<br /> **False**per nascondere il componente blu (z); in caso contrario **True**.<br /><br /> **Alfa / W**<br /> **False** per nascondere il componente alfa (w); in caso contrario **True**.|  
|**Vettore riflesso**|Calcola il vettore riflesso per il pixel corrente nello spazio tangente, in base alla posizione della camera.<br /><br /> È possibile usare questo valore per calcolare i riflessi, le coordinate della mappa cubi e i contributi di illuminazione speculare.<br /><br /> **Input:**<br /><br /> `Tangent Space Surface Normal`: `float3`<br /> Normale alla superficie del pixel corrente, definita nello spazio tangente del pixel corrente. È possibile usare questa impostazione per intervenire sulla normale alla superficie apparente, come nel mapping di normali.<br /><br /> **Output:**<br /><br /> `Output`: `float3`<br /> Vettore riflesso.|nessuno|  
|**Speculare**|Calcola il contributo di illuminazione speculare, in base al modello di illuminazione Phong, usando la normale alla superficie specificata.<br /><br /> L'illuminazione speculare dà un aspetto brillante e riflettente a un oggetto, ad esempio acqua, plastica o metalli.<br /><br /> **Input:**<br /><br /> `Surface Normal`: `float3`<br /> Normale alla superficie del pixel corrente, definita nello spazio tangente del pixel corrente. È possibile usare questa impostazione per intervenire sulla normale alla superficie apparente, come nel mapping di normali.<br /><br /> **Output:**<br /><br /> `Output`: `float3`<br /> Contributo di colore delle evidenziazioni speculari.|nessuno|


