---
title: Previsto VBArray | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5013
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f2998d7d-13a4-4bbe-b872-3ff3316551e4
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a4b5416c6e37e59a60206bd21606b5214f05a269
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347463"
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