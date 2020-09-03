---
title: Intervallo non valido nel set di caratteri (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5021
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 971e9d5a-f88a-47a8-af94-f3c7c4aed5ab
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a81634a96fb85584c9176db8c72bfc5c3468dc2c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85816878"
---
# <a name="invalid-range-in-character-set-javascript"></a>Intervallo non valido nel set di caratteri (JavaScript)
Si è provato a creare un'espressione regolare con un intervallo di set di caratteri non valido. I set di caratteri devono variare solo da singoli caratteri, ad esempio a-z o 0-9; non è possibile includere classi di caratteri come \w in un set di caratteri. Il primo carattere nell'intervallo deve essere precedere anche dal secondo carattere nell'intervallo. Ad esempio:  
  
```JavaScript  
var good = /[a-z]/;     // A valid character range - a comes before z.  
var notGood = /[z-a]/;  // An invalid character range - z does not come before a.  
```  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Usare solo caratteri singoli per comporre il set di caratteri dell'espressione regolare e verificare che siano nell'ordine corretto.  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintassi delle espressioni regolari (JavaScript)](https://msdn.microsoft.com/library/1400241x)