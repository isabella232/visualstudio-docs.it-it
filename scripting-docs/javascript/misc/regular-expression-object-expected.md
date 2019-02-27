---
title: Previsto oggetto Regular expression | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5016
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: e226096c-c58f-4bcb-a71e-fa32ce474b67
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2b27c90a0c2461d500f618fbf7acede4d6942781
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/26/2019
ms.locfileid: "56840672"
---
# <a name="regular-expression-object-expected"></a>Previsto un oggetto di espressione regolare
Si è provato a richiamare il **RegExp.prototype.toString** oppure **RegExp.prototype.valueOf** metodo in un oggetto di un tipo diverso da `RegExp`. L'oggetto di questo tipo di chiamata deve essere di tipo `RegExp`.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Richiamare solo le **RegExp.prototype.toString** oppure **RegExp.prototype.valueOf** metodi su oggetti di tipo `RegExp`.  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto di espressione regolare](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintassi di espressione regolare (JavaScript)](https://msdn.microsoft.com/library/1400241x)