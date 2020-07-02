---
title: Non è possibile assegnare a un risultato della funzione | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 84ec3426c80da0578dda7cb99e9160b81e31ab87
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817632"
---
# <a name="cannot-assign-to-a-function-result"></a>Assegnazione a un risultato di funzione non consentita
Si è provato a assegnare un valore al risultato di una funzione. Il risultato di una funzione può essere assegnato a una variabile, ma non può essere utilizzato come variabile. Se si desidera assegnare un nuovo valore alla funzione stessa, omettere le parentesi (operatore di chiamata di funzione). Nell'esempio seguente viene illustrata una situazione in cui viene generato questo errore.  
  
```js
myFunction() = 42;  // Attempting to assign the value 42 to the result of the function call.  
```  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Non usare il valore di un risultato di una chiamata di funzione come un elemento a cui è possibile *assegnare*. È tuttavia possibile assegnare il risultato della chiamata di funzione *a una variabile* .  
  
    ```JavaScript  
    myVar = myFunction(42);  
    ```  
  
- In alternativa, è possibile assegnare la funzione stessa (e non il relativo valore restituito) a una variabile.  
  
    ```JavaScript  
    myFunction = new Function("return 42;");  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Function](../../javascript/reference/function-object-javascript.md)   
 [Scrittura di codice JavaScript](../../javascript/writing-javascript-code.md)   
 [Funzioni](../../javascript/functions-javascript.md)