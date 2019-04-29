---
title: Funzione è privo di un oggetto prototype valido | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b9e34652-190f-4b57-b253-df2e8c4d09c6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 413f73a53a6d4f698219139a87c449be4c155831
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63007503"
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>La funzione non ha un oggetto Prototype valido
Si è provato a usare **instanceof** per determinare se un oggetto derivato da una classe particolare funzione, ma è stata ridefinita dell'oggetto `prototype` proprietà come `null`, o un tipo di oggetto esterno (entrambi neplatné [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] oggetti). Un oggetto esterno può essere un oggetto dal modello a oggetti host (ad esempio, il documento di Internet Explorer o oggetto window) o un oggetto COM esterno.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Verificare che la funzione `prototype` proprietà fa riferimento a un valore valido [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] oggetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto funzione](../../javascript/reference/function-object-javascript.md)   
 [Proprietà prototype (Object)](../../javascript/reference/prototype-property-object-javascript.md)