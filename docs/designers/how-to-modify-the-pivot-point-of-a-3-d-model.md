---
title: 'Procedura: Modificare il punto pivot di un modello 3D'
description: Informazioni su come usare l'Editor modelli per modificare il punto pivot di un modello 3D, ovvero il punto che definisce il centro dell'oggetto per la rotazione e il ridimensionamento.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c20b4ec8-29f5-4ca5-bc39-d4548ca6f573
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-designers
ms.workload:
- multiple
ms.openlocfilehash: 1ee504bfb1cc919fd721f66fd3e0141784d7cd7fe3f3d5df27d927ac71a27d98
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121308616"
---
# <a name="how-to-modify-the-pivot-point-of-a-3d-model"></a>Procedura: Modificare il punto pivot di un modello 3D

Questo articolo illustra come usare l'editor dei modelli per modificare il *punto di perno* di un modello 3D. Il punto di perno è il punto nello spazio che definisce il centro matematico dell'oggetto per la rotazione e il ridimensionamento.

## <a name="modify-the-pivot-point-of-a-3d-model"></a>Modificare il punto pivot di un modello 3D

È possibile ridefinire l'origine di un modello 3D modificandone il punto di perno.

Assicurarsi che siano visualizzate la finestra **Proprietà** e la **casella degli strumenti**.

1. Iniziare con un modello 3D esistente, ad esempio quello descritto in [Procedura: Creare un modello 3D di base.](../designers/how-to-create-a-basic-3-d-model.md)

2. Passare alla modalità perno. Nella barra degli strumenti disponibile in modalità **Editor dei modelli** scegliere il pulsante **Modalità perno** per attivare la modalità perno. Viene visualizzata una casella intorno al pulsante **Modalità perno** per indicare che l'editor dei modelli è ora in modalità perno. In modalità perno, operazioni come la traslazione agiscono sul punto di perno dell'oggetto anziché sulla struttura dell'oggetto nello spazio globale.

3. Modificare il punto di perno dell'oggetto. In modalità **Seleziona** selezionare l'oggetto e nella barra degli strumenti del **visualizzatore modelli** scegliere lo strumento **Trasla**. Nell'area di progettazione viene visualizzata una casella che rappresenta il punto di perno. Spostare la casella per modificare il punto di perno dell'oggetto.

     Spostando la casella è possibile spostare il punto di perno in tutte le tre dimensioni. Per traslare il punto di perno lungo un asse, spostare la freccia corrispondente all'asse. La casella e le frecce vengono visualizzate in giallo per indicare l'asse interessata dalla traslazione.

     È possibile specificare il punto di perno anche tramite la proprietà **Traslazione perno** della finestra **Proprietà**.

    > [!TIP]
    > È possibile visualizzare l'effetto del nuovo punto di perno ruotando l'oggetto. Per ruotarlo, usare lo strumento **Ruota** o modificare la proprietà **Rotazione**.

Di seguito è riportato un modello con un punto di perno modificato:

![Modello di casa con punto pivot modificato](../designers/media/digit-modified-model.png)

## <a name="see-also"></a>Vedi anche

- [Procedura: Creare un modello 3D di base](../designers/how-to-create-a-basic-3-d-model.md)
- [Editor dei modelli](../designers/model-editor.md)
