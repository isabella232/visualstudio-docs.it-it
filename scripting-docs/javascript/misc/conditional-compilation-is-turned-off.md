---
title: Compilazione condizionale disattivata | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 56621d6f7fcc195a4ece7654adeafd1096c37e8b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572935"
---
# <a name="conditional-compilation-is-turned-off"></a>Compilazione condizionale disattivata
Si è provato a usare una variabile di compilazione condizionale senza prima attivare la compilazione condizionale. L'attivazione della compilazione condizionale indica al compilatore [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] di interpretare gli identificatori che iniziano con @ come variabili di compilazione condizionale. A tale scopo, iniziare il codice condizionale con l'istruzione:  
  
```js
/*@cc_on @*/  
```  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Aggiungere l'istruzione seguente all'inizio del codice condizionale:  
  
    ```JavaScript  
    /*@cc_on @*/  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 @No__t_1 di [compilazione condizionale](../../javascript/advanced/conditional-compilation-javascript.md)  
 [Variabili di compilazione condizionale](../../javascript/advanced/conditional-compilation-variables-javascript.md)    
 [istruzione @cc_on](../../javascript/reference/at-cc-on-statement-javascript.md)    
 [istruzione @if](../../javascript/reference/at-if-statement-javascript.md)    
 [Istruzione @set](../../javascript/reference/at-set-statement-javascript.md)