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
ms.openlocfilehash: 2c2507acd42336511dadc3dedd2eba15fe0d5b76
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60050075"
---
# <a name="expected-hexadecimal-digit"></a>Prevista cifra esadecimale
È stata creata una sequenza di escape Unicode non corretta. Le sequenze di escape Unicode iniziano con \u, seguita da quattro cifre esadecimali (non più e non meno). Cifre esadecimali Unicode possono contenere solo i numeri da 0 a 9, le lettere maiuscole lettere A-F e lettere minuscole lettere a-f. L'esempio seguente illustra una sequenza di escape Unicode in formato corretto.  
  
```JavaScript  
z = "\u1A5F";  
```  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Verificare che le cifre esadecimali Unicode iniziano con \u, contiene solo i numeri 0-9, le lettere maiuscole lettere A-F, lettere minuscole lettere a-f; e vengono raggruppati in quattro cifre.  
  
    > [!NOTE]
    >  Se si desidera utilizzare \u il testo letterale in una stringa, quindi utilizzare due barre rovesciate - (\\\u)-uno per la prima barra rovesciata di escape.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi di dati](../../javascript/data-types-javascript.md)