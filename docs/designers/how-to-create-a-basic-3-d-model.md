---
title: 'Procedura: Creare un modello 3D di base'
description: Informazioni su come usare l'Editor modelli per creare un modello 3D di base, inclusa l'aggiunta di oggetti a una scena, la traduzione delle selezioni e altre attività.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: a0d97966-2df8-449b-a8cf-5a19684dc773
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-designers
ms.workload:
- multiple
ms.openlocfilehash: a9bb4e2c847cdc198f3955cccb2f3b86cd85dcff
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122153667"
---
# <a name="how-to-create-a-basic-3d-model"></a>Procedura: Creare un modello 3D di base

Questo articolo illustra come usare l'editor dei modelli per creare un modello 3D di base. Sono descritte le attività seguenti:

- Aggiunta di oggetti a una scena

- Selezione di facce e bordi

- Traslazione delle selezioni

- Utilizzo degli strumenti **Suddividi faccia** e **Estrudi faccia**

- Utilizzo del comando **Triangolazione**

## <a name="create-a-basic-3d-model"></a>Creazione di un modello 3D di base
È possibile usare l'editor dei modelli per creare e modificare modelli e scene 3D per il gioco o l'applicazione. Nei passaggi seguenti viene illustrato come usare l'editor dei modelli per creare un modello 3D semplificato di una casa. Un modello semplificato può essere utilizzato come alternativa temporanea agli asset grafici finali ancora in fase di creazione, come mesh per il rilevamento dei conflitti o come modello a basso livello di dettaglio da utilizzare quando l'oggetto da esso rappresentato è troppo distante per beneficiare di un rendering più dettagliato.

Al termine, il modello dovrebbe risultare simile al seguente:

![Modello completato della casa semplificata](../designers/media/gfx_model_demo_house_final.png)

Prima di iniziare, assicurarsi che siano visualizzate la finestra **Proprietà** e la **casella degli strumenti**.

### <a name="to-create-a-simplified-3d-model-of-a-house"></a>Per creare un modello 3D semplificato di una casa

1. Creare un modello 3D da usare. Per informazioni su come aggiungere un modello al progetto, vedere la sezione Attività iniziali [nell'Editor modelli](../designers/model-editor.md).

2. Aggiungere un cubo alla scena. Nella finestra **Casella degli strumenti**, in **Forme**, selezionare **Cubo** e spostarlo nell'area di progettazione.

3. Passare alla selezione della faccia. Nella barra degli strumenti dell'editor dei modelli scegliere **Seleziona icona**.

4. Suddividere la parte superiore del cubo. In modalità di selezione icona scegliere una volta il cubo per attivarlo per la selezione, quindi scegliere la parte superiore del cubo per selezionare la faccia superiore. Nella barra degli strumenti dell'editor dei modelli scegliere **Suddividi faccia**. In questo modo vengono aggiunti nuovi vertici alla parte superiore del cubo che la dividono in quattro parti uguali.

    ![La parte superiore del cubo è stata suddivisa](../designers/media/gfx_model_demo_house_subdiv.png)

5. Estrudere due lati adiacenti del cubo, ad esempio i lati frontale e destro. In modalità di selezione icona, scegliere una volta il cubo per attivarlo per la selezione, quindi scegliere un lato del cubo. Tenendo premuto **CTRL**, scegliere un altro lato del cubo adiacente al lato selezionato per primo e nella barra degli strumenti dell'editor dei modelli scegliere **Estrudi faccia**.

    ![I lati del cubo sono stati estrusi](../designers/media/gfx_model_demo_house_extrude.png)

6. Estendere una delle estrusioni. Scegliere una delle facce appena estruse e nella barra degli strumenti dell'editor dei modelli scegliere lo strumento **Traslazione** e spostare il manipolatore della traslazione nella stessa direzione dell'estrusione.

    ![Una lato del cubo è stato ulteriormente estruso](../designers/media/gfx_model_demo_house_extend.png)

7. Eseguire la triangolazione del modello. Sulla barra degli strumenti dell'editor dei modelli **scegliere Strumenti**  >    >  **avanzati Triangolazione.**

8. Creare il tetto della casa. Passare alla modalità di selezione bordo scegliendo **Seleziona bordo** nella barra degli strumenti dell'editor dei modelli e quindi scegliere il cubo per attivarlo. Durante la selezione dei bordi visualizzati qui, tenere premuto **CTRL**:

    ![Bordi che formeranno il picco del tetto](../designers/media/gfx_model_demo_house_edges.png)

    Una volta selezionati i bordi, nella barra degli strumenti dell'editor dei modelli scegliere lo strumento **Traslazione** e spostare il manipolatore della traslazione verso l'alto per creare il tetto della casa.

   Il modello semplificato della casa è completato. Di seguito viene nuovamente mostrato il modello finale a cui è stata applicata l'ombreggiatura semplice:

   ![Modello completato della casa semplificata](../designers/media/gfx_model_demo_house_final.png)

   Come passaggio successivo, è possibile applicare uno shader a questo modello 3D. Per informazioni, [vedere Procedura: Applicare uno shader a un modello 3D.](../designers/how-to-apply-a-shader-to-a-3-d-model.md)

## <a name="see-also"></a>Vedi anche

- [Procedura: Modellare il terreno 3D](../designers/how-to-model-3-d-terrain.md)
- [Editor dei modelli](../designers/model-editor.md)
- [Finestra di progettazione shader](../designers/shader-designer.md)
