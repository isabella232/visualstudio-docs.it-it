---
title: Prevista cifra esadecimale | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 82f020b5f3b82ab2ce3545102be83a5cd41c6069
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446519"
---
# <a name="expected-hexadecimal-digit"></a>Prevista cifra esadecimale
È stata creata una sequenza di escape Unicode non corretta. Le sequenze di escape Unicode iniziano con \u, seguita da quattro cifre esadecimali (non più e non meno). Cifre esadecimali Unicode possono contenere solo i numeri da 0 a 9, le lettere maiuscole lettere A-F e lettere minuscole lettere a-f. L'esempio seguente illustra una sequenza di escape Unicode in formato corretto.  
  
```JavaScript  
z = "\u1A5F";  
```  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Verificare che le cifre esadecimali Unicode iniziano con \u, contiene solo i numeri 0-9, le lettere maiuscole lettere A-F, lettere minuscole lettere a-f; e vengono raggruppati in quattro cifre.  
  
    > [!NOTE]
    > Se si desidera utilizzare \u il testo letterale in una stringa, quindi utilizzare due barre rovesciate - (\\\u)-uno per la prima barra rovesciata di escape.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi di dati](../../javascript/data-types-javascript.md)