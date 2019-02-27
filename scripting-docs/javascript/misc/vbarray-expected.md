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
ms.openlocfilehash: 159a5dd0195cc0cbb244664d75e19d1ac6af3dec
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/26/2019
ms.locfileid: "56843416"
---
# <a name="vbarray-expected"></a>Previsto VBArray
È fornito un oggetto che non era un safeArray di Visual Basic, quando ne è previsto.  
  
```js
new VBArray(safeArray);  
```  
  
 Gli oggetti VBArray sono di sola lettura e non possono essere creati direttamente. L'argomento di safeArray è un valore VBArray e deve aver ottenuto un valore VBArray prima di essere passato al `VBArray` costruttore. Ciò può essere ottenuto solo recuperando il valore da un oggetto ActiveX o altro esistente.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Verificare di passare solo **VBArray** gli oggetti per il **VBArray** costruttore.  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto VBArray](../../javascript/reference/vbarray-object-javascript.md)   
 [Uso delle matrici](../../javascript/advanced/using-arrays-javascript.md)