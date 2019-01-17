---
title: Previsto Boolean | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5010
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 35d71b7f-53fd-44c4-a7c7-b1550c65cfd4
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cb8ec8f7244b98cfa628794b485859dbec611c19
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347931"
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