---
title: Completamento istruzioni per gli identificatori | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [JavaScript], statement completion
- statement completion, JavaScript IntelliSense
ms.assetid: c2cd4945-c67e-471b-8057-96cfd25f7fb2
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f5e52bf174e5a41d79fa23bfca39121db668e40e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72643863"
---
# <a name="statement-completion-for-identifiers"></a>Completamento delle istruzioni per gli identificativi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

JavaScript non consente la tipizzazione esplicita per le dichiarazioni di variabili. Di conseguenza, IntelliSense non è sempre in grado di fornire elenchi di completamento per gli oggetti. Questa situazione può verificarsi in varie situazioni. Di seguito sono riportate alcune delle opzioni più comuni.

- Un parametro è dichiarato, ma non è stato chiamato altrove nel documento attivo, come illustrato nell'esempio seguente.

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

- Un oggetto si trova in una funzione che viene chiamata in risposta a un evento. In fase di progettazione, il motore IntelliSense non è in grado di determinare il tipo di oggetti utilizzati in questa situazione.

   Se il motore IntelliSense è in grado di determinare che l'evento deve essere chiamato, in genere tramite l'utilizzo di `addEventListener` per l'evento nel documento attivo, vengono fornite informazioni di IntelliSense più accurate.

  Quando IntelliSense non è in grado di identificare un oggetto, il motore di IntelliSense compila l'elenco di completamento con le entità denominate o gli identificatori presenti nel documento attivo. Quando l'elenco di completamento contiene questi identificatori, le icone delle informazioni vengono visualizzate accanto. Inoltre, una descrizione comando per ogni identificatore indica che l'espressione è sconosciuta. Nella figura seguente sono illustrate le opzioni di completamento delle istruzioni per un oggetto di tipo `light` che non è possibile identificare perché l'oggetto e le relative proprietà non sono definiti. Tuttavia, la `intensity` proprietà è disponibile nell'elenco di identificatori perché è stata usata nella `illuminate` funzione.

  **Opzioni di completamento per un oggetto che non è possibile identificare**

  ![JavaScript IntelliSense per identificatori](../ide/media/js-intellisense-identifiers.png "js_intellisense_identifiers")

  È possibile eseguire l'override dell'elenco di completamento per un oggetto usando i commenti della documentazione XML o le funzionalità di estensibilità IntelliSense per JavaScript. Utilizzando queste funzionalità, è possibile fornire informazioni sul tipo e informazioni IntelliSense più descrittive quando potrebbero non essere disponibili in altro modo. Per ulteriori informazioni, vedere [estensione di JavaScript IntelliSense](../ide/extending-javascript-intellisense.md) e [creazione di commenti alla documentazione XML](../ide/create-xml-documentation-comments-for-javascript-intellisense.md).

## <a name="see-also"></a>Vedere anche
 [IntelliSense per JavaScript](../ide/javascript-intellisense.md)
