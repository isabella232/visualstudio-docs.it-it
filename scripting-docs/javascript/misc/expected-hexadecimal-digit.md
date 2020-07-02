---
title: Prevista cifra esadecimale | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 67a86df7-49f9-43cb-99c6-99b1a427827a
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c0797d44115fb5b44cb0c670153e8476356bd533
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85816566"
---
# <a name="expected-hexadecimal-digit"></a>Prevista cifra esadecimale
È stata creata una sequenza di escape Unicode non corretta. Le sequenze di escape Unicode iniziano con \u, seguite esattamente da quattro cifre esadecimali (non più e non meno). Le cifre esadecimali Unicode possono contenere solo i numeri 0-9, lettere maiuscole A-F e lettere minuscole a-f. Nell'esempio seguente viene illustrata una sequenza di escape Unicode correttamente formata.  
  
```JavaScript  
z = "\u1A5F";  
```  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Assicurarsi che le cifre esadecimali Unicode inizino con \u, che contenga solo i numeri 0-9, lettere maiuscole A-F, lettere minuscole a-f; e sono raggruppati in quattro cifre.  
  
    > [!NOTE]
    > Se si vuole usare il testo letterale \u in una stringa, usare due barre rovesciate ( \\ \u), una per l'escape della prima barra rovesciata.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi di dati](../../javascript/data-types-javascript.md)