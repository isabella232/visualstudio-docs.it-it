---
title: "'default' può apparire solo una volta in un'istruzione 'switch' | Microsoft Docs"
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
- VS.WebClient.Help.SCRIPT1027
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a94100f4-6ee5-4759-b635-9d309e47111e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a4f254825e27793999932b772ac4bc2512908fae
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347307"
---
# <a name="default-can-only-appear-once-in-a-switch-statement"></a>'default' può apparire una sola volta in un'istruzione 'switch'
Si è provato a usare il **predefinito** istruzione più volte all'interno di un'istruzione switch. Nel caso predefinito è sempre l'ultima istruzione case in un'istruzione switch (è il caso di FallThrough).  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Rimuovere qualsiasi elemento aggiuntivo **predefinito** caso le istruzioni dal `switch` istruzione (usare la maggior parte delle istruzione case a un valore predefinito nell'istruzione switch).  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzione switch](../../javascript/reference/switch-statement-javascript.md)   
 [Controllo del flusso di programma](../../javascript/controlling-program-flow-javascript.md)   
 [Parole riservate in JavaScript](../../javascript/reference/javascript-reserved-words.md)