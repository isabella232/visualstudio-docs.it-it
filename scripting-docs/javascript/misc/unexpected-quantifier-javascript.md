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
ms.openlocfilehash: ef0955bac35009d9b6c82f1856bb9005a08043ad
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2018
ms.locfileid: "44282266"
---
# <a name="unexpected-quantifier-javascript"></a>Quantificatore imprevisto (JavaScript)
Quando si crea un criterio di ricerca di espressioni regolari, è creato un elemento di modello con un fattore di ripetizioni non valido. Ad esempio, il criterio  
  
```  
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