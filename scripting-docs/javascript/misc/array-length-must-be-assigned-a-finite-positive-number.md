---
title: Alla lunghezza della matrice deve essere assegnato un numero positivo finito | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: c51c66a4-a543-4e95-b18d-2cfbcb3d1fdd
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8e0016c7a0a6acb3f08121d8636ccdf848dcf201
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862809"
---
# <a name="array-length-must-be-assigned-a-finite-positive-number"></a>Alla lunghezza della matrice deve essere assegnato un numero positivo finito
Quando si imposta la proprietà **length** di un oggetto **Array** esistente, è stata specificata una lunghezza della matrice che non è un numero positivo o zero. Questo errore si verifica quando si assegna un valore alla proprietà **length** di un `Array` oggetto negativo o non numerico ( `NaN` ). Si noti che [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] converte automaticamente i numeri frazionari in interi interi.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Assegnare un numero intero positivo alla proprietà Length. Non esiste un limite massimo per la dimensione di una matrice, ad eccezione del valore intero massimo (approssimativamente 4 miliardi). Nell'esempio seguente viene illustrato il modo corretto per impostare la proprietà **length** di un oggetto **Array** .  
  
    ```JavaScript  
    var my_array = new Array();  
    my_array.length = 99;  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo di matrici](https://developer.mozilla.org/docs/Learn/JavaScript/First_steps/Arrays)