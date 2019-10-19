---
title: Previsto ']' nell'espressione regolare (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1ca2079a-44dd-479f-a1e3-e04a14d0739e
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9af38a5fa754a811416f1a998b90946345f3e4a2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576485"
---
# <a name="expected--in-regular-expression-javascript"></a>Prevista ']' nell'espressione regolare (JavaScript)
Si è tentato di creare una classe di caratteri per una corrispondenza di espressione regolare, ma non è stata inclusa la parentesi quadra chiusa. Le singole combinazioni di caratteri letterali possono essere assemblate in classi di caratteri inserendole tra parentesi quadre. Una classe di caratteri trova la corrispondenza con qualsiasi carattere contenuto. Ad esempio,/[ABC]/corrisponde a una qualsiasi delle lettere "a", "b" o "c".  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Aggiungere la parentesi quadra chiusa all'espressione regolare.  
  
    > [!NOTE]
    > Se si desidera trovare la corrispondenza con una singola parentesi, eseguire l'escape con una barra rovesciata-\\ [-in modo che non venga interpretata come carattere speciale per [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 @No__t_1 [oggetto Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)  
 [Sintassi delle espressioni regolari (JavaScript)](https://msdn.microsoft.com/library/1400241x)