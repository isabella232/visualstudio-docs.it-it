---
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
ms.openlocfilehash: f67f9a2fc81b0bd950e171e4274eb09eacd88bbc
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/09/2020
ms.locfileid: "91861858"
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
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Regular Expression](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/RegExp)   
 [Sintassi delle espressioni regolari (JavaScript)](/previous-versions/1400241x(v=vs.100))