---
title: Previsto oggetto Regular Expression | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 370e5a8028bae0e60c265ba65dca12668e4b8d8c
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862054"
---
# <a name="regular-expression-object-expected"></a>Previsto un oggetto di espressione regolare
Si è provato a richiamare il metodo **RegExp. Prototype. ToString** o **RegExp. Prototype. valueOf** su un oggetto di un tipo diverso da `RegExp` . L'oggetto di questo tipo di chiamata deve essere di tipo `RegExp` .  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Richiamare solo i metodi **RegExp. Prototype. ToString** o **RegExp. Prototype. valueOf** su oggetti di tipo `RegExp` .  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Regular Expression](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/RegExp)   
 [Sintassi delle espressioni regolari (JavaScript)](/previous-versions/1400241x(v=vs.100))