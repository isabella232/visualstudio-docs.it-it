---
title: 'Procedura: visualizzare documenti Script | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Script Explorer
ms.assetid: 8b621e53-4508-4b4a-9995-70995b0b9ac8
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ede19ada6509bd4473ac2455fbe6cd9fdf5ec8b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51735688"
---
# <a name="how-to-view-script-documents"></a>Procedura: visualizzare documenti script
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nelle versioni precedenti di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] i file script sul lato client generati da uno script sul lato server venivano visualizzati nella finestra Esplora script. La finestra Esplora script era spesso nascosta, per cui la disponibilità di script sul lato client non era sempre ovvia.  
  
 In [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] i file script sul lato client generati da uno script sul lato server vengono visualizzati in Esplora soluzioni, visualizzata per impostazione predefinita. La finestra Esplora script è stata eliminata.  
  
 I file script sul lato client sono visibili solo in modalità di debug o in modalità interruzione. Vengono visualizzati nei **documenti Script** nodo.  
  
 I file script sul lato server sono sempre visibili. Vengono visualizzati nei  **\<percorso sito Web >** nodo. Il nome del nodo è simile a questo esempio: `c:\...\Website2\`  
  
### <a name="to-view-a-server-side-script-document"></a>Per visualizzare un documento script sul lato server  
  
1.  Nelle **Esplora soluzioni**, aprire il  **\<percorso sito Web >** nodo.  
  
2.  Fare doppio clic sul file script che si desidera visualizzare.  
  
     Il file script sul lato server verrà aperto in una finestra di origine.  
  
### <a name="to-view-a-client-side-script-document"></a>Per visualizzare un documento script sul lato client  
  
1.  Nelle **Esplora soluzioni**, aprire il **documenti Script** nodo.  
  
2.  Fare doppio clic sul file script che si desidera visualizzare.  
  
     Il file script sul lato client verrà aperto in una finestra di origine.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione di dati nel debugger](../debugger/viewing-data-in-the-debugger.md)



