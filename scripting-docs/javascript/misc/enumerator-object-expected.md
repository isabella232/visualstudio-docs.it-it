---
title: Previsto oggetto enumeratore | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: d90b6b923f631c7785428a1b3879528e97c1bfd6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572873"
---
# <a name="enumerator-object-expected"></a>Previsto oggetto Enumerator
Si è provato a richiamare il metodo **Enumerator. Prototype. atEnd, Enumerator. Prototype. Item, Enumerator. Prototype. MoveFirst** o **Enumerator. Prototype. MoveNext** su un oggetto di un tipo diverso da `Enumerator`. L'oggetto di questo tipo di chiamata deve essere di tipo `Enumerator`. Di seguito è riportato un esempio di codice che interrompe questa regola:  
  
```JavaScript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Richiamare solo i metodi **Enumerator. Prototype. atEnd**, **Enumerator. Prototype. Item**, **Enumerator. Prototype. MoveFirst**o **Enumerator. prototype. MoveNext** su oggetti di tipo `Enumerator`. Per determinare se l'oggetto è un oggetto `Enumerator`, usare:  
  
    ```js
    if(x instanceof Enumerator)  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Enumerator](../../javascript/reference/enumerator-object-javascript.md)