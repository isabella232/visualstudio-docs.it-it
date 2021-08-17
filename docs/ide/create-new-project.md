---
title: Creare un nuovo progetto
description: Informazioni su come creare un nuovo progetto in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 12/23/2020
ms.topic: how-to
f1_keywords:
- vs.newproject
helpviewer_keywords:
- projects [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 8f885922e5b383d81d1d7c31faff43e569dc6732
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122109539"
---
# <a name="create-a-new-project-in-visual-studio"></a>Creare un nuovo progetto in Visual Studio

Questo articolo illustra come creare rapidamente un nuovo progetto in Visual Studio da un modello.

::: moniker range="vs-2017"

## <a name="open-the-new-project-dialog"></a>Aprire la finestra di dialogo Nuovo progetto

Per creare un nuovo progetto in Visual Studio 2017 esistono più metodi. Nella pagina Iniziale è possibile digitare il nome di  un modello di  progetto nella casella Cerca modelli di progetto oppure selezionare il collegamento Crea nuovo progetto per aprire la finestra di **dialogo Project** nuovo progetto. Oltre alla pagina Iniziale, è anche possibile selezionare File New Project (Nuovo file) sulla barra dei menu o fare clic sul pulsante  >    >   New **Project (Nuovo** Project) sulla barra degli strumenti.

![Screenshot della barra dei menu in Visual Studio con le opzioni > Nuovo > Project selezionate.](./media/vside-newproject1.png)

## <a name="select-a-template-type"></a>Selezionare un tipo di modello

Nella finestra di dialogo **Nuovo progetto** i modelli di progetto disponibili vengono visualizzati in un elenco sotto la categoria **Modelli**. I modelli sono organizzati per linguaggio di programmazione e tipo di progetto, ad esempio Visual C#, JavaScript e Azure Data Lake.

![Screenshot della finestra di dialogo Project nuova versione che mostra un elenco di modelli installati.](./media/vside-newproject-templates-list.png)

> [!NOTE]
> L'elenco delle lingue disponibili e i modelli di progetto visualizzati dipendono dalla versione di Visual Studio in esecuzione e dai carichi di lavoro installati. Per informazioni su come installare altri carichi di lavoro, vedere [Modificare Visual Studio aggiungendo o rimuovendo carichi di lavoro e componenti](../install/modify-visual-studio.md).

Visualizzare l'elenco dei modelli per il linguaggio di programmazione che si vuole usare facendo clic sul triangolo accanto al nome del linguaggio e quindi scegliendo una categoria di progetto, ad esempio Windows Desktop.

L'immagine seguente illustra i modelli di progetto disponibili per i progetti .NET Core di Visual C#:

![Screenshot della finestra di dialogo Project nuovo progetto in cui sono elencati i modelli di progetto tra cui è possibile scegliere.](./media/new-project-dialog-net-core.png)

## <a name="configure-your-project"></a>Configurare il progetto

Immettere il nome del nuovo progetto nella casella **Nome**. È possibile salvare il progetto nel percorso predefinito nel computer oppure fare clic sul pulsante **Sfoglia** per trovare un altro percorso. È anche possibile selezionare un nome di soluzione o aggiungere il nuovo progetto a un repository Git (selezionando **Aggiungi al controllo del codice sorgente).**

Fare clic su **OK** per creare la soluzione e il progetto.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="open-the-create-a-new-project-page"></a>Aprire la pagina Crea un nuovo progetto

Per creare un nuovo progetto in Visual Studio 2019 esistono più metodi. Quando si apre per la Visual Studio, viene visualizzata la finestra iniziale e da qui è possibile selezionare **Crea un nuovo progetto.**

:::image type="content" source="media/vs-2019/start-window-create-new-project.png" alt-text="Screenshot della finestra di dialogo &quot;Crea un nuovo progetto&quot; dalla finestra iniziale Visual Studio 2019":::

Se l Visual Studio di sviluppo è già aperto, è possibile creare un nuovo progetto scegliendo  >    >  **Nuovo file Project** sulla barra dei menu. È anche possibile fare clic **sul pulsante Project** sulla barra degli strumenti oppure premere **CTRL** + **MAIUSC** + **N.**

:::image type="content" source="media/vs-2019/new-project-button.png" alt-text="Screenshot del pulsante Project 2019 in Visual Studio 2019.":::

## <a name="select-a-template-type"></a>Selezionare un tipo di modello

Sul lato sinistro della pagina **Crea un nuovo progetto** viene visualizzato l'elenco dei modelli selezionati di recente. I modelli sono ordinati a partire da quello *usato più di recente*.

Se non si intende eseguire una selezione tra i modelli usati di recente, è possibile filtrare tutti i modelli di progetto disponibili per **Linguaggio**, ad esempio C# o C++, **Piattaforma**, ad esempio Windows o Azure e **Tipo di progetto**, ad esempio Desktop o Web. È anche possibile immettere testo nella casella di ricerca, ad esempio **asp.net**, per filtrare ulteriormente i modelli.

:::image type="content" source="media/vs-2019/create-new-project-filters.png" alt-text="Screenshot dei filtri del modello di progetto in Visual Studio 2019.":::

I tag visualizzati sotto ogni modello corrispondono ai tre filtri a discesa (Linguaggio, Piattaforma e Tipo di progetto).

> [!TIP]
> Se il modello che si sta cercando non è visualizzato, potrebbe mancare un carico di lavoro per Visual Studio. Per installare carichi di lavoro aggiuntivi, ad esempio **Sviluppo di Azure** o **Sviluppo di applicazioni per dispositivi mobili con .NET**, fare clic sul collegamento **Installa altri strumenti e funzionalità** per aprire il Programma di installazione di Visual Studio. Da qui selezionare i carichi di lavoro da installare e quindi selezionare **Modifica.** Dopo questa operazione saranno disponibili modelli di progetto aggiuntivi da cui scegliere.
>
> :::image type="content" source="media/vs-2019/install-more-tools-features.png" alt-text="Screenshot del collegamento &quot;Installa altri strumenti e funzionalità&quot; in Visual Studio 2019.":::

Selezionare un modello e quindi fare clic su **Avanti**.

## <a name="configure-your-project"></a>Configurare il progetto

La **pagina Configura il nuovo** progetto include opzioni per assegnare un nome al progetto (e alla soluzione), selezionare un percorso su disco e selezionare una versione del framework (se applicabile al modello scelto).

:::image type="content" source="media/vs-2019/configure-new-project.png" alt-text="Screenshot della pagina &quot;Configura il nuovo progetto&quot; in Visual Studio 2019.":::

> [!NOTE]
> Se si crea un nuovo progetto mentre in Visual Studio è già aperto un progetto o una soluzione, è disponibile un'opzione di configurazione aggiuntiva. È possibile scegliere di creare una nuova soluzione o di aggiungere il nuovo progetto alla soluzione già aperta.
>
> :::image type="content" source="media/vs-2019/configure-new-project-solution.png" alt-text="Screenshot della finestra di dialogo &quot;Crea nuova soluzione&quot; o &quot;Aggiungi alla soluzione&quot; Visual Studio 2019.":::

Fare clic su **Crea** per creare il nuovo progetto.

::: moniker-end

## <a name="add-additional-projects-to-a-solution"></a>Aggiungere altri progetti a una soluzione

Se si vuole aggiungere un altro progetto a una soluzione, fare clic con il pulsante destro del mouse sul nodo della soluzione in **Esplora soluzioni** quindi  >  **scegliere Aggiungi nuovo Project**.

> [!TIP]
> Per un esempio di progetto e soluzione creati da zero, con istruzioni dettagliate e codice di esempio, vedere Introduzione a [progetti e soluzioni.](../get-started/tutorial-projects-solutions.md)

## <a name="see-also"></a>Vedi anche

- [Introduzione a progetti e soluzioni](../get-started/tutorial-projects-solutions.md)
- [Usare soluzioni e progetti](creating-solutions-and-projects.md)
- [Gestire le proprietà di progetti e soluzioni](managing-project-and-solution-properties.md)
- [Creare progetti (Visual Studio per Mac)](/visualstudio/mac/create-new-projects)
