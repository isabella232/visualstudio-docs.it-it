---
title: Quantificatore imprevisto (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba6d34f9-2d6f-486c-a929-6cd9818be322
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 693fdf4091a6f6fdf63c701b63c4355a67ee6fbd
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096746"
---
# <a name="unexpected-quantifier-javascript"></a>Quantificatore imprevisto (JavaScript)
Quando si crea un criterio di ricerca di espressioni regolari, è creato un elemento di modello con un fattore di ripetizioni non valido. Ad esempio, il criterio  
  
```js
/^+/  
```  
  
 non è valido perché l'elemento ^ (inizio dell'input) non può avere un fattore di ripetizione. Nella tabella seguente elenca gli elementi che non possono avere i fattori di ripetizione.  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|^|Inizio dell'input|  
|$|Konec vstupu|  
|\b|Confine di parola|  
|\B|Non costituisce un confine|  
|*|Zero o più ripetizioni|  
|+|Uno o più ripetizioni|  
|?|Uno o zero ripetizioni|  
|{n}|n ripetizioni|  
|{n}|n o altre ripetizioni|  
|{n, m}|Da n a m ripetizioni, inclusive|  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Verificare che l'elemento di modello di ricerca contiene solo i fattori di ripetizioni legali.  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto di espressione regolare](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintassi di espressione regolare (JavaScript)](https://msdn.microsoft.com/library/1400241x)