---
description: Quando si compone il criterio di ricerca di espressioni regolari, è stato creato un elemento pattern con un fattore di ripetizione non valido.
title: Quantificatore imprevisto (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba6d34f9-2d6f-486c-a929-6cd9818be322
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9351f9306cea9e3f6346b007d6fe05c1d7bbf319
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571961"
---
# <a name="unexpected-quantifier-javascript"></a>Quantificatore imprevisto (JavaScript)
Quando si compone il criterio di ricerca di espressioni regolari, è stato creato un elemento pattern con un fattore di ripetizione non valido. Ad esempio, il modello  
  
```js
/^+/  
```  
  
 non è valido perché l'elemento ^ (inizio dell'input) non può avere un fattore di ripetizione. Nella tabella seguente sono elencati gli elementi che non possono avere fattori di ripetizione.  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|^|Inizio dell'input|  
|$|Fine dell'input|  
|\b|Confine di parola|  
|\B|Confine non alfanumerico|  
|*|Zero o più ripetizioni|  
|+|Una o più ripetizioni|  
|?|Nessuna o una ripetizione|  
|n|n ripetizioni|  
|{n,}|n o più ripetizioni|  
|{n, m}|Da n a m ripetizioni incluse|  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Verificare che l'elemento del criterio di ricerca contenga solo fattori di ripetizione legali.  
  
## <a name="see-also"></a>Vedi anche  
 [Oggetto Regular Expression](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/RegExp)   
 [Sintassi delle espressioni regolari (JavaScript)](/previous-versions/1400241x(v=vs.100))
