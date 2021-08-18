---
title: 'Procedura dettagliata: Acquisizione di informazioni grafiche | Microsoft Docs'
description: Informazioni su come usare Visual Studio Diagnostica della grafica acquisire manualmente informazioni grafiche da un'app Direct3D.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 48f12f6e-57b4-48ec-a145-89fa71a42424
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 241ffcdb979dec0c7e39cb998479090c1e596bc18e6251ee1fe22e7b163fd0c5
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121435868"
---
# <a name="walkthrough-capturing-graphics-information"></a>Procedura dettagliata: Acquisizione di informazioni grafiche
Questa procedura dettagliata dimostra come usare Diagnostica grafica di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per acquisire manualmente informazioni grafiche da un'app Direct3D.

 In questa procedura dettagliata vengono illustrate le attività seguenti:

- Associazione di Diagnostica grafica all'app

- Acquisizione di informazioni grafiche

## <a name="capturing-graphics-information"></a>Acquisizione di informazioni grafiche
 Per usare gli strumenti di diagnostica grafica, occorre prima di tutto acquisire le informazioni grafiche necessarie. Per abilitare l'acquisizione, usare il comando **Avvia diagnostica** per associare Diagnostica grafica all'app all'avvio.

#### <a name="to-enable-the-capture-of-graphics-information-after-a-project-or-solution-is-loaded"></a>Per abilitare l'acquisizione di informazioni grafiche dopo il caricamento di un progetto o una soluzione

1. In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]caricare un file di progetto o di soluzione per l'app dalla quale si vogliono acquisire informazioni grafiche.

2. Scegliere **Avvia diagnostica** sulla barra degli strumenti Diagnostica grafica.

#### <a name="to-enable-the-capture-of-graphics-information-without-loading-a-project-or-solution"></a>Per abilitare l'acquisizione di informazioni grafiche senza caricare un progetto o una soluzione

1. Nella barra dei menu scegliere **File**, **Apri**, **Progetto/Soluzione**. Verrà visualizzata la finestra di dialogo **Apri progetto** .

2. Invece di un file di progetto o di soluzione, specificare il file eseguibile per l'app da cui si vogliono acquisire le informazioni grafiche e quindi scegliere **Apri**.

3. Nella barra dei menu scegliere **Debug**, **Grafica**, **Avvia diagnostica**.

   Dopo aver avviato l'applicazione e i relativi frame di rendering, è possibile acquisire le informazioni grafiche.

#### <a name="to-capture-graphics-information"></a>Per acquisire informazioni grafiche

- Scegliere **Acquisisci** sulla barra degli strumenti Diagnostica grafica. ![Icona pulsante acquisizione grafica](media/debuggingdirectxgraphics.png "DebuggingDirectXGraphics")

   -oppure-

   Con lo stato attivo nell'app premere **STAMP**.

  Ogni volta che si acquisiscono informazioni su un frame, Diagnostica grafica registra gli eventi di Direct3D e lo stato associato e aggiunge questi dati a un log di grafica. Per ogni sessione di Diagnostica grafica viene creato un nuovo log di grafica. Per informazioni sui log di grafica, vedere [Panoramica.](overview-of-visual-studio-graphics-diagnostics.md)

## <a name="next-steps"></a>Passaggi successivi
 In questa procedura dettagliata è stato illustrato come acquisire informazioni grafiche manualmente. Come passaggio successivo, prendere in considerare questa opzione:

- Apprendere come analizzare le informazioni grafiche acquisite usando gli strumenti di Diagnostica grafica. Vedere [Panoramica.](overview-of-visual-studio-graphics-diagnostics.md)

## <a name="see-also"></a>Vedi anche
- [Acquisizione di informazioni grafiche](capturing-graphics-information.md)