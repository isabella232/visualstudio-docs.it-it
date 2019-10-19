---
title: È previsto un valore booleano | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 91ff0ec8cbd6e5cedb5ec02a8c574ff137b1c6ad
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576050"
---
# <a name="boolean-expected"></a>Previsto Boolean
Si è provato a richiamare il metodo **Boolean. Prototype. ToString** o **Boolean. Prototype. valueOf** su un oggetto di un tipo diverso da `Boolean`. L'oggetto di questo tipo di chiamata deve essere di tipo `Boolean`. Esempio:

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