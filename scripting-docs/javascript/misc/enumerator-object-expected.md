---
description: Si è provato a richiamare il Metodo Enumerator. Prototype. atEnd, Enumerator. Prototype. Item, Enumerator. Prototype. moveFirst o Enumerator. Prototype. moveNext su un oggetto di un tipo diverso da Enumerator.
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
ms.openlocfilehash: 9fc48ca3e0f17d97af3d538033c2319538afc079
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571051"
---
# <a name="enumerator-object-expected"></a>Previsto oggetto Enumerator
Si è provato a richiamare il metodo **Enumerator. Prototype. atEnd, Enumerator. Prototype. Item, Enumerator. Prototype. MoveFirst** o **Enumerator. Prototype. MoveNext** su un oggetto di un tipo diverso da `Enumerator` . L'oggetto di questo tipo di chiamata deve essere di tipo `Enumerator` . Di seguito è riportato un esempio di codice che interrompe questa regola:  
  
```JavaScript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Richiamare solo i metodi **Enumerator. Prototype. atEnd**, **Enumerator. Prototype. Item**, **Enumerator. Prototype. MoveFirst** o **Enumerator. Prototype. MoveNext** su oggetti di tipo `Enumerator` . Per determinare se l'oggetto è un `Enumerator` oggetto, usare:  
  
    ```js
    if(x instanceof Enumerator)  
    ```  
  
## <a name="see-also"></a>Vedi anche  
 [Oggetto Enumerator](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/Enumerator)
