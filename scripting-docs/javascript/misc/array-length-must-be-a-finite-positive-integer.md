---
title: La lunghezza della matrice deve essere un numero intero positivo finito | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5029
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1a467040-4702-4178-848f-418a5974e907
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 69494f1485a97ff4f2c98cf2493e5d0bc5b8aa9f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576085"
---
# <a name="array-length-must-be-a-finite-positive-integer"></a>La lunghezza della matrice deve essere pari a un numero intero positivo finito
Si sta chiamando il costruttore di **matrice** con un argomento che non è un numero intero (i numeri interi sono costituiti da zero e dal set di numeri interi positivi).  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Usare numeri interi positivi solo quando si crea un nuovo oggetto `Array`. Se si vuole creare una matrice con un singolo elemento che non è un numero intero, eseguirla in un processo in due passaggi. Creare prima di tutto una matrice con un elemento, quindi inserire il valore nel primo elemento (array [0]). Di seguito è riportato un esempio che genera questo errore.  
  
    ```JavaScript  
    var piArray = new Array(3.14159);  
    ```  
  
     Nell'esempio seguente viene illustrato il modo corretto per specificare una matrice con un singolo elemento numerico.  
  
    ```JavaScript  
    var piArray = new Array(1);  
    piArray [0] = 3.14159;  
    ```  
  
     Non esiste un limite massimo per la dimensione di una matrice, ad eccezione del valore intero massimo (approssimativamente 4 miliardi).  
  
## <a name="see-also"></a>Vedere anche  
 [Uso delle matrici](../../javascript/advanced/using-arrays-javascript.md)