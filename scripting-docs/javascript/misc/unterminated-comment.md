---
title: Commento senza terminazione | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 16f675cb62c0c3fd5f3aba7ba6190427fe101353
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85814803"
---
# <a name="unterminated-comment"></a>Commento senza terminazione
È stato avviato un blocco di commento a più righe, ma non è stato terminato correttamente. I commenti a più righe iniziano con una combinazione "/*" e terminano con la \* combinazione "/" inversa. Di seguito è riportato un esempio:  
  
```JavaScript  
/* This is a comment  
This is another part of the same comment.*/  
```  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Assicurarsi di terminare i commenti a più righe con "*/".  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzioni per commenti](../../javascript/reference/comment-statements-javascript.md)