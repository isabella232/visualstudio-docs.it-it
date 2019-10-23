---
title: 'Procedura: Applicare uno shader a un modello 3D | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: a3877bd6-abd8-4a9d-842c-6848b6c2f335
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 15d88f52b3af3a3e4502c618280107a882761259
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664606"
---
# <a name="how-to-apply-a-shader-to-a-3-d-model"></a>Procedura: Applicare uno shader a un modello 3D
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questo documento illustra come usare l'editor dei modelli per applicare uno shader DGSL (Directed Graph Shader Language) a un modello 3D.

 Questo documento illustra questa attività:

- Applicazione di uno shader a un modello 3D

## <a name="applying-a-shader-to-a-3-d-model"></a>Applicazione di uno shader a un modello 3D
 È possibile applicare un effetto shader a un modello 3D per conferirgli un aspetto più interessante.

 Prima di iniziare, assicurarsi che sia visualizzata la finestra **Proprietà**.

#### <a name="to-apply-a-shader-to-a-3-d-model"></a>Per applicare uno shader a un modello 3D

1. Iniziare con una scena 3D contenente uno o più modelli. Se non si ha una scena 3D adatta, crearne una come descritto in [How per: Creare un modello 3D di base ](../designers/how-to-create-a-basic-3-d-model.md). È necessario avere anche uno shader DGSL da applicare al modello. Se non si ha uno shader adatto, crearne uno come descritto in [Procedura: Creare uno shader con colore di base ](../designers/how-to-create-a-basic-color-shader.md) e assicurarsi che sia stato salvato in un file prima di continuare.

2. In modalità **Seleziona** selezionare il modello a cui si vuole applicare lo shader e, nella finestra **Proprietà**, specificare lo shader DGSL da applicare al modello nella proprietà **Nome file** del gruppo di proprietà **Effetto**.

   Di seguito è illustrato un modello a cui è stato applicato l'effetto colore di base.

   ![scena&#45;3 D che mostra l'effetto colore di base](../designers/media/digit-3d-model-effect.png "Digit-3D-Model-Effect")

   Dopo aver applicato uno shader a un modello, è possibile aprirlo nella finestra di progettazione shader selezionando il modello e, nella finestra **Proprietà**, scegliendo il pulsante con i puntini di sospensione ( **...** ) nella proprietà **(Avanzata)** del gruppo di proprietà **Effetto**.

## <a name="see-also"></a>Vedere anche
 [Procedura: Creare un modello 3D di base ](../designers/how-to-create-a-basic-3-d-model.md) [How per: Creare una [finestra di progettazione shader](../designers/shader-designer.md) di base ](../designers/how-to-create-a-basic-color-shader.md) [modello](../designers/model-editor.md) di shader
