---
description: Si è provato a usare la parola chiave break all'esterno di un ciclo.
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
ms.openlocfilehash: d761a1cff89f650e5fc465b6a6aef2713aafb765
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2021
ms.locfileid: "103570648"
---
# <a name="cant-have-break-outside-of-loop"></a>Impossibile utilizzare 'break' all'esterno di un ciclo
Si è provato a usare la parola chiave **break** all'esterno di un ciclo. La parola chiave **break** viene utilizzata per terminare un ciclo o un' `switch` istruzione. Deve essere incorporato nel corpo di un ciclo o di un' `switch` istruzione. Tuttavia, un' **etichetta** può seguire la parola chiave Break.  
  
```js
break labelname;  
```  
  
 È necessario solo il formato con etichetta della parola chiave **break** quando si utilizzano le istruzioni o i cicli annidati `switch` ed è necessario suddividere un ciclo che non è quello più interno.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Verificare che la parola chiave **break** venga visualizzata all'interno di un ciclo di inclusione o di un'istruzione switch.  
  
## <a name="see-also"></a>Vedi anche  
 [Break (istruzione)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/break)   
 [Controllo del flusso di programma](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)   
 [Risoluzione dei problemi relativi agli script](https://developer.mozilla.org/docs/Learn/JavaScript/First_steps/What_went_wrong)
