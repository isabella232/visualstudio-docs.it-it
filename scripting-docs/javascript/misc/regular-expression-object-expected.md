---
title: Previsto oggetto Regular expression | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5016
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: e226096c-c58f-4bcb-a71e-fa32ce474b67
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1b8e3c48b116680fe73d4cc318038cb2c13c4164
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346111"
---
# <a name="regular-expression-object-expected"></a>Previsto un oggetto di espressione regolare
Si è provato a richiamare il **RegExp.prototype.toString** oppure **RegExp.prototype.valueOf** metodo in un oggetto di un tipo diverso da `RegExp`. L'oggetto di questo tipo di chiamata deve essere di tipo `RegExp`.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Richiamare solo le **RegExp.prototype.toString** oppure **RegExp.prototype.valueOf** metodi su oggetti di tipo `RegExp`.  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto di espressione regolare](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintassi di espressione regolare (JavaScript)](https://msdn.microsoft.com/library/1400241x)