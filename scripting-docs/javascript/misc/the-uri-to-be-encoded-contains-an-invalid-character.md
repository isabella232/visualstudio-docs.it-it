---
title: L'URI da codificare contiene un carattere non valido | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: f2f9111acf656bf882a3d506fe95b8361f3693ff
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63006208"
---
# <a name="the-uri-to-be-encoded-contains-an-invalid-character"></a>L'URI da codificare contiene un carattere non valido
Si è tentato di codificare una stringa come un URI (Uniform Resource Identifier), ma contiene caratteri non validi. Sebbene la maggior parte dei caratteri sono validi all'interno delle stringhe da convertire in URI, alcune sequenze di caratteri Unicode non sono valide.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Verificare che la stringa da codificare contiene solo le sequenze di Unicode valide. Un URI completo è costituito da una sequenza di componenti e i separatori. I nomi delle parentesi acute rappresentano i componenti e il ":", "/", ";" e "?" sono caratteri riservati utilizzati come separatori. Il formato generale è:  
  
    ```JavaScript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione encodeURI](../../javascript/reference/encodeuri-function-javascript.md)   
 [Funzione encodeURIComponent](../../javascript/reference/encodeuricomponent-function-javascript.md)