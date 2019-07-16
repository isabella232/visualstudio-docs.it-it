---
title: 'Procedura: Visualizzare documenti Script | Microsoft Docs'
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
- Script Explorer
ms.assetid: 8b621e53-4508-4b4a-9995-70995b0b9ac8
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 88f923ab0447f1ac7d57e84d94f0ab442d912d67
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68189594"
---
# <a name="how-to-view-script-documents"></a>Procedura: Visualizzare documenti script
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nelle versioni precedenti di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] i file script sul lato client generati da uno script sul lato server venivano visualizzati nella finestra Esplora script. La finestra Esplora script era spesso nascosta, per cui la disponibilità di script sul lato client non era sempre ovvia.  
  
 In [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] i file script sul lato client generati da uno script sul lato server vengono visualizzati in Esplora soluzioni, visualizzata per impostazione predefinita. La finestra Esplora script è stata eliminata.  
  
 I file script sul lato client sono visibili solo in modalità di debug o in modalità interruzione. Vengono visualizzati nel nodo **Documenti script**.  
  
 I file script sul lato server sono sempre visibili. Vengono visualizzati nel nodo **\<Percorso sito Web>** . Il nome del nodo è simile a questo esempio: `c:\...\Website2\`  
  
### <a name="to-view-a-server-side-script-document"></a>Per visualizzare un documento script sul lato server  
  
1. In **Esplora soluzioni** aprire il nodo **\<Percorso sito Web>** .  
  
2. Fare doppio clic sul file script che si desidera visualizzare.  
  
     Il file script sul lato server verrà aperto in una finestra di origine.  
  
### <a name="to-view-a-client-side-script-document"></a>Per visualizzare un documento script sul lato client  
  
1. In **Esplora soluzioni** aprire il nodo **Documenti script**.  
  
2. Fare doppio clic sul file script che si desidera visualizzare.  
  
     Il file script sul lato client verrà aperto in una finestra di origine.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione di dati nel debugger](../debugger/viewing-data-in-the-debugger.md)
