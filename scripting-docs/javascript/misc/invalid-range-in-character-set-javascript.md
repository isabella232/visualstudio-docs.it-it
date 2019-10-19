---
title: Intervallo non valido nel set di caratteri (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 29f28f0ceeb6bd1bf0a8f28438afd803d3a9a9ac
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576625"
---
# <a name="invalid-range-in-character-set-javascript"></a>Intervallo non valido nel set di caratteri (JavaScript)
Si è provato a creare un'espressione regolare con un intervallo di set di caratteri non valido. I set di caratteri devono variare solo da singoli caratteri, ad esempio a-z o 0-9; non è possibile includere classi di caratteri come \w in un set di caratteri. Il primo carattere nell'intervallo deve essere precedere anche dal secondo carattere nell'intervallo. Esempio:  
  
```JavaScript  
var good = /[a-z]/;     // A valid character range - a comes before z.  
var notGood = /[z-a]/;  // An invalid character range - z does not come before a.  
```  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Usare solo caratteri singoli per comporre il set di caratteri dell'espressione regolare e verificare che siano nell'ordine corretto.  
  
## <a name="see-also"></a>Vedere anche  
 @No__t_1 [oggetto Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)  
 [Sintassi delle espressioni regolari (JavaScript)](https://msdn.microsoft.com/library/1400241x)