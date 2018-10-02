---
title: 'Procedura dettagliata: Cattura delle informazioni grafica | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 48f12f6e-57b4-48ec-a145-89fa71a42424
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de553729d37bb82d1b30c6a142f7e65c983bb1c1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47519060"
---
# <a name="walkthrough-capturing-graphics-information"></a>Procedura dettagliata: cattura delle informazioni grafica
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura dettagliata: acquisizione di informazioni grafiche](https://docs.microsoft.com/visualstudio/debugger/graphics/walkthrough-capturing-graphics-information).  
  
Questa procedura dettagliata illustra come usare il [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] diagnostica della grafica per acquisire manualmente informazioni grafiche da un'app Direct3D.  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   Associazione di Diagnostica grafica all'app  
  
-   Acquisizione di informazioni grafiche  
  
## <a name="capturing-graphics-information"></a>Acquisizione di informazioni grafiche  
 Per usare gli strumenti di diagnostica grafica, occorre prima di tutto acquisire le informazioni grafiche necessarie. Per abilitare l'acquisizione, usare il comando **Avvia diagnostica** per associare Diagnostica grafica all'app all'avvio.  
  
#### <a name="to-enable-the-capture-of-graphics-information-after-a-project-or-solution-is-loaded"></a>Per abilitare l'acquisizione di informazioni grafiche dopo il caricamento di un progetto o una soluzione  
  
1.  In [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], caricare un file di progetto o una soluzione per l'app che si desidera acquisire informazioni grafiche da.  
  
2.  Scegliere **Avvia diagnostica**sulla barra degli strumenti Diagnostica grafica.  
  
#### <a name="to-enable-the-capture-of-graphics-information-without-loading-a-project-or-solution"></a>Per abilitare l'acquisizione di informazioni grafiche senza caricare un progetto o una soluzione  
  
1.  Nella barra dei menu scegliere **File**, **Apri**, **Progetto/Soluzione**. Verrà visualizzata la finestra di dialogo **Apri progetto** .  
  
2.  Invece di un file di progetto o di soluzione, specificare il file eseguibile per l'app da cui si vogliono acquisire le informazioni grafiche e quindi scegliere **Apri**.  
  
3.  Nella barra dei menu scegliere **Debug**, **Grafica**, **Avvia diagnostica**.  
  
 Dopo aver avviato l'applicazione e i relativi frame di rendering, è possibile acquisire le informazioni grafiche.  
  
#### <a name="to-capture-graphics-information"></a>Per acquisire informazioni grafiche  
  
-   Scegliere **Acquisisci** sulla barra degli strumenti Diagnostica grafica. ![Icona pulsante acquisizione grafica](../debugger/media/debuggingdirectxgraphics.png "DebuggingDirectXGraphics")  
  
     oppure  
  
     Con lo stato attivo nell'app premere **STAMP**.  
  
 Ogni volta che si acquisiscono informazioni su un frame, Diagnostica grafica registra gli eventi di Direct3D e lo stato associato e aggiunge questi dati a un log di grafica. Per ogni sessione di Diagnostica grafica viene creato un nuovo log di grafica. Per informazioni sui log di grafica, vedere [Panoramica](../debugger/overview-of-visual-studio-graphics-diagnostics.md).  
  
## <a name="next-steps"></a>Passaggi successivi  
 In questa procedura dettagliata è stato illustrato come acquisire informazioni grafiche manualmente. Come passaggio successivo, prendere in considerare questa opzione:  
  
-   Apprendere come analizzare le informazioni grafiche acquisite usando gli strumenti di Diagnostica grafica. Visualizzare [Panoramica](../debugger/overview-of-visual-studio-graphics-diagnostics.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Acquisizione di informazioni grafiche](../debugger/capturing-graphics-information.md)



