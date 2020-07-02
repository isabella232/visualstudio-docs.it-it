---
title: Previsto ' @' | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 209a8793c0940511b7ecb2abb32f537a614ebf8b
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85814824"
---
# <a name="expected-"></a>Previsto ' \@ '
Si è provato a creare una variabile da usare con le istruzioni di compilazione condizionale usando l' `@set` istruzione, ma non è stato inserito un simbolo di chiocciola " **@** " prima del nome della variabile.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Aggiungere un simbolo di chiocciola " **@** " immediatamente prima del nome della variabile. Ad esempio:  
  
    ```JavaScript  
    @set @myvar = 1  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [@setIstruzione](../../javascript/reference/at-set-statement-javascript.md)   
 [Compilazione condizionale](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variabili di compilazione condizionale](../../javascript/advanced/conditional-compilation-variables-javascript.md)
