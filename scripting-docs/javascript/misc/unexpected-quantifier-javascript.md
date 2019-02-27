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
ms.openlocfilehash: f18195f344adca16fce7403d225c42826a2af544
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/26/2019
ms.locfileid: "56843403"
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
|{n,}|n o altre ripetizioni|  
|{n,m}|Da n a m ripetizioni, inclusive|  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Verificare che l'elemento di modello di ricerca contiene solo i fattori di ripetizioni legali.  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto di espressione regolare](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintassi di espressione regolare (JavaScript)](https://msdn.microsoft.com/library/1400241x)