---
title: Compilazione condizionale disattivata | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 59a030b0-a6c6-47f2-b90e-c0ed204d5116
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da272529768f3227ce6e0ee3e0ebbf086140dd15
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85816124"
---
# <a name="conditional-compilation-is-turned-off"></a>Compilazione condizionale disattivata
Si è provato a usare una variabile di compilazione condizionale senza prima attivare la compilazione condizionale. L'attivazione della compilazione condizionale indica al [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] compilatore di interpretare gli identificatori che iniziano con @ come variabili di compilazione condizionale. A tale scopo, iniziare il codice condizionale con l'istruzione:  
  
```js
/*@cc_on @*/  
```  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Aggiungere l'istruzione seguente all'inizio del codice condizionale:  
  
    ```JavaScript  
    /*@cc_on @*/  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Compilazione condizionale](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variabili di compilazione condizionale](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc_onIstruzione](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@ifIstruzione](../../javascript/reference/at-if-statement-javascript.md)   
 [@setIstruzione](../../javascript/reference/at-set-statement-javascript.md)