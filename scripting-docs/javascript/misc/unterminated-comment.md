---
title: Non ha terminazione commento | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1016
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d4286315-814b-4966-b4c4-1ee19d796eff
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f2b21c585bb48b55929a78554d686477e0fa5649
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/26/2019
ms.locfileid: "56842442"
---
# <a name="unterminated-comment"></a>Commento senza terminazione
Si è iniziato un blocco di commento su più righe, ma non lo è stato correttamente terminato. I commenti su più righe iniziano con un "/ *" combinazione e terminano con l'operazione inversa "\*/" combinazione. Di seguito è riportato un esempio:  
  
```JavaScript  
/* This is a comment  
This is another part of the same comment.*/  
```  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Assicurarsi di terminare i commenti su più righe con "* /".  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzioni per commenti](../../javascript/reference/comment-statements-javascript.md)