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
ms.openlocfilehash: 969f2bcb578d74ac02a7bdaa6984de5948e49e27
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817606"
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
 [Oggetto date](../../javascript/reference/date-object-javascript.md)   
 [Metodo getDate (date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Oggetti intrinseci](../../javascript/intrinsic-objects-javascript.md)