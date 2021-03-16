---
description: Si è provato a creare un'espressione regolare con un intervallo di set di caratteri non valido.
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
ms.openlocfilehash: 9441f9cfd3adf94ddd38841d522c83922c9154f1
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571675"
---
# <a name="invalid-range-in-character-set-javascript"></a>Intervallo non valido nel set di caratteri (JavaScript)
Si è provato a creare un'espressione regolare con un intervallo di set di caratteri non valido. I set di caratteri devono variare solo da singoli caratteri, ad esempio a-z o 0-9; non è possibile includere classi di caratteri come \w in un set di caratteri. Il primo carattere nell'intervallo deve essere precedere anche dal secondo carattere nell'intervallo. Ad esempio:  
  
```JavaScript  
var good = /[a-z]/;     // A valid character range - a comes before z.  
var notGood = /[z-a]/;  // An invalid character range - z does not come before a.  
```  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Usare solo caratteri singoli per comporre il set di caratteri dell'espressione regolare e verificare che siano nell'ordine corretto.  
  
## <a name="see-also"></a>Vedi anche  
 [Oggetto Regular Expression](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/RegExp)   
 [Sintassi delle espressioni regolari (JavaScript)](/previous-versions/1400241x(v=vs.100))
