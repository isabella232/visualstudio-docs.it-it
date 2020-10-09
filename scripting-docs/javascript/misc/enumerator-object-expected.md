---
title: Previsto oggetto enumeratore | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5015
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: dc6e32c1-a6e6-4e12-ac99-e3f65f91c8d7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5e63ee2970c90ffcfff5c02a384d3346b3ea6229
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862626"
---
# <a name="enumerator-object-expected"></a>Previsto oggetto Enumerator
Si è provato a richiamare il metodo **Enumerator. Prototype. atEnd, Enumerator. Prototype. Item, Enumerator. Prototype. MoveFirst** o **Enumerator. Prototype. MoveNext** su un oggetto di un tipo diverso da `Enumerator` . L'oggetto di questo tipo di chiamata deve essere di tipo `Enumerator` . Di seguito è riportato un esempio di codice che interrompe questa regola:  
  
```JavaScript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Richiamare solo i metodi **Enumerator. Prototype. atEnd**, **Enumerator. Prototype. Item**, **Enumerator. Prototype. MoveFirst**o **Enumerator. Prototype. MoveNext** su oggetti di tipo `Enumerator` . Per determinare se l'oggetto è un `Enumerator` oggetto, usare:  
  
    ```js
    if(x instanceof Enumerator)  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Enumerator](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/Enumerator)