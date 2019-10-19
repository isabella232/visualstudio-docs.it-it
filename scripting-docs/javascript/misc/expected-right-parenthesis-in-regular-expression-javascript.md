---
title: Previsto ')' nell'espressione regolare (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 7c10449df9ef3331949695b7423da3eb08b65433
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577535"
---
# <a name="expected--in-regular-expression-javascript"></a>Prevista ')' nell'espressione regolare (JavaScript)
Si è tentato di creare un'acquisizione, un'asserzione o un gruppo di espressioni regolari, ma non è stata inclusa la parentesi di chiusura. Le parentesi hanno diversi scopi nelle espressioni regolari. Vengono usati principalmente per acquisire sottoespressioni, per specificare asserzioni o per raggruppare i modelli in modo che gli elementi possano essere considerati come una singola unità per *, +,? e così via.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Aggiungere le parentesi di chiusura più a destra.  
  
    > [!NOTE]
    > Se si desidera trovare la corrispondenza con una sola parentesi, eseguire l'escape con una barra \\ rovesciata, in modo che non venga interpretata come carattere speciale per [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 @No__t_1 [oggetto Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)  
 [Sintassi delle espressioni regolari (JavaScript)](https://msdn.microsoft.com/library/1400241x)