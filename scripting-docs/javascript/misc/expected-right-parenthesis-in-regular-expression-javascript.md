---
title: Previsto ')' nell'espressione regolare (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5020
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2087ba1d-9783-4d40-b609-e8542f579f7f
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 29b25b5ab48ffe0a9a9dfafa9e60d66913c5e25e
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/09/2020
ms.locfileid: "91861897"
---
# <a name="expected--in-regular-expression-javascript"></a>Prevista ')' nell'espressione regolare (JavaScript)
Si è tentato di creare un'acquisizione, un'asserzione o un gruppo di espressioni regolari, ma non è stata inclusa la parentesi di chiusura. Le parentesi hanno diversi scopi nelle espressioni regolari. Vengono usati principalmente per acquisire sottoespressioni, per specificare asserzioni o per raggruppare i modelli in modo che gli elementi possano essere considerati come una singola unità per *, +,? e così via.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Aggiungere le parentesi di chiusura più a destra.  
  
    > [!NOTE]
    > Se si desidera trovare la corrispondenza con una sola parentesi, eseguire l'escape con una barra rovesciata, in \\ modo che non venga interpretata come carattere speciale da [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] .  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Regular Expression](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/RegExp)   
 [Sintassi delle espressioni regolari (JavaScript)](/previous-versions/1400241x(v=vs.100))