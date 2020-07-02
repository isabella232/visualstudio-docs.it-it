---
title: L'URI da codificare contiene un carattere non valido | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5024
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a3f0fdbb-8d4b-41ae-a396-43dfc9483760
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e6091968dcbdd98240b1705e0fa7dc855dad3bda
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85816072"
---
# <a name="the-uri-to-be-encoded-contains-an-invalid-character"></a>L'URI da codificare contiene un carattere non valido
Si è provato a codificare una stringa come URI (Uniform Resource Identifier), ma sono contenuti caratteri non validi. Anche se la maggior parte dei caratteri è valida all'interno di stringhe da convertire in URI, alcune sequenze di caratteri Unicode non sono valide.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Verificare che la stringa da codificare contenga solo sequenze Unicode valide. Un URI completo è costituito da una sequenza di componenti e separatori. I nomi racchiusi tra parentesi acute rappresentano i componenti e gli elementi ":", "/", ";" e "?" sono caratteri riservati utilizzati come separatori. Il modulo generale è:  
  
    ```JavaScript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [encodeURI (funzione)](../../javascript/reference/encodeuri-function-javascript.md)   
 [Funzione encodeURIComponent](../../javascript/reference/encodeuricomponent-function-javascript.md)