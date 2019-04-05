---
title: Previsto '@' | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1032
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 82ff8b74-1710-4358-9a26-dc92ab29c53b
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da8eb2f21cbe7ef611aaba863e853a2fe7a71753
ms.sourcegitcommit: b6177ce198c7c5a00030604c9d4faa735405d5df
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/04/2019
ms.locfileid: "59018311"
---
# <a name="expected-"></a>Previsto '\@'
Si è tentato di creare una variabile da utilizzare con le istruzioni di compilazione condizionale utilizzando il `@set` istruzione, ma non è stato inserito un simbolo di chiocciola "**@**" prima il nome della variabile.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Aggiungere un simbolo di chiocciola "**@**" immediatamente prima del nome della variabile. Ad esempio:  
  
    ```JavaScript  
    @set @myvar = 1  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [@set Istruzione](../../javascript/reference/at-set-statement-javascript.md)   
 [Compilazione condizionale](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variabili di compilazione condizionale](../../javascript/advanced/conditional-compilation-variables-javascript.md)
