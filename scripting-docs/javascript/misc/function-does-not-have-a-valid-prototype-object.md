---
title: La funzione non ha un oggetto prototipo valido | Microsoft Docs
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
ms.openlocfilehash: cb3cffa4bffd616560aa95ace4ad82a4368ebbd5
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574594"
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>La funzione non ha un oggetto Prototype valido
Si è provato a usare **instanceof** per determinare se un oggetto è derivato da una classe di funzione particolare, ma è stata ridefinita la proprietà `prototype` dell'oggetto come `null` o un tipo di oggetto esterno (entrambi non validi [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] oggetti). Un oggetto esterno può essere un oggetto del modello a oggetti host, ad esempio il documento o l'oggetto finestra di Internet Explorer, oppure un oggetto COM esterno.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Verificare che la proprietà `prototype` della funzione faccia riferimento a un oggetto [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] valido.  
  
## <a name="see-also"></a>Vedere anche  
 @No__t_1 [oggetto funzione](../../javascript/reference/function-object-javascript.md)  
 [Proprietà prototype (Object)](../../javascript/reference/prototype-property-object-javascript.md)