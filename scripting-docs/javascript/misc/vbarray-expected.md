---
title: Previsto VBArray | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5013
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f2998d7d-13a4-4bbe-b872-3ff3316551e4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4b4e6521e5d363c21311b19e2ecc1679981acac3
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862698"
---
# <a name="vbarray-expected"></a>Previsto VBArray
È stato fornito un oggetto che non era un Visual Basic safeArray, quando ne era previsto uno.  
  
```js
new VBArray(safeArray);  
```  
  
 Gli oggetti VBArray sono di sola lettura e non possono essere creati direttamente. L'argomento safeArray è un valore VBArray e deve avere ottenuto un valore VBArray prima di essere passato al `VBArray` costruttore. Ciò può essere ottenuto solo recuperando il valore da un oggetto ActiveX o altro esistente.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Assicurarsi di passare solo gli oggetti **VBArray** al costruttore **VBArray** .  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto VBArray](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/VBArray)   
 [Utilizzo di matrici](https://developer.mozilla.org/docs/Learn/JavaScript/First_steps/Arrays)