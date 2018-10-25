---
title: Possono&#39;ha &#39;break&#39; all'esterno del ciclo | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT1019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 11d02172-2a78-4705-a730-d21111db5f42
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb23f1bc3de087515cad9ba4910cf2ebaf640353
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49928555"
---
# <a name="can39t-have-39break39-outside-of-loop"></a>Possono&#39;ha &#39;break&#39; all'esterno del ciclo
Si è provato a usare il **interruzione** (parola chiave) all'esterno di un ciclo. Il **INTERR** parola chiave viene usata per interrompere un ciclo o `switch` istruzione. Deve essere incorporato nel corpo di un ciclo o `switch` istruzione. Tuttavia, un **etichetta** possibile seguire la parola chiave break.  
  
```  
break labelname;  
```  
  
 È necessario solo il form con etichette del **break** parola chiave quando si utilizzano cicli annidati o `switch` istruzioni ed è necessario interrompere un ciclo che non corrisponde a quello più interno.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Assicurarsi che il **interruzione** (parola chiave) viene visualizzato all'interno di un'istruzione di ciclo o un commutatore di inclusione.  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzione break](../../javascript/reference/break-statement-javascript.md)   
 [Controllo del flusso di programma](../../javascript/controlling-program-flow-javascript.md)   
 [Risoluzione dei problemi relativi agli script](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)