---
title: Previsto oggetto date | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 10af48c4804df3b5513df71578b948abe73ff8c2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572895"
---
# <a name="date-object-expected"></a>Previsto oggetto date
Si è provato a richiamare il metodo **date. Prototype. ToString** o **date. Prototype. valueOf** su un oggetto di un tipo diverso da `Date`. L'oggetto di questo tipo di chiamata deve essere di tipo `Date`. Ad esempio:  
  
```JavaScript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Richiamare solo i metodi **date. Prototype. ToString** o **date. Prototype. valueOf** su oggetti di tipo `Date`.  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Date](../../javascript/reference/date-object-javascript.md)   
 [Metodo getDate (date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Oggetti intrinseci](../../javascript/intrinsic-objects-javascript.md)