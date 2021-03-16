---
description: Si è tentato di decodificare un URI formato in modo errato.
title: L'URI da decodificare non è una codifica valida | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: db9d2f89a193ca4542ff5d1ca5ed5c2ae6419f53
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571987"
---
# <a name="the-uri-to-be-decoded-is-not-a-valid-encoding"></a>La codifica usata per l'URI da decodificare non è valida
Si è tentato di decodificare un URI (Uniform Resource Identifier) formato in modo errato. Gli URI hanno una sintassi speciale. la maggior parte dei caratteri non alfanumerici deve essere codificata prima di poter essere usata in un URI. È possibile usare i `encodeURI` `encodeURIComponent` metodi e per creare un URI da una [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] stringa normale.  
  
 Un URI completo è costituito da una sequenza di componenti e separatori. Il modulo generale è:  
  
```JavaScript  
<Scheme>:<first>/<second>;<third>?<fourth>  
```  
  
 I nomi racchiusi tra parentesi acute rappresentano i componenti e gli elementi ":", "/", ";" e "?" sono caratteri riservati utilizzati come separatori.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Assicurarsi di provare a decodificare solo gli URI validi. Non è possibile decodificare [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] stringhe normali, perché possono contenere caratteri non validi.  
  
## <a name="see-also"></a>Vedi anche  
 [decodeURI (funzione)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/decodeuri)   
 [Funzione DecodeURIComponent](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/decodeuricomponent)
