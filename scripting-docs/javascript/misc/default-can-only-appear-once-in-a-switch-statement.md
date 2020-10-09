---
title: "' default ' può essere presente una sola volta in un'istruzione ' switch ' | Microsoft Docs"
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1027
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a94100f4-6ee5-4759-b635-9d309e47111e
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b49b5cfe7076a4a9504500a63f4d47d2f54bcc1a
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862792"
---
# <a name="default-can-only-appear-once-in-a-switch-statement"></a>'default' può apparire una sola volta in un'istruzione 'switch'
Si è provato a usare l'istruzione **predefinita** più di una volta all'interno di un'istruzione switch. Il case predefinito è sempre l'ultima istruzione case in un'istruzione switch, ovvero il caso.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Rimuovere tutte le istruzioni case **predefinite** aggiuntive dall' `switch` istruzione (usare al massimo un'istruzione case predefinita nell'istruzione switch).  
  
## <a name="see-also"></a>Vedere anche  
 [Switch (istruzione)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/switch)   
 [Controllo del flusso di programma](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)   
 [Parole riservate in JavaScript](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Lexical_grammar)