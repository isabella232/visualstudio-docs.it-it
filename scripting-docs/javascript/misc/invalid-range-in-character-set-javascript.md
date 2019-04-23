---
title: Intervallo non valido nel carattere set (JavaScript) | Microsoft Docs
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
ms.openlocfilehash: 1cbfa4de401c2a1dc0626f8f00dbb0bd1bf24408
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60079591"
---
# <a name="invalid-range-in-character-set-javascript"></a>Intervallo non valido nel set di caratteri (JavaScript)
Si è provato a creare un'espressione regolare con un intervallo di set di caratteri non validi. Set di caratteri deve essere compresa tra singoli caratteri, ad esempio a-z o 0-9; è possibile includere le classi di caratteri, ad esempio \w in un set di caratteri. Il primo carattere dell'intervallo di inoltre deve precedere il secondo carattere compreso nell'intervallo. Ad esempio:  
  
```JavaScript  
var good = /[a-z]/;     // A valid character range - a comes before z.  
var notGood = /[z-a]/;  // An invalid character range - z does not come before a.  
```  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Usare solo singoli caratteri per comporre il set di caratteri espressione regolare e assicurarsi che siano nell'ordine corretto.  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto di espressione regolare](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintassi di espressione regolare (JavaScript)](https://msdn.microsoft.com/library/1400241x)