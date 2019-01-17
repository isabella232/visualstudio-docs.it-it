---
title: Previsto oggetto Enumerator | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5015
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: dc6e32c1-a6e6-4e12-ac99-e3f65f91c8d7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 002c3a748af8f7fa5c21109adcb279f893b38965
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347242"
---
# <a name="enumerator-object-expected"></a>Previsto oggetto Enumerator
Si è provato a richiamare il **metodo Enumerator.prototype.atEnd, Enumerator.prototype.item, Enumerator.prototype.moveFirst,** oppure **Enumerator.prototype.moveNext** metodo in un oggetto di un tipo diverso rispetto a `Enumerator`. L'oggetto di questo tipo di chiamata deve essere di tipo `Enumerator`. Ecco un esempio di codice che causa l'interruzione di questa regola:  
  
```JavaScript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Richiamare solo le **metodo Enumerator.prototype.atEnd**, **Enumerator.prototype.item**, **Enumerator.prototype.moveFirst**, o  **Enumerator.prototype.moveNext** metodi su oggetti di tipo `Enumerator`. Per determinare se l'oggetto è un `Enumerator` oggetto, usare:  
  
    ```js
    if(x instanceof Enumerator)  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Enumerator](../../javascript/reference/enumerator-object-javascript.md)