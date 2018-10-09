---
title: 'Procedura: Applicare uno shader a un modello 3D | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a3877bd6-abd8-4a9d-842c-6848b6c2f335
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 277711a0dd2a106c8770b2b7d720666589e65d86
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47529892"
---
# <a name="how-to-apply-a-shader-to-a-3-d-model"></a>Procedura: Applicare uno shader a un modello tridimensionale
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura: applicare uno Shader a un modello 3D](https://docs.microsoft.com/visualstudio/designers/how-to-apply-a-shader-to-a-3-d-model).  
  
Questo documento illustra come usare l'editor dei modelli per applicare uno shader DGSL (Directed Graph Shader Language) a un modello 3D.  
  
 Questo documento illustra questa attività:  
  
-   Applicazione di uno shader a un modello 3D  
  
## <a name="applying-a-shader-to-a-3-d-model"></a>Applicazione di uno shader a un modello 3D  
 È possibile applicare un effetto shader a un modello 3D per conferirgli un aspetto più interessante.  
  
 Prima di iniziare, assicurarsi che sia visualizzata la finestra **Proprietà**.  
  
#### <a name="to-apply-a-shader-to-a-3-d-model"></a>Per applicare uno shader a un modello 3D  
  
1.  Iniziare con una scena 3D contenente uno o più modelli. Se non si ha una scena 3D adatta, crearne una come descritto in [Procedura: Creare un modello 3D di base](../designers/how-to-create-a-basic-3-d-model.md). È necessario avere anche uno shader DGSL da applicare al modello. Se non si ha uno shader adatto, crearne uno come descritto in [Procedura: Creare uno shader con colore di base](../designers/how-to-create-a-basic-color-shader.md) e assicurarsi di salvarlo in un file prima di continuare.  
  
2.  In modalità **Seleziona** selezionare il modello a cui si vuole applicare lo shader e, nella finestra **Proprietà**, specificare lo shader DGSL da applicare al modello nella proprietà **Nome file** del gruppo di proprietà **Effetto**.  
  
 Di seguito è illustrato un modello a cui è stato applicato l'effetto colore di base.  
  
 ![Scena 3D che illustra l'effetto colore di base](../designers/media/digit-3d-model-effect.png "Digit-3D-Model-Effect")  
  
 Dopo aver applicato uno shader a un modello, è possibile aprirlo nella finestra di progettazione shader selezionando il modello e, nella finestra **Proprietà**, scegliendo il pulsante con i puntini di sospensione (**...** ) nella proprietà **(Avanzata)** del gruppo di proprietà **Effetto**.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Creare un modello 3D di base](../designers/how-to-create-a-basic-3-d-model.md)   
 [Procedura: Creare uno shader con colore di base](../designers/how-to-create-a-basic-color-shader.md)   
 [Editor dei modelli](../designers/model-editor.md)   
 [Finestra di progettazione shader](../designers/shader-designer.md)


