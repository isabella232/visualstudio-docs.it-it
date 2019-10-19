---
title: Quantificatore imprevisto (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 2070ec6ad01eb62c6be9b6b9acfc91cba7bc863d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572531"
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
 @No__t_1 [oggetto Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)  
 [Sintassi delle espressioni regolari (JavaScript)](https://msdn.microsoft.com/library/1400241x)