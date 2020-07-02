---
title: Previsto oggetto | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5007
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 5d88c93d-e5b5-4b11-9bb5-bf1a5e41ccc3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 28eec125914f0207fbdf79a39ea2140dd74d6d0d
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85816228"
---
# <a name="object-expected"></a>Previsto oggetto
Si è tentato di richiamare un metodo o una proprietà in un oggetto di tipo diverso da `Object` oppure è stato passato un argomento di tipo diverso da `Object` quando era obbligatorio un `Object`.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Richiamare il metodo o la proprietà solo in oggetti di tipo `Object`.  
  
- Se l'errore si verifica per un argomento non oggetto, passare un oggetto di tipo `Object`.  
  
- Verificare se viene richiamato un riferimento non definito o Null invece di un oggetto di tipo `Object`.  
  
     Ad esempio, se si verifica questo errore su myVar nel codice seguente:  
  
    ```JavaScript  
    var str = myVar.toString();  
    ```  
  
     È possibile usare invece questo codice:  
  
    ```JavaScript  
    if (myVar) {  
        var str = myVar.toString();  
    }  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Object](../../javascript/reference/object-object-javascript.md)   
 [Oggetti e matrici](../../javascript/objects-and-arrays-javascript.md)