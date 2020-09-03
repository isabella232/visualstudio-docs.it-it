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
ms.openlocfilehash: 4dbb7e55f6afe6d3edfe4e98749807732ffa05ac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817671"
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

- [Oggetto Boolean](../../javascript/reference/boolean-object-javascript.md)
- [Tipi di dati](../../javascript/data-types-javascript.md)
- [Controllo del flusso di programma](../../javascript/controlling-program-flow-javascript.md)
- [Copia, passaggio e confronto di dati](../../javascript/advanced/copying-passing-and-comparing-data-javascript.md)