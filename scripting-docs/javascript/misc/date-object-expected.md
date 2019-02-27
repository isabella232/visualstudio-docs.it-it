---
title: Previsto oggetto Date | Microsoft Docs
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
ms.openlocfilehash: a53ff758622cf719c2b10ea47fc516ac8684eb6a
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/26/2019
ms.locfileid: "56842247"
---
# <a name="date-object-expected"></a>Previsto oggetto date
Si è provato a richiamare il **Date.prototype.toString** oppure **Date.prototype.valueOf** metodo in un oggetto di un tipo diverso da `Date`. L'oggetto di questo tipo di chiamata deve essere di tipo `Date`. Ad esempio:  
  
```JavaScript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Richiamare solo le **Date.prototype.toString** oppure **Date.prototype.valueOf** metodi su oggetti di tipo `Date`.  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Date](../../javascript/reference/date-object-javascript.md)   
 [Metodo getDate (Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Oggetti intrinseci](../../javascript/intrinsic-objects-javascript.md)