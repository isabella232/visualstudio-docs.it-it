---
title: Animare oggetti in una finestra di progettazione XAML
titleSuffix: Blend for Visual Studio
ms.date: 07/31/2019
ms.topic: conceptual
ms.assetid: fb88fa26-e835-47f5-9771-2f279441c83c
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: ab5be23d2756c1afc38f5ea071fe10a621c5cf2e
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593048"
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

## <a name="see-also"></a>Vedere anche

- [Creare un'interfaccia utente usando Blend per Visual Studio](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md)
