---
title: Limitazioni del debug degli Script | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ASPX breakpoint mapping, limitations
- script debugging, limitations
- breakpoint mapping, limitations
ms.assetid: 280eead5-693c-47af-967f-dfe9d23f84db
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c51bb5edf5a139d2d19350c6a7a83c0ad3277ce4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58969555"
---
# <a name="limitations-on-script-debugging"></a>Limitazioni del debug di script
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] supporta il debug di script lato client, soggetto alle limitazioni trattate in questo argomento.  
  
## <a name="limitations-on-breakpoint-mapping-with-client-side-script"></a>Limitazioni sul mapping dei punti di interruzione con script lato client  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] consente di impostare un punto di interruzione in un file HTML o ASPX lato server trasformato in un file lato client in fase di esecuzione. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] esegue il mapping del punto di interruzione dal file lato server a un punto di interruzione corrispondente nel file lato client, soggetto alle seguenti limitazioni:  
  
-   I punti di interruzione devono essere impostati all'interno di blocchi `<script>`. Non è possibile eseguire il mapping di punti di interruzione in script inline o blocchi `<% %>`.  
  
-   L'URL del browser per la pagina deve contenere il nome della pagina. Ad esempio http://microsoft.com/default.apsx. I punti di interruzione in grado di riconoscere un reindirizzamento da un indirizzo, ad esempio http://microsoft.com alla pagina predefinita.  
  
-   Il punto di interruzione deve essere impostato nella pagina specificata nell'URL del browser, non in un file di controllo (ascx) ASPX, in una pagina master o in un altro file incluso dalla pagina. Non è possibile eseguire il mapping dei punti di interruzione impostati nelle pagine incluse.  
  
-   Non è possibile eseguire il mapping dei punti di interruzione impostati nei blocchi `<script defer=true>`.  
  
-   Per i punti di interruzione impostati nei blocchi `<script id="">`, l'attributo `id` viene ignorato dal mapping dei punti di interruzione.  
  
## <a name="breakpoint-mapping-and-duplicate-lines"></a>Mapping dei punti di interruzione e righe duplicate  
 Per trovare la posizione corrispondente negli script lato server e lato client, l'algoritmo di mapping dei punti di interruzione esamina il codice su ogni riga. L'algoritmo presuppone che ogni riga sia univoca. Se due o più righe contengono lo stesso codice e si imposta un punto di interruzione su una delle righe duplicate, l'algoritmo di mapping dei punti di interruzione potrebbe selezionare il duplicato errato nel file lato client. Per evitare questo problema, aggiungere un commento alla riga in cui è stato impostato il punto di interruzione. Ad esempio:  
  
```  
i++ ;  
i ++; // I added a comment, so this line is now unique  
i ++;  
```
