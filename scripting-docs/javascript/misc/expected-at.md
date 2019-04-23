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
ms.openlocfilehash: aa2728306d9e650bf7f8b446b6af5a409a39d0e0
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60101561"
---
# <a name="expected-"></a>Previsto '\@'
Si è tentato di creare una variabile da utilizzare con le istruzioni di compilazione condizionale utilizzando il `@set` istruzione, ma non è stato inserito un simbolo di chiocciola "**@**" prima il nome della variabile.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Aggiungere un simbolo di chiocciola "**@**" immediatamente prima del nome della variabile. Ad esempio:  
  
    ```JavaScript  
    @set @myvar = 1  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [@set Istruzione](../../javascript/reference/at-set-statement-javascript.md)   
 [Compilazione condizionale](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variabili di compilazione condizionale](../../javascript/advanced/conditional-compilation-variables-javascript.md)
