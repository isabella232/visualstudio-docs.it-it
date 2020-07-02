---
title: Previsto ']' nell'espressione regolare (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 8a2a2b83b818e37c0b62e103fe284c5c4d110c6c
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85815631"
---
# <a name="expected--in-regular-expression-javascript"></a>Prevista ']' nell'espressione regolare (JavaScript)
Si è tentato di creare una classe di caratteri per una corrispondenza di espressione regolare, ma non è stata inclusa la parentesi quadra chiusa. Le singole combinazioni di caratteri letterali possono essere assemblate in classi di caratteri inserendole tra parentesi quadre. Una classe di caratteri trova la corrispondenza con qualsiasi carattere contenuto. Ad esempio,/[ABC]/corrisponde a una qualsiasi delle lettere "a", "b" o "c".  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Aggiungere la parentesi quadra chiusa all'espressione regolare.  
  
    > [!NOTE]
    > Se si desidera trovare la corrispondenza con una singola parentesi quadre, eseguire l'escape con una barra rovesciata, in \\ modo che non venga interpretata come carattere speciale da [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] .  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintassi delle espressioni regolari (JavaScript)](https://msdn.microsoft.com/library/1400241x)