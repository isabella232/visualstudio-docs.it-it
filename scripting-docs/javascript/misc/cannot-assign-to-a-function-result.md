---
title: Non è possibile assegnare a un risultato di funzione | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5003
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ee8ffb3a-1451-4cb3-99bf-5e9cf8b77d79
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 226056f139e45f432d757aff8f8774b013742de3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946602"
---
# <a name="cannot-assign-to-a-function-result"></a>Assegnazione a un risultato di funzione non consentita
Si è provato ad assegnare un valore a un risultato di funzione. Il risultato di una funzione può essere assegnato a una variabile, ma non può essere usato come una variabile. Se si desidera assegnare un nuovo valore alla funzione stessa, omettere le parentesi (l'operatore di chiamata di funzione). L'esempio seguente illustra una situazione in cui viene generato questo errore.  
  
```js
myFunction() = 42;  // Attempting to assign the value 42 to the result of the function call.  
```  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Non usare il valore del risultato di una chiamata di funzione come un elemento è possibile *assegnare al*. È possibile assegnare il risultato della chiamata alla funzione *a una variabile* se.  
  
    ```JavaScript  
    myVar = myFunction(42);  
    ```  
  
- In alternativa, è possibile assegnare la funzione stessa (e non il relativo valore restituito) a una variabile.  
  
    ```JavaScript  
    myFunction = new Function("return 42;");  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto funzione](../../javascript/reference/function-object-javascript.md)   
 [Scrittura di codice JavaScript](../../javascript/writing-javascript-code.md)   
 [Funzioni](../../javascript/functions-javascript.md)