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
ms.openlocfilehash: 31226f972ff4714dd81207cf27d862d3449184a5
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/26/2019
ms.locfileid: "56840763"
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>La funzione non ha un oggetto Prototype valido
Si è provato a usare **instanceof** per determinare se un oggetto derivato da una classe particolare funzione, ma è stata ridefinita dell'oggetto `prototype` proprietà come `null`, o un tipo di oggetto esterno (entrambi neplatné [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] oggetti). Un oggetto esterno può essere un oggetto dal modello a oggetti host (ad esempio, il documento di Internet Explorer o oggetto window) o un oggetto COM esterno.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Verificare che la funzione `prototype` proprietà fa riferimento a un valore valido [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] oggetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto funzione](../../javascript/reference/function-object-javascript.md)   
 [Proprietà prototype (Object)](../../javascript/reference/prototype-property-object-javascript.md)