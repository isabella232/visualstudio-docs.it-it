---
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
ms.openlocfilehash: 98d2ee08a52e86c435c58502da1ab4f68b594905
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85816163"
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
  
## <a name="see-also"></a>Vedere anche  
 [decodeURI (funzione)](../../javascript/reference/decodeuri-function-javascript.md)   
 [Funzione DecodeURIComponent](../../javascript/reference/decodeuricomponent-function-javascript.md)