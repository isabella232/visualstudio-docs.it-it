---
title: Nodi dei parametri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: da54db0b-3a3d-48dc-858c-7ac43aa04b13
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 110f380f7450d611de5786fb865bdee8e64195f6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54764171"
---
# <a name="parameter-nodes"></a>Nodi Parameter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nella finestra di progettazione shader, i nodi dei parametri rappresentano gli input dello shader controllati dall'app in base al disegno e includono, ad esempio, proprietà materiali, luci direzionali, posizione della fotocamera e ora. Questi parametri possono essere modificati a ogni chiamata di disegno e, quindi, è possibile usare lo stesso shader per fornire aspetti diversi a uno stesso oggetto.  
  
## <a name="parameter-node-reference"></a>Riferimento per i nodi dei parametri  
  
|Nodo|Dettagli|Proprietà|  
|----------|-------------|----------------|  
|**Posizione globale fotocamera**|Posizione della camera nello spazio globale.<br /><br /> **Output:**<br /><br /> `Output`: `float4`<br /> Posizione della camera.|nessuno|  
|**Direzione luce**|Vettore che definisce la direzione in cui viene diffusa la luce da una sorgente di luce nello spazio globale.<br /><br /> È possibile usare questo valore per calcolare i contributi di illuminazione e speculari nello spazio globale.<br /><br /> **Output:**<br /><br /> `Output`: `float3`<br /> Il vettore dal pixel corrente a una sorgente di luce.|nessuno|  
|**Ambiente materiale**|Contributo di colore con riflessione diffusa del pixel corrente attribuito all'illuminazione indiretta.<br /><br /> Il colore con riflessione diffusa di un pixel simula l'interazione dell'illuminazione con superfici ruvide. È possibile usare il parametro Ambiente materiale per approssimare il modo in cui l'illuminazione indiretta contribuisce all'aspetto di un oggetto nel mondo reale.<br /><br /> **Output:**<br /><br /> `Output`: `float4`<br /> Colore con riflessione diffusa del pixel corrente, in base all'illuminazione indiretta, ovvero alla luce ambientale.|**Accesso**<br /> **Pubblico** per consentire l'impostazione della proprietà dall'editor dei modelli. **Privato** in caso contrario.<br /><br /> **Valore**<br /> Colore con riflessione diffusa del pixel corrente, in base all'illuminazione indiretta, ovvero alla luce ambientale.|  
|**Materiale diffuso**|Colore che descrive il modo in cui il pixel corrente diffonde l'illuminazione diretta.<br /><br /> Il colore con riflessione diffusa di un pixel simula l'interazione dell'illuminazione con superfici ruvide. È possibile usare il parametro Materiale diffuso per modificare il modo in cui il pixel corrente diffonde l'illuminazione diretta, ovvero la luce direzionale, la luce puntiforme e la luce spot.<br /><br /> **Output:**<br /><br /> `Output`: `float4`<br /> Colore che descrive il modo in cui il pixel corrente diffonde l'illuminazione diretta.|**Accesso**<br /> **Pubblico** per consentire l'impostazione della proprietà dall'editor dei modelli. **Privato** in caso contrario.<br /><br /> **Valore**<br /> Colore che descrive il modo in cui il pixel corrente diffonde l'illuminazione diretta.|  
|**Materiale emissivo**|Contributo di colore del pixel corrente attribuito all'illuminazione autofornita.<br /><br /> È possibile usare questo valore per simulare un oggetto brillante, ovvero un oggetto che ha una luce propria. Questa luce non agisce su nessun altro oggetto.<br /><br /> **Output:**<br /><br /> `Output`: `float4`<br /> Contributo di colore del pixel corrente, in base all'illuminazione autofornita.|**Accesso**<br /> **Pubblico** per consentire l'impostazione della proprietà dall'editor dei modelli. **Privato** in caso contrario.<br /><br /> **Valore**<br /> Contributo di colore del pixel corrente, in base all'illuminazione autofornita.|  
|**Materiale speculare**|Colore che descrive il modo in cui l'illuminazione diretta viene riflessa dal pixel corrente.<br /><br /> Il colore speculare di un pixel simula l'interazione dell'illuminazione con superfici lisce come gli specchi. È possibile usare il parametro Materiale speculare per modificare il modo in cui il pixel corrente riflette l'illuminazione diretta, ovvero la luce direzionale, la luce puntiforme e la luce spot.<br /><br /> **Output:**<br /><br /> `Output`: `float4`<br /> Colore che descrive il modo in cui l'illuminazione diretta viene riflessa dal pixel corrente.|**Accesso**<br /> **Pubblico** per consentire l'impostazione della proprietà dall'editor dei modelli. **Privato** in caso contrario.<br /><br /> **Valore**<br /> Colore che descrive il modo in cui l'illuminazione diretta viene riflessa dal pixel corrente.|  
|**Materiale potenza speculare**|Valore scalare che descrive l'intensità delle evidenziazioni speculari.<br /><br /> Maggiore è la potenza speculare, più intense e lunghe diventano le evidenziazioni speculari.<br /><br /> **Output:**<br /><br /> `Output`: `float`<br /> Termine esponenziale che descrive l'intensità delle evidenziazioni speculari nel pixel corrente.|**Accesso**<br /> **Pubblico** per consentire l'impostazione della proprietà dall'editor dei modelli. **Privato** in caso contrario.<br /><br /> **Valore**<br /> Esponente che definisce l'intensità delle evidenziazioni speculari nel pixel corrente.|  
|**Tempo normalizzato**|Tempo in secondi, normalizzato sull'intervallo [0, 1], in modo che quando il tempo raggiunge 1, viene automaticamente reimpostato su 0.<br /><br /> È possibile usare questo valore come parametro nei calcoli dello shader, ad esempio per animare coordinate di trama, valori di colore o altri attributi.<br /><br /> **Output:**<br /><br /> `Output`: `float`<br /> Tempo normalizzato, in secondi.|nessuno|  
|**Ora**|Tempo espresso in secondi.<br /><br /> È possibile usare questo valore come parametro nei calcoli dello shader, ad esempio per animare coordinate di trama, valori di colore o altri attributi.<br /><br /> **Output:**<br /><br /> `Output`: `float`<br /> Tempo, in secondi.|nessuno|
