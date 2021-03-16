---
description: Si è provato a usare instanceof per determinare se un oggetto è derivato da una classe di funzione particolare, ma è stata ridefinita la proprietà prototype dell'oggetto come null o un tipo di oggetto esterno (entrambi non oggetti JavaScript validi).
title: La funzione non ha un oggetto prototipo valido | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 0356ac9ef7c63c77c0cc0dfca623ff24d3de24af
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571415"
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>La funzione non ha un oggetto Prototype valido
Si è provato a usare **instanceof** per determinare se un oggetto è derivato da una classe di funzione particolare, ma è stata ridefinita la proprietà dell'oggetto `prototype` come `null` o un tipo di oggetto esterno (entrambi non [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] oggetti validi). Un oggetto esterno può essere un oggetto del modello a oggetti host, ad esempio il documento o l'oggetto finestra di Internet Explorer, oppure un oggetto COM esterno.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Verificare che la proprietà della funzione faccia `prototype` riferimento a un [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] oggetto valido.  
  
## <a name="see-also"></a>Vedi anche  
 [Oggetto Function](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function)   
 [Proprietà prototype (Object)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)
