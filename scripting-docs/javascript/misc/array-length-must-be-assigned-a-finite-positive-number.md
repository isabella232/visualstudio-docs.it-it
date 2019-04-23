---
title: La lunghezza della matrice deve essere assegnata un numero positivo finito | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 39f2720efbcd8defffb9d0c77047a50e57939e95
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60082347"
---
# <a name="array-length-must-be-assigned-a-finite-positive-number"></a>Alla lunghezza della matrice deve essere assegnato un numero positivo finito
Quando si impostano i **lunghezza** proprietà di un oggetto esistente **matrice** oggetto, è specificata una lunghezza della matrice non è un numero positivo o zero. Questo errore si verifica quando si assegna un valore per il **lunghezza** proprietà di un `Array` oggetto che è negativo o non è un numero (`NaN`). Si noti che [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] converte automaticamente i numeri frazionari in interi.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Assegnare un numero intero positivo per la proprietà length. Non vi è alcun limite massimo per le dimensioni di una matrice, diverso dal valore massimo numero intero (circa 4 miliardi). L'esempio seguente illustra il modo corretto per impostare il **lunghezza** proprietà di un **matrice** oggetto.  
  
    ```JavaScript  
    var my_array = new Array();  
    my_array.length = 99;  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Uso delle matrici](../../javascript/advanced/using-arrays-javascript.md)