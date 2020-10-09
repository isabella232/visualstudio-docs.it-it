---
title: È previsto un valore booleano | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5010
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 35d71b7f-53fd-44c4-a7c7-b1550c65cfd4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b6d88815a33187e209bcba248d3c363afdd91227
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862655"
---
# <a name="boolean-expected"></a>Previsto Boolean
Si è provato a richiamare il metodo **Boolean. Prototype. ToString** o **Boolean. Prototype. valueOf** su un oggetto di un tipo diverso da `Boolean` . L'oggetto di questo tipo di chiamata deve essere di tipo `Boolean` . Ad esempio:

```JavaScript
var o = new Object;
o.f = Boolean.prototype.toString;
o.f();
```

## <a name="to-correct-this-error"></a>Per correggere l'errore

- Richiamare solo i metodi **Boolean. Prototype. ToString** o **Boolean. Prototype. valueOf** su oggetti di tipo **booleano.**

## <a name="see-also"></a>Vedere anche

- [Oggetto Boolean](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean)
- [Tipi di dati](https://developer.mozilla.org/docs/Web/JavaScript/Data_structures)
- [Controllo del flusso di programma](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)
- [Copia, passaggio e confronto di dati](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Functions)