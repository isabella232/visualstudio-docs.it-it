---
title: Previsto oggetto date | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5006
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d6ab82e6-ca64-46b4-a06c-5c6b0aa057cb
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 28531c1ac1dc73ca2bf309d412b08d23dd17bfb8
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862644"
---
# <a name="date-object-expected"></a>Previsto oggetto date
Si è provato a richiamare il metodo **date. Prototype. ToString** o **date. Prototype. valueOf** su un oggetto di un tipo diverso da `Date` . L'oggetto di questo tipo di chiamata deve essere di tipo `Date` . Ad esempio:  
  
```JavaScript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Richiamare solo i metodi **date. Prototype. ToString** o **date. Prototype. valueOf** su oggetti di tipo `Date` .  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto date](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Date)   
 [Metodo getDate (date)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Date/getdate)   
 [Oggetti intrinseci](https://developer.mozilla.org/docs/Learn/JavaScript/Objects)