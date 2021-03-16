---
description: È stato fornito un oggetto che non era un Visual Basic safeArray, quando ne era previsto uno.
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
ms.openlocfilehash: e344e24b3fbef7b7f119a36513c222e085328072
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2021
ms.locfileid: "103572078"
---
# <a name="vbarray-expected"></a>Previsto VBArray
È stato fornito un oggetto che non era un Visual Basic safeArray, quando ne era previsto uno.  
  
```js
new VBArray(safeArray);  
```  
  
 Gli oggetti VBArray sono di sola lettura e non possono essere creati direttamente. L'argomento safeArray è un valore VBArray e deve avere ottenuto un valore VBArray prima di essere passato al `VBArray` costruttore. Ciò può essere ottenuto solo recuperando il valore da un oggetto ActiveX o altro esistente.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Assicurarsi di passare solo gli oggetti **VBArray** al costruttore **VBArray** .  
  
## <a name="see-also"></a>Vedi anche  
 [Oggetto VBArray](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/VBArray)   
 [Utilizzo di matrici](https://developer.mozilla.org/docs/Learn/JavaScript/First_steps/Arrays)
