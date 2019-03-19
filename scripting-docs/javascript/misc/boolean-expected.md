---
title: Previsto Boolean | Microsoft Docs
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
ms.openlocfilehash: 261cf0ad93208c0eac09e42dcd68853352318e88
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58149156"
---
# <a name="boolean-expected"></a>Previsto Boolean
Si è provato a richiamare il **Boolean.prototype.toString** oppure **Boolean.prototype.valueOf** metodo in un oggetto di un tipo diverso da `Boolean`. L'oggetto di questo tipo di chiamata deve essere di tipo `Boolean`. Ad esempio:

```JavaScript
var o = new Object;
o.f = Boolean.prototype.toString;
o.f();
```

## <a name="to-correct-this-error"></a>Per correggere l'errore

- Richiamare solo le **Boolean.prototype.toString** oppure **Boolean.prototype.valueOf** metodi su oggetti di tipo **booleano.**

## <a name="see-also"></a>Vedere anche

- [Oggetto Boolean](../../javascript/reference/boolean-object-javascript.md)
- [Tipi di dati](../../javascript/data-types-javascript.md)
- [Controllo del flusso di programma](../../javascript/controlling-program-flow-javascript.md)
- [Copia, passaggio e confronto di dati](../../javascript/advanced/copying-passing-and-comparing-data-javascript.md)