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
ms.openlocfilehash: df1c62c00fdfc8b2b28300cbca1052f0fa350b32
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576505"
---
# <a name="expected-"></a>Previsto '\@'
Si è provato a creare una variabile da usare con le istruzioni di compilazione condizionale usando l'istruzione `@set`, ma non è stato inserito un simbolo di chiocciola " **@** " prima del nome della variabile.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Aggiungere un simbolo di chiocciola " **@** " immediatamente prima del nome della variabile. Ad esempio:  
  
    ```JavaScript  
    @set @myvar = 1  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [istruzione@set](../../javascript/reference/at-set-statement-javascript.md)   
   di [compilazione condizionale](../../javascript/advanced/conditional-compilation-javascript.md)  
 [Variabili di compilazione condizionale](../../javascript/advanced/conditional-compilation-variables-javascript.md)
