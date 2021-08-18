---
title: 'Procedura: Creare uno shader con sfumatura basata sulla geometria'
description: Informazioni su come usare la finestra di progettazione shader e il Graph shader per creare uno shader con sfumatura basata sulla geometria che ridimensiona un valore di colore RGB costante.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 4b204405-ba95-4c5e-bd51-ec033a3ebfb6
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-designers
ms.workload:
- multiple
ms.openlocfilehash: 68d0c5af184fa22a41204f7d1937831b67c80244
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122104872"
---
# <a name="how-to-create-a-geometry-based-gradient-shader"></a>Procedura: Creare uno shader con un gradiente basato sulla geometria

Questo articolo illustra come usare la finestra di progettazione shader e il linguaggio DGSL (Directed Graph Shader Language) per creare uno shader con sfumatura basata sulla geometria. Questo shader ridimensiona un valore di colore RGB costante in base all'altezza di ogni punto di un oggetto nello spazio globale.

## <a name="create-a-geometry-based-gradient-shader"></a>Creare uno shader con sfumatura basata sulla geometria

È possibile implementare uno shader basato sulla geometria incorporando la posizione del pixel nello shader. Nei linguaggi shader, oltre al colore e alla posizione sullo schermo 2D, un pixel contiene altre informazioni. Un pixel, noto in alcuni sistemi come *frammento*, è costituito da una raccolta di valori che descrivono l'area corrispondente a un pixel. Lo shader descritto in questo documento usa l'altezza di ciascun pixel di un oggetto 3D nello spazio globale per influire sul colore di output finale del frammento.

Prima di iniziare, assicurarsi che siano visualizzate la finestra **Proprietà** e la **casella degli strumenti**.

1. Creare uno shader DGSL da usare. Per informazioni su come aggiungere uno shader DGSL al progetto, vedere la sezione Introduzione in [Finestra di progettazione shader](../designers/shader-designer.md).

2. Scollegare il nodo **Colore punto** dal nodo **Colore finale**. Scegliere il terminale **RGB** del nodo **Colore punto** e quindi scegliere **Interrompi collegamenti**. In questo modo si crea lo spazio per il nodo che viene aggiunto nel passaggio successivo.

3. Aggiungere un nodo **Per** al grafico. Nella **casella degli strumenti**, in **Matematica**, selezionare **Per** e spostarlo nell'area di progettazione.

4. Aggiungere un nodo **Mascheramento vettore** al grafico. Nella **casella degli strumenti**, in **Utilità**, selezionare **Mascheramento vettore** e spostarlo nell'area di progettazione.

5. Specificare i valori di maschera per il nodo **Mascheramento vettore**. In modalità **Seleziona** selezionare il nodo **Mascheramento vettore** e nella finestra **Proprietà** impostare la proprietà **Verde / Y** su **True**. Impostare quindi le proprietà **Rosso / X**, **Blu / Z** e **Alfa / W** su **False**. In questo esempio, le proprietà **Rosso / X**, **Verde / Y** e **Blu / Z** corrispondono ai componenti x, y e z del nodo **Posizione globale** e **Alfa / W** non viene usato. Poiché solo **Verde / Y** è impostato su **True**, dopo il mascheramento del vettore di input rimane solo il componente y.

6. Aggiungere un nodo **Posizione globale** al grafico. Nella **casella degli strumenti**, in **Costanti**, selezionare **Posizione globale** e spostarlo nell'area di progettazione.

7. Mascherare la posizione del frammento nello spazio globale. In modalità **Seleziona** spostare il terminale **Output** del nodo **Posizione globale** nel terminale **Vettore** del nodo **Mascheramento vettore**. Questa connessione maschera la posizione del frammento in modo da ignorare i componenti x e z.

8. Moltiplicare la costante di colore RGB per la posizione mascherata nello spazio globale. Spostare il terminale **RGB** del nodo **Colore punto** nel terminale **Y** del nodo **Per** e quindi spostare il terminale **Output** del nodo **Mascheramento vettore** nel terminale **X** del nodo **Per**. Tale connessione consente di ridimensionare il valore del colore in base all'altezza del pixel nello spazio globale.

9. Collegare il valore del colore ridimensionato al colore finale. Spostare il terminale **Output** del nodo **Per** nel terminale **RGB** del nodo **Colore finale**.

La figura seguente illustra il grafico shader completato e un'anteprima dello shader applicato a una sfera.

> [!NOTE]
> In questa figura è stato specificato un colore arancione per illustrare meglio l'effetto dello shader, ma poiché la forma di anteprima non ha una posizione nello spazio globale, lo shader non può essere interamente visualizzato in anteprima nella finestra di progettazione dello shader. Per poter illustrare l'effetto completo, lo shader deve essere visualizzato in anteprima in una scena reale.

![Grafico shader e anteprima del relativo effetto](../designers/media/digit-gradient-effect-graph.png)

Alcune forme potrebbero produrre anteprime migliori per alcuni shader. Per informazioni su come visualizzare in anteprima gli shader nella finestra di progettazione shader, vedere la sezione **Anteprima degli shader** in [Finestra di progettazione shader](../designers/shader-designer.md).

La figura seguente illustra lo shader descritto in questo documento applicato alla scena 3D illustrata in [Procedura: Creare un modello di terreno 3D](../designers/how-to-model-3-d-terrain.md). L'intensità del colore aumenta con l'altezza del punto nello spazio globale.

![Effetto sfumatura applicato a un modello di terreno 3D](../designers/media/digit-gradient-effect-result.png)

Per altre informazioni su come applicare uno shader a un modello 3D, vedere Procedura: Applicare uno [shader a un modello 3D.](../designers/how-to-apply-a-shader-to-a-3-d-model.md)

## <a name="see-also"></a>Vedi anche

- [Procedura: Applicare uno shader a un modello 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Procedura: Esportare uno shader](../designers/how-to-export-a-shader.md)
- [Procedura: Modellare il terreno 3D](../designers/how-to-model-3-d-terrain.md)
- [Procedura: Creare uno shader con trama in scala di grigi](../designers/how-to-create-a-grayscale-texture-shader.md)
- [Finestra di progettazione shader](../designers/shader-designer.md)
- [Nodi della finestra di progettazione shader](../designers/shader-designer-nodes.md)
