---
title: Funzione è privo di un oggetto prototype valido | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b9e34652-190f-4b57-b253-df2e8c4d09c6
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a4e2cbf198a452cd61f1355682ea3041436d2a27
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346696"
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>La funzione non ha un oggetto Prototype valido
Si è provato a usare **instanceof** per determinare se un oggetto derivato da una classe particolare funzione, ma è stata ridefinita dell'oggetto `prototype` proprietà come `null`, o un tipo di oggetto esterno (entrambi neplatné [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] oggetti). Un oggetto esterno può essere un oggetto dal modello a oggetti host (ad esempio, il documento di Internet Explorer o oggetto window) o un oggetto COM esterno.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Verificare che la funzione `prototype` proprietà fa riferimento a un valore valido [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] oggetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto funzione](../../javascript/reference/function-object-javascript.md)   
 [Proprietà prototype (Object)](../../javascript/reference/prototype-property-object-javascript.md)