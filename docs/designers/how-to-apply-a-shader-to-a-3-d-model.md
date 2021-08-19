---
title: 'Procedura: Applicare uno shader a un modello 3D'
description: Informazioni su come usare l'Editor modelli per applicare uno shader directed Graph Shader Language a un modello 3D per ottenere un aspetto interessante.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: a3877bd6-abd8-4a9d-842c-6848b6c2f335
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-designers
ms.workload:
- multiple
ms.openlocfilehash: 08f078d07ad1a3d408c25f5cda2d8d19754ae881
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122127818"
---
# <a name="how-to-apply-a-shader-to-a-3d-model"></a>Procedura: Applicare uno shader a un modello 3D

Questo articolo illustra come usare l'editor dei modelli per applicare uno shader DGSL (Directed Graph Shader Language) a un modello 3D.

## <a name="apply-a-shader-to-a-3d-model"></a>Applicare uno shader a un modello 3D

È possibile applicare un effetto shader a un modello 3D per conferirgli un aspetto più interessante.

Prima di iniziare, assicurarsi che sia visualizzata la finestra **Proprietà**.

1. Iniziare con una scena 3D contenente uno o più modelli. Se non si ha una scena 3D adatta, crearne una come descritto in Procedura: Creare un modello [3D di base.](../designers/how-to-create-a-basic-3-d-model.md) È necessario avere anche uno shader DGSL da applicare al modello. Se non si ha uno shader adatto, crearne uno come descritto in [Procedura: Creare uno shader con colore di base](../designers/how-to-create-a-basic-color-shader.md) e assicurarsi di salvarlo in un file prima di continuare.

2. In modalità **Seleziona** selezionare il modello a cui si vuole applicare lo shader e nella finestra **Proprietà** specificare lo shader DGSL da applicare al modello nella proprietà **Nome file** del gruppo di proprietà **Effetto**.

Di seguito è illustrato un modello a cui è stato applicato l'effetto colore di base.

![Scena 3D che illustra l'effetto colore di base](../designers/media/digit-3d-model-effect.png)

Dopo aver applicato uno shader a un modello, è possibile aprirlo nella finestra di progettazione shader selezionando il modello e, nella finestra **Proprietà**, scegliendo il pulsante con i puntini di sospensione (**...**) nella proprietà **(Avanzata)** del gruppo di proprietà **Effetto**.

## <a name="see-also"></a>Vedi anche

- [Procedura: Creare un modello 3D di base](../designers/how-to-create-a-basic-3-d-model.md)
- [Procedura: Creare uno shader con colori di base](../designers/how-to-create-a-basic-color-shader.md)
- [Editor dei modelli](../designers/model-editor.md)
- [Finestra di progettazione shader](../designers/shader-designer.md)
