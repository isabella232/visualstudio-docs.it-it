---
title: 'Procedura: Creare uno shader con phong di base'
description: Informazioni su come usare La finestra di progettazione shader e il linguaggio Graph shader per creare uno shader di illuminazione che implementa il modello di illuminazione Phong classico.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c7c69da8-142b-4d3b-9be9-4be0d5970b25
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-designers
ms.workload:
- multiple
ms.openlocfilehash: b04f8b9188d982f12f6de2be13751644116a77eff5a72a1170f3808b2e8250eb
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121435206"
---
# <a name="how-to-create-a-basic-phong-shader"></a>Procedura: Creare uno shader con phong di base

Questo articolo illustra come usare la finestra di progettazione shader e il linguaggio DGSL (Directed Graph Shader Language) per creare uno shader di illuminazione che implementa il modello di illuminazione Phong classico.

## <a name="the-phong-lighting-model"></a>Modello di illuminazione Phong

Il modello di illuminazione Phong estende il modello di illuminazione Lambert con l'evidenziazione speculare, che simula le proprietà riflettenti di una superficie. Il componente speculare fornisce maggiore illuminazione dalle stesse sorgenti di luce direzionale usate nel modello di illuminazione Lambert, ma il contributo apportato al colore finale viene elaborato in modo diverso. L'evidenziazione speculare influenza ogni area della scena in modo diverso, in base alla relazione tra la direzione di visualizzazione, la direzione delle sorgenti di luce e l'orientamento della superficie. È un prodotto del colore speculare, della potenza speculare e dell'orientamento della superficie, nonché del colore, dell'intensità e della direzione delle sorgenti di luce. Le superfici che riflettono la sorgente di luce in direzione dell'osservatore ricevono il contributo speculare massimo, mentre le superfici che riflettono la sorgente di luce lontano dall'osservatore non ricevono alcun contributo. Nel modello di illuminazione Phong uno o più componenti speculari vengono combinati per determinare il colore e l'intensità di evidenziazione speculare di ogni punto sull'oggetto e quindi vengono aggiunti al risultato del modello di illuminazione Lambert per produrre il colore finale del pixel.

Per altre informazioni sul modello di illuminazione Lambert, vedere [Procedura: Creare uno shader con Lambert di base](../designers/how-to-create-a-basic-lambert-shader.md).

Prima di iniziare, assicurarsi che siano visualizzate la finestra **Proprietà** e la **casella degli strumenti**.

1. Creare uno shader Lambert, come descritto in [Procedura: Creare uno shader con Lambert di base](../designers/how-to-create-a-basic-lambert-shader.md).

2. Scollegare il nodo **Lambert** dal nodo **Colore finale**. Scegliere il terminale **RGB** del nodo **Lambert** e quindi scegliere **Interrompi collegamenti**. In questo modo si crea lo spazio per il nodo che viene aggiunto nel passaggio successivo.

3. Aggiungere un nodo **Aggiungi** al grafico. Nella **casella degli strumenti**, in **Matematica**, selezionare **Aggiungi** e spostarlo nell'area di progettazione.

4. Aggiungere un nodo **Speculare** al grafico. Nella **casella degli strumenti**, in **Utilità**, selezionare **Speculare** e spostarlo nell'area di progettazione.

5. Aggiungere il contributo speculare. Spostare il terminale **Output** del nodo **Speculare** nel terminale **X** del nodo **Aggiungi** e quindi spostare il terminale **Output** del nodo **Lambert** nel terminale **Y** del nodo **Aggiungi**. Queste connessioni combinano i contributi totali di colore con riflessione diffusa e colore speculare per il pixel.

6. Collegare il valore del colore calcolato al colore finale. Spostare il terminale **Output** del nodo **Aggiungi** nel terminale **RGB** del nodo **Colore finale**.

   La figura seguente illustra il grafico shader completato e un'anteprima dello shader applicato a un modello di teiera.

> [!NOTE]
> Per illustrare meglio l'effetto dello shader in questa figura, è stato specificato un colore arancione usando il parametro **MaterialDiffuse** dello shader e un colore metallizzato usando i parametri **MaterialSpecular** e **MaterialSpecularPower**. Per informazioni sui parametri di materiale, vedere la sezione Anteprima degli shader in [Finestra di progettazione shader](../designers/shader-designer.md).

![Grafico shader e anteprima del relativo effetto](../designers/media/digit-lighting-graph.png)

Alcune forme potrebbero produrre anteprime migliori per alcuni shader. Per altre informazioni su come visualizzare in anteprima gli shader nella finestra di progettazione shader, vedere la sezione Anteprima degli shader in [Progettazione shader](../designers/shader-designer.md)

La figura seguente illustra lo shader descritto in questo documento applicato a un modello 3D. La proprietà **MaterialSpecular** è impostata su (1.00, 0.50, 0.20, 0.00) e la proprietà **MaterialSpecularPower** è impostata su 16.

> [!NOTE]
> La proprietà **MaterialSpecular** determina la finitura apparente della superficie. Una superficie molto lucente come il vetro o la plastica tende ad avere un colore speculare equivalente a una sfumatura brillante di bianco, mentre una superficie metallica tende ad avere un colore speculare simile al relativo colore diffuso. Una superficie con finitura satinata tende invece ad avere un colore speculare equivalente a una sfumatura scura di grigio.
>
> La proprietà **MaterialSpecularPower** determina l'intensità delle evidenziazioni speculari. Potenze speculari elevate simulano evidenziazioni deboli e più localizzate, mentre potenze speculari molto deboli simulano evidenziazioni intense e ampie che possono saturare eccessivamente e nascondere il colore dell'intera superficie.

![Illuminazione Phong applicata a un modello](../designers/media/digit-lighting-model.png)

Per altre informazioni su come applicare uno shader a un modello 3D, vedere Procedura: Applicare uno [shader a un modello 3D.](../designers/how-to-apply-a-shader-to-a-3-d-model.md)

## <a name="see-also"></a>Vedi anche

- [Procedura: Applicare uno shader a un modello 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Procedura: Esportare uno shader](../designers/how-to-export-a-shader.md)
- [Procedura: Creare uno shader Lambert di base](../designers/how-to-create-a-basic-lambert-shader.md)
- [Finestra di progettazione shader](../designers/shader-designer.md)
- [Nodi della finestra di progettazione shader](../designers/shader-designer-nodes.md)
