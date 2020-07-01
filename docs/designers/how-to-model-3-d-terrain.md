---
title: 'Procedura: Creare un modello di territorio 3D'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: f779b1fd-82a9-4a11-8ab7-c1c9caabc883
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 12f19363d9024f8e7e2deb69a8038b8854eb50e4
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85768967"
---
# <a name="how-to-model-3d-terrain"></a>Procedura: Creare un modello di terreno 3D

Questo articolo illustra come usare l'editor dei modelli per creare un modello di terreno 3D.

## <a name="create-a-3d-terrain-model"></a>Creare un modello di terreno 3D

È possibile creare un terreno 3D suddividendo un piano in modo da creare facce aggiuntive e quindi manipolando i vertici in modo da creare caratteristiche del terreno interessanti.

Al termine, il modello dovrebbe risultare simile al seguente:

![Scena 3D che illustra un modello di terreno](../designers/media/digit-terrain-model.png)

Prima di iniziare, assicurarsi che siano visualizzate la finestra **Proprietà** e la **casella degli strumenti**.

1. Creare un modello 3D da usare. Per informazioni su come aggiungere un modello al progetto, vedere la sezione Introduzione in [Editor dei modelli](../designers/model-editor.md).

2. Aggiungere un piano alla scena. Nella **casella degli strumenti**, in **Forme**, selezionare **Piano** e spostarlo nell'area di progettazione.

    > [!TIP]
    > Per semplificare l'utilizzo dell'oggetto piano è possibile inserirlo in un frame nell'area di progettazione. In modalità **Seleziona** selezionare l'oggetto piano nella barra degli strumenti dell'editor dei modelli scegliere il pulsante **FrameObject**.

3. Passare alla modalità di selezione icona. Nella barra degli strumenti dell'editor dei modelli scegliere **Seleziona icona**.

4. Suddividere il piano. In modalità di selezione icona scegliere una volta il piano per attivarlo per la selezione e quindi sceglierlo di nuovo per selezionarne l'icona. Nella barra degli strumenti dell'editor dei modelli scegliere **Suddividi faccia**. In questo modo vengono aggiunti nuovi vertici al piano in modo che risulti suddiviso in quattro parti uguali.

5. Creare altre suddivisioni. Con le nuove icone ancora selezionate, scegliere **Suddividi faccia** altre due volte. Viene così creato un totale di 64 icone. Creando più suddivisioni, è possibile aumentare ulteriormente il livello di dettaglio del terreno.

6. Passare alla modalità di selezione punto. Nella barra degli strumenti Editor modello scegliere **Seleziona punto**.

7. Modificare un punto per creare una caratteristica del terreno. In modalità di selezione punto selezionare uno dei punti e scegliere lo strumento **Trasla** nella barra degli strumenti dell'editor dei modelli. Nell'area di progettazione viene visualizzata una casella che rappresenta il punto. Usare la freccia verde per spostare la casella e modificare l'altezza del punto. Ripetere questo passaggio per tutti gli altri punti con l'obiettivo di creare funzionalità del terreno interessanti.

    > [!TIP]
    > È possibile selezionare contemporaneamente più punti per modificarli in modo uniforme.

Il modello di terreno è completo. Di seguito viene nuovamente illustrato il modello finale con l'ombreggiatura Phong applicata.

![Scena 3D che illustra un modello di terreno](../designers/media/digit-terrain-model.png)

È possibile usare questo modello di terreno per dimostrare l'effetto dello shader sfumato descritto in [procedura: creare uno shader con sfumatura basata sulla geometria](../designers/how-to-create-a-geometry-based-gradient-shader.md).

## <a name="see-also"></a>Vedere anche

- [Editor dei modelli](../designers/model-editor.md)
