---
title: Funzione prevista | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5002
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f62ade94-9f6f-4832-9b9b-49a06a385bbe
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2028d8923c2f81d1d99fec752d7ac0ce2fb32f65
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862168"
---
# <a name="function-expected"></a>Prevista funzione
Si è provato a richiamare uno dei metodi del **prototipo di funzione** su un oggetto che non era un `Function` oggetto oppure è stato usato un oggetto in un contesto di chiamata di funzione. Il codice seguente, ad esempio, genera questo errore perché **ad esempio** non è una funzione.  
  
```JavaScript  
var example = new Object();  // Create a new object called "example".  
var x = example();           // Try and call example as if it were a function.  
```  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Chiamare solo i metodi del **prototipo di funzione** sugli `Function` oggetti.  
  
- Assicurarsi di usare l'operatore `()` di chiamata di funzione per chiamare solo funzioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Function](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function)   
 [Proprietà prototype (Object)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)