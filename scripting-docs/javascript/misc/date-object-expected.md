---
title: Previsto oggetto Date | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5006
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d6ab82e6-ca64-46b4-a06c-5c6b0aa057cb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 05e27b822f933ade811084552f6f0379257ae82e
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349114"
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