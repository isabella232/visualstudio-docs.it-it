---
title: Completamento delle istruzioni per gli identificatori | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IntelliSense [JavaScript], statement completion
- statement completion, JavaScript IntelliSense
ms.assetid: c2cd4945-c67e-471b-8057-96cfd25f7fb2
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f0f990526bc142b9951ab095e4bbf26636c94e30
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49241270"
---
# <a name="statement-completion-for-identifiers"></a>Completamento delle istruzioni per gli identificativi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

JavaScript non consente esplicita tipizzazione per dichiarazioni di variabili. Di conseguenza, IntelliSense non può sempre fornire elenchi di completamento per gli oggetti. Ciò può verificarsi in varie situazioni. Di seguito sono alcune più comuni.  
  
-   Viene dichiarato un parametro, ma non è stato chiamato in un' posizione nel documento attivo, come illustrato nell'esempio seguente.  
  
    ```javascript  
    function illuminate(light) {  
             light.  // Accurate statement completion is not available   
                     // unless illuminate is called elsewhere with a   
                     // parameter that has a value. If it is called only  
                     // in a function that is a sibling to   
                     // illuminate(light) in the call hierarchy, the   
                     // IntelliSense engine also cannot determine the   
                     // parameter type.  
         }  
  
    // Sibling function. No statement completion for light   
    // object in preceding code.  
    function lightLamp() {  
        var x = illuminate(1);  
    }  
  
    // Uncomment the next line to obtain statement completion for  
    // light object in preceding code.  
    // var x = illuminate(1);  
    ```  
  
-   Un oggetto è una funzione che viene chiamata in risposta a un evento. In fase di progettazione, il motore di IntelliSense non è possibile determinare il tipo degli oggetti utilizzati in questa situazione.  
  
     Se il motore di IntelliSense può determinare che l'evento deve essere chiamato, in genere tramite l'utilizzo di `addEventListener` per l'evento nel documento attivo, vengono fornite informazioni di IntelliSense più accurate.  
  
 Se IntelliSense non riesce a identificare un oggetto, il motore di IntelliSense consente di popolare l'elenco di completamento con le entità denominate, o gli identificatori che sono presenti nel documento attivo. Quando l'elenco di completamento contiene questi identificatori, vengono visualizzate le icone di informazioni accanto a essi. Inoltre, una descrizione comando per ogni identificatore indica che l'espressione è sconosciuto. Di seguito vengono illustrati le opzioni di completamento per un oggetto di tipo istruzione `light` che non è possibile identificare perché l'oggetto e le relative proprietà sono definite. Tuttavia, il `intensity` proprietà è disponibile nell'elenco di identificatore perché è stato usato nel `illuminate` (funzione).  
  
 **Opzioni di completamento di un oggetto che non può essere identificato**  
  
 ![JavaScript IntelliSense per identificatori](../ide/media/js-intellisense-identifiers.png "js_intellisense_identifiers")  
  
 È possibile sostituire l'elenco di completamento di un oggetto usando i commenti della documentazione XML o funzionalità di estensibilità JavaScript IntelliSense. Usando queste funzionalità, è possibile fornire le informazioni sul tipo e le informazioni di IntelliSense più descrittive quando che altrimenti non sarebbero disponibile. Per altre informazioni, vedere [estensione di IntelliSense per JavaScript](../ide/extending-javascript-intellisense.md) e [creare commenti in formato documentazione XML](../ide/create-xml-documentation-comments-for-javascript-intellisense.md).  
  
## <a name="see-also"></a>Vedere anche  
 [IntelliSense per JavaScript](../ide/javascript-intellisense.md)



