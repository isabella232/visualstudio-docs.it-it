---
title: Previsto VBArray | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 467a6ec6ca45f2ea0411e0266163ca23a9e3d594
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572501"
---
# <a name="vbarray-expected"></a>Previsto VBArray
È stato fornito un oggetto che non era un Visual Basic safeArray, quando ne era previsto uno.  
  
```js
new VBArray(safeArray);  
```  
  
 Gli oggetti VBArray sono di sola lettura e non possono essere creati direttamente. L'argomento safeArray è un valore VBArray e deve avere ottenuto un valore VBArray prima di essere passato al costruttore `VBArray`. Ciò può essere ottenuto solo recuperando il valore da un oggetto ActiveX o altro esistente.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Assicurarsi di passare solo gli oggetti **VBArray** al costruttore **VBArray** .  
  
## <a name="see-also"></a>Vedere anche  
 @No__t_1 [oggetto VBArray](../../javascript/reference/vbarray-object-javascript.md)  
 [Uso delle matrici](../../javascript/advanced/using-arrays-javascript.md)