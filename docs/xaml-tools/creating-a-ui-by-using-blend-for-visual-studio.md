---
title: Presentazione delle funzionalità di Blend per Visual Studio
titleSuffix: ''
description: Informazioni sull'interfaccia utente dell'area di lavoro e sulle funzionalità di Blend per Visual Studio, un componente per la progettazione di applicazioni Web e Windows basate su XAML.
ms.custom: SEO-VS-2020
ms.date: 07/31/2019
ms.topic: overview
f1_keywords:
- Blend.Start.Dev12
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xaml-tools
ms.workload:
- multiple
ms.openlocfilehash: 5d658ac48d2481f414fdef07906275f25b35479c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122092020"
---
# <a name="blend-for-visual-studio-overview"></a>Panoramica di Blend per Visual Studio

Blend per Visual Studio consente di progettare applicazioni Windows e Web basate su XAML. Offre la stessa esperienza di progettazione XAML di base disponibile in Visual Studio e aggiunge finestre di progettazione visive per attività avanzate, quali animazioni e comportamenti. Per un confronto tra Blend e Visual Studio, vedere [Progettare XAML in Visual Studio e Blend per Visual Studio](../xaml-tools/designing-xaml-in-visual-studio.md).

Blend per Visual Studio è un componente di Visual Studio. Per installare Blend, nel **programma di installazione di Visual Studio** scegliere il carico di lavoro **Sviluppo di app per la piattaforma UWP (Universal Windows Platform)** o **Sviluppo per desktop .NET**. Entrambi questi carichi di lavoro includono il componente Blend per Visual Studio.

![Componenti del carico di lavoro UWP](media/installer-uwp.png)&nbsp;&nbsp;&nbsp;&nbsp;![Componenti del carico di lavoro Sviluppo per desktop .NET](media/installer-dotnet-desktop.png)

Se non si ha familiarità con Blend per Visual Studio, dedicare alcuni minuti all'esame delle funzionalità specifiche dell'area di lavoro. In questo argomento è disponibile una breve panoramica.

## <a name="tools-panel"></a>Pannello Strumenti

È possibile usare il pannello **Strumenti** in Blend per Visual Studio per creare e modificare oggetti nell'applicazione. Il pannello **Strumenti** è visualizzato sul lato sinistro della finestra di progettazione XAML quando è aperto un file *XAML*.

Per creare oggetti, si seleziona lo strumento e si disegna sulla tavola da disegno con il mouse.

![Pannello Strumenti in Blend per Visual Studio](media/blend-tools-panel.png)

> [!TIP]
> Alcuni degli strumenti del pannello **Strumenti** presentano delle variazioni, ad esempio, anziché un rettangolo, è possibile scegliere un'ellisse o una linea. Per accedere a queste varianti, fare clic con il pulsante destro del mouse o fare clic e tenere premuto sullo strumento.
>
> ![Varianti dello strumento Forma in Blend per Visual Studio](media/blend-rectangle-tool-variations.png)

### <a name="selection-tools"></a>Strumenti di selezione

Selezionare oggetti e percorsi. Usare lo strumento **Selezione diretta** per selezionare gli oggetti annidati e i segmenti di percorso.

### <a name="view-tools"></a>Strumenti di visualizzazione

Consente di modificare la visualizzazione della tavola da disegno, ad esempio per la panoramica e lo zoom.

### <a name="brush-tools"></a>Strumento per i pennelli

Usare gli attributi visivi di un oggetto, ad esempio la trasformazione di un pennello o l'applicazione di una sfumatura.

### <a name="object-tools"></a>Strumenti per gli oggetti

Consente di disegnare gli oggetti più comuni sulla tavola da disegno, ad esempio tracciati, forme, pannelli di layout, testo e controlli.

### <a name="asset-tools"></a>Strumenti per gli asset

Consente di accedere alla finestra Asset e visualizzare l'ultimo asset usato nella libreria.

## <a name="assets-window"></a>Finestra Asset

La finestra **Asset** contiene tutti i controlli disponibili ed è simile alla **casella degli strumenti** di Visual Studio. Oltre ai controlli, nella finestra **Asset** è disponibile tutto ciò che può essere aggiunto alla tavola da disegno, inclusi gli stili, gli elementi multimediali, i comportamenti e gli effetti. Per aprire la finestra **Asset**, scegliere **Visualizza** > **Finestra Asset** oppure premere **CTRL**+**ALT**+**X**.

![Finestra Asset in Blend per Visual Studio](media/blend-assets-window.png)

- Immettere il testo nella casella **Cerca asset** per filtrare l'elenco di asset.
- Passare dalla visualizzazione Modalità griglia alla visualizzazione Modalità elenco degli asset usando i pulsanti in alto a destra.

## <a name="objects-and-timeline-window"></a>Finestra Oggetti e sequenza temporale

Usare questa finestra per organizzare gli oggetti nella tavola da disegno e, se si vuole, per animarli. Per aprire la finestra **Oggetti e sequenza temporale**, scegliere **Visualizza** > **Struttura documento**. Oltre alla funzionalità fornita nella finestra [Struttura documento](creating-a-ui-by-using-xaml-designer-in-visual-studio.md#document-outline-window) in Visual Studio, la finestra Oggetti e sequenza temporale in Blend per Visual Studio dispone di un'area di composizione della sequenza temporale a destra. Usare la sequenza temporale durante la creazione e la modifica di animazioni.

![Finestra Oggetti e sequenza temporale in modalità animazione](media/storyboard-timeline.png)

Usare i pulsanti correlati allo storyboard ![Pulsanti dello storyboard in Blend per Visual Studio](media/storyboard-buttons.png) per creare, eliminare, chiudere o selezionare uno storyboard. Usare l'area di composizione della sequenza temporale a destra per visualizzare la sequenza temporale e spostare i fotogrammi chiave.

Passare il puntatore del mouse su ogni pulsante della finestra per altre informazioni sulle funzionalità disponibili.

## <a name="see-also"></a>Vedi anche

- [Animare oggetti](../xaml-tools/animate-objects-in-xaml-designer.md)
- [Disegnare forme e tracciati](../xaml-tools/draw-shapes-and-paths.md)
- [Progettazione di XAML in Visual Studio e Blend per Visual Studio](../xaml-tools/designing-xaml-in-visual-studio.md)
