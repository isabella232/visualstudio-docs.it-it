---
title: Funzione prevista | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 988ca00613d3dec4c55309fd77bc43705a6038ae
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576588"
---
# <a name="function-expected"></a>Prevista funzione
Si è provato a richiamare uno dei metodi del **prototipo di funzione** su un oggetto che non è un oggetto `Function` oppure è stato usato un oggetto in un contesto di chiamata di funzione. Il codice seguente, ad esempio, genera questo errore perché **ad esempio** non è una funzione.  
  
```JavaScript  
var example = new Object();  // Create a new object called "example".  
var x = example();           // Try and call example as if it were a function.  
```  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Chiamare solo i metodi del **prototipo di funzione** su oggetti `Function`.  
  
- Assicurarsi di usare l'operatore di chiamata di funzione `()` per chiamare solo funzioni.  
  
## <a name="see-also"></a>Vedere anche  
 @No__t_1 [oggetto funzione](../../javascript/reference/function-object-javascript.md)  
 [Proprietà prototype (Object)](../../javascript/reference/prototype-property-object-javascript.md)