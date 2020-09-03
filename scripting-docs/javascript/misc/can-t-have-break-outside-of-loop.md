---
title: Non è possibile avere ' Break ' all'esterno del ciclo | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 11d02172-2a78-4705-a730-d21111db5f42
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0959bad452d3b24ca1475b66e37fbdab1e9c3e7f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817658"
---
# <a name="cant-have-break-outside-of-loop"></a>Impossibile utilizzare 'break' all'esterno di un ciclo
Si è provato a usare la parola chiave **break** all'esterno di un ciclo. La parola chiave **break** viene utilizzata per terminare un ciclo o un' `switch` istruzione. Deve essere incorporato nel corpo di un ciclo o di un' `switch` istruzione. Tuttavia, un' **etichetta** può seguire la parola chiave Break.  
  
```js
break labelname;  
```  
  
 È necessario solo il formato con etichetta della parola chiave **break** quando si utilizzano le istruzioni o i cicli annidati `switch` ed è necessario suddividere un ciclo che non è quello più interno.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Verificare che la parola chiave **break** venga visualizzata all'interno di un ciclo di inclusione o di un'istruzione switch.  
  
## <a name="see-also"></a>Vedere anche  
 [Break (istruzione)](../../javascript/reference/break-statement-javascript.md)   
 [Controllo del flusso di programma](../../javascript/controlling-program-flow-javascript.md)   
 [Risoluzione dei problemi relativi agli script](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)