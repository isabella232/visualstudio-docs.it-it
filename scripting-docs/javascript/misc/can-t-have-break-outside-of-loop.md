---
title: Non è possibile avere ' Break ' all'esterno del ciclo | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 356e7022f940e696030b0cda4f71a599c147dd5a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576014"
---
# <a name="cant-have-break-outside-of-loop"></a>Impossibile utilizzare 'break' all'esterno di un ciclo
Si è provato a usare la parola chiave **break** all'esterno di un ciclo. La parola chiave **break** viene utilizzata per terminare un'istruzione loop o `switch`. Deve essere incorporato nel corpo di un'istruzione Loop o `switch`. Tuttavia, un' **etichetta** può seguire la parola chiave Break.  
  
```js
break labelname;  
```  
  
 È necessario solo il formato con etichetta della parola chiave **break** quando si usano i cicli annidati o le istruzioni `switch` ed è necessario uscire da un ciclo che non è quello più interno.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Verificare che la parola chiave **break** venga visualizzata all'interno di un ciclo di inclusione o di un'istruzione switch.  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzione break](../../javascript/reference/break-statement-javascript.md)   
 [Controllo del flusso di programma](../../javascript/controlling-program-flow-javascript.md)   
 [Risoluzione dei problemi relativi agli script](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)