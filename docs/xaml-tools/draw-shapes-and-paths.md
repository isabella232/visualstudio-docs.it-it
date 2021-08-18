---
title: Disegnare forme e tracciati
description: Usare le funzionalità del finestra di progettazione XAML in Blend per Visual Studio tracciati e forme, modificarli e combinarli.
ms.custom: SEO-VS-2020
titleSuffix: Blend for Visual Studio
ms.date: 09/22/2020
ms.topic: conceptual
ms.assetid: d5378c59-e2e5-49f0-91f1-aa82d984a33c
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xaml-tools
ms.workload:
- multiple
ms.openlocfilehash: f534d1917e6533c7a03e313f29f3a792dd545aee
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122136573"
---
# <a name="draw-shapes-and-paths"></a>Disegnare forme e tracciati

Nella finestra di progettazione XAML la parola *forma* indica esattamente una forma. Ad esempio: un rettangolo, un cerchio o un'ellissi. Un *tracciato* è una versione più flessibile di una forma. È possibile ad esempio modificarne la forma o combinarli per creare nuove forme.

Le forme e i tracciati usano la grafica vettoriale per una scalabilità ottimale negli schermi ad alta risoluzione.

## <a name="draw-a-shape"></a>Disegnare una forma

Trovare le forme nella finestra **Asset**.

:::image type="content" source="media/blend-shapes.png" alt-text="Screenshot della categoria Forme della finestra Asset in Blend per Visual Studio":::

Trascinare la forma da usare nella tavola da disegno. Usare quindi i quadratini sulla forma per ridimensionarla, ruotarla, spostarla o inclinarla.

![Selettori](../designers/media/84261e83-3091-4490-ab58-4218b188439e.png)

## <a name="draw-a-path"></a>Disegnare un tracciato

Un tracciato è costituito da una serie di linee e curve collegate. Usare un tracciato per creare forme interessanti non disponibili nella finestra **Asset**.

È possibile disegnare un tracciato usando una riga, una penna o una matita. Questi strumenti sono disponibili nella finestra **Strumenti**.

### <a name="draw-a-straight-line"></a>Disegnare una linea retta

Usare lo strumento **Penna** oppure lo strumento **Linea**.

**Uso dello strumento Penna**

Nella tavola da disegno fare clic una volta per definire il punto di inizio, quindi fare di nuovo clic per definire la fine della linea.

**Uso dello strumento Linea**

Nella tavola da disegno trascinare il puntatore dal punto in cui si vuole che abbia inizio la riga e quindi rilasciare il puntatore nel punto in cui si vuole che termini la linea.

### <a name="draw-a-curve"></a>Disegnare una curva

Usare lo strumento **Penna**.

Nella tavola da disegno fare clic una volta per definire il punto di inizio di una linea, quindi fare clic e trascinare il puntatore per creare la curva desiderata.

Per chiudere il tracciato, fare clic sul primo punto della linea.

### <a name="change-the-shape-of-a-curve"></a>Cambiare la forma di una curva

Usare lo strumento **Selezione diretta**.

Fare clic sulla forma, quindi trascinare qualsiasi punto della forma per modificare le forme della curva.

### <a name="draw-a-free-form-path"></a>Disegnare un tracciato a mano libera

Usare lo strumento **Matita**.

Nella tavola da disegno disegnare un tracciato a mano libera, proprio come se si usasse una vera matita.

### <a name="remove-part-of-a-path"></a>Eliminare una parte di un tracciato

Usare lo strumento **Selezione diretta**.

Selezionare il tracciato contenente il segmento da eliminare, quindi fare clic su **Elimina** .

### <a name="remove-a-point-in-a-path"></a>Rimuovere un punto da un tracciato

Usare lo strumento **Selezione** per selezionare il tracciato. Usare quindi lo strumento **Penna** per fare clic sul punto da rimuovere.

### <a name="add-a-point-to-a-path"></a>Aggiungere un punto a un tracciato

Usare lo strumento **Selezione** per selezionare il tracciato. Usare lo strumento **Penna** per fare clic in un punto qualsiasi del tracciato in cui si vuole aggiungere il punto.

## <a name="convert-a-shape-to-a-path"></a>Convertire una forma in un tracciato

Per modificare una forma in modo analogo alla modifica di un tracciato, convertire la forma in tracciato. Selezionare la forma e quindi selezionare  >  **Formatta**  >  **percorso Converti in tracciato**.

**Guardare un breve video:** ![ Configurare le funzionalità installate ](../designers/media/bldadminconsoleinitialconfigicon.png) [Uso dei tracciati: convertire una forma in un tracciato](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=147).

> [!NOTE]
> **Converti in tracciato** non è attualmente disponibile per le app UWP con `TargetPlatformVersion` minima 10.0.16299.0 o successiva.

## <a name="combine-paths"></a>Combinare tracciati

È possibile combinare forme e tracciati in un unico tracciato.

![Combinare tracciati](../designers/media/2df17a5d-a338-4ef4-96c5-dae51cc1ca8a.png)

|Numero|Azione|
|-|-|
|![Due forme prima della combinazione](../designers/media/b1_1.png)|Due forme prima della combinazione|
|![Unisci](../designers/media/b1_2.png)|Unisci|
|![Divisione](../designers/media/b1_3.png)|Divisione|
|![Intersect](../designers/media/b1_4.png)|Intersect|
|![Escludi sovrapposizione](../designers/media/b1_5.png)|Escludi sovrapposizione|
|![Sottrazione](../designers/media/b1_6.png)|Sottrazione|

**Guardare un breve video:** ![ Configurare le funzionalità installate ](../designers/media/bldadminconsoleinitialconfigicon.png) [Uso dei percorsi: Combina percorsi](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=195).

## <a name="create-a-compound-path"></a>Creare un tracciato composto

Quando si crea un tracciato composto, eventuali parti del tracciato che si intersecano vengono sottratte dal risultato e il tracciato risultante assume le proprietà visive del percorso situato più in basso.

È possibile separare un tracciato composto in qualsiasi momento dopo averlo creato.

![Interrompere un tracciato composto](../designers/media/2157a8aa-d9a7-4de4-8de5-b10d28f08a84.png)

**Guardare un breve video:** ![ Configurare le funzionalità installate ](../designers/media/bldadminconsoleinitialconfigicon.png) [Uso dei percorsi: Creare un percorso composto](https://www.youtube.com/watch?v=Io5bC0-nH6Q).

## <a name="create-a-clipping-path"></a>Creare un tracciato di ritaglio

Un tracciato di ritaglio è un tracciato o una forma applicato a un altro oggetto, in modo da nascondere le parti dell'oggetto mascherato esterne al tracciato di ritaglio.

![Tracciato di ritaglio](../designers/media/22471e98-a841-4f39-a3ef-36090cf5a625.png)

**Guardare un breve video:** ![ Configurare le funzionalità installate ](../designers/media/bldadminconsoleinitialconfigicon.png) [Uso dei tracciati: creare un tracciato di ritaglio.](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=232)
