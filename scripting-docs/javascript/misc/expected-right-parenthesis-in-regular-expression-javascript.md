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
ms.openlocfilehash: af32127476c83100c0340021428e3abc572ef2f7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85815643"
---
# <a name="expected--in-regular-expression-javascript"></a>Prevista ')' nell'espressione regolare (JavaScript)
Si è tentato di creare un'acquisizione, un'asserzione o un gruppo di espressioni regolari, ma non è stata inclusa la parentesi di chiusura. Le parentesi hanno diversi scopi nelle espressioni regolari. Vengono usati principalmente per acquisire sottoespressioni, per specificare asserzioni o per raggruppare i modelli in modo che gli elementi possano essere considerati come una singola unità per *, +,? e così via.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Aggiungere le parentesi di chiusura più a destra.  
  
    > [!NOTE]
    > Se si desidera trovare la corrispondenza con una sola parentesi, eseguire l'escape con una barra rovesciata, in \\ modo che non venga interpretata come carattere speciale da [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] .  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintassi delle espressioni regolari (JavaScript)](https://msdn.microsoft.com/library/1400241x)