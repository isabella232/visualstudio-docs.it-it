---
title: L'URI da decodificare non è un valido codifica | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5025
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 029e0790-ffd1-496d-8700-3b3dbac1b6fd
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8fd8add72d016bc3f2e815f41c29c735505c8817
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60108425"
---
# <a name="the-uri-to-be-decoded-is-not-a-valid-encoding"></a>La codifica usata per l'URI da decodificare non è valida
Si è provato a decodificare un formato non corretto URI (Uniform Resource Identifier). Gli URI hanno una sintassi speciale. la maggior parte dei caratteri non alfanumerici devono essere codificati prima di poter essere utilizzate in un URI. È possibile usare la `encodeURI` e `encodeURIComponent` metodi per creare un URI da un normale [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] stringa.  
  
 Un URI completo è costituito da una sequenza di componenti e i separatori. Il formato generale è:  
  
```JavaScript  
<Scheme>:<first>/<second>;<third>?<fourth>  
```  
  
 I nomi delle parentesi acute rappresentano i componenti e il ":", "/", ";" e "?" sono caratteri riservati utilizzati come separatori.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Verificare che si sta tentando di decodificare solo URI validi. Impossibile decodificare normale [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] stringhe, poiché potrebbero contenere caratteri non validi.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione decodeURI](../../javascript/reference/decodeuri-function-javascript.md)   
 [Funzione DecodeURIComponent](../../javascript/reference/decodeuricomponent-function-javascript.md)