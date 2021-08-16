---
title: Animare oggetti in una finestra di progettazione XAML
titleSuffix: Blend for Visual Studio
description: Informazioni su come creare un'animazione in Blend per Visual Studio usando uno storyboard con una sequenza temporale e fotogrammi chiave per animare un oggetto in finestra di progettazione XAML.
ms.custom: SEO-VS-2020
ms.date: 07/31/2019
ms.topic: how-to
ms.assetid: fb88fa26-e835-47f5-9771-2f279441c83c
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xaml-tools
ms.openlocfilehash: da206cedbe2cf14be1fc6bcd2d8f1dd1cd154524767ed9b33ddb69e392599053
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121393466"
---
# <a name="animate-objects-in-xaml-designer"></a>Animare oggetti in una finestra di progettazione XAML

Blend per Visual Studio consente di creare facilmente brevi animazioni che spostano gli oggetti o li visualizzano in dissolvenza in entrata e in uscita, ad esempio.

Per creare un'animazione è necessario uno *storyboard*. Uno storyboard contiene uno o più *sequenze temporali*. Impostare i *fotogrammi chiave* in una sequenza temporale per contrassegnare le modifiche alle proprietà. Quando poi si esegue l'animazione, Blend per Visual Studio interpola le modifiche alle proprietà nel periodo di tempo indicato, garantendo in tal modo una transizione graduale. È possibile aggiungere un'animazione a qualsiasi proprietà che appartiene a un oggetto, anche quelle non visive.

Le immagini seguenti mostrano uno storyboard denominato **Storyboard1**. La sequenza temporale contiene fotogrammi chiave che indicano le posizioni X e Y di un rettangolo. Quando si esegue questa animazione, il rettangolo si sposta da una posizione a un altro in modo graduale.

![Storyboard per l'animazione in Blend per Visual Studio](media/storyboard-timeline.png)

## <a name="create-an-animation"></a>Creare un'animazione

1. Per creare uno storyboard, selezionare il pulsante **Opzioni storyboard** nella finestra **Oggetti e sequenza temporale**, quindi selezionare **Nuovo**.

   ![Aggiungere uno storyboard in Blend per Visual Studio](media/new-storyboard.png)

2. Nella finestra di dialogo **Crea risorsa di storyboard** immettere un nome per lo storyboard.

3. Nel riquadro **Asset** in visualizzazione Progettazione aggiungere un rettangolo sul lato inferiore sinistro della pagina.

   ![Rettangolo nel riquadro Asset della finestra di progettazione XAML](media/add-rectangle.PNG)

4. Nella finestra **Oggetti e sequenza temporale** spostare il puntatore temporale giallo su **3** secondi.

   ![Indicatore temporale nella sequenza temporale](media/timeline-indicator.PNG)

5. Nella visualizzazione Progettazione della pagina trascinare il rettangolo sul lato destro della pagina.

6. Scegliere **Riproduci** e osservare il rettangolo spostarsi dal lato sinistro al lato destro della pagina.

Provare ad apportate altre modifiche al rettangolo in altri punti della sequenza temporale. Ad esempio, è possibile cambiare il colore di riempimento o capovolgere l'orientamento nella finestra Proprietà.

## <a name="see-also"></a>Vedi anche

- [Creare un'interfaccia utente usando Blend per Visual Studio](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md)
