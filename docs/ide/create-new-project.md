---
title: Creare un nuovo progetto
description: Informazioni su come creare un nuovo progetto in Visual Studio.
ms.custom: SEO-VS-2020, contperf-fy21q2
ms.date: 12/17/2020
ms.topic: how-to
f1_keywords:
- vs.newproject
helpviewer_keywords:
- projects [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cd8b6cb4819ae13b526eb5106bc7de3919d1a74f
ms.sourcegitcommit: c558d8a0f02ed2c932c8d6f70756d8d2cedb10b3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/18/2020
ms.locfileid: "97683981"
---
# <a name="create-a-new-project-in-visual-studio"></a>Creare un nuovo progetto in Visual Studio

In questo articolo verrà illustrato come creare rapidamente un nuovo progetto in Visual Studio.

::: moniker range="vs-2017"

## <a name="open-the-new-project-dialog"></a>Aprire la finestra di dialogo Nuovo progetto

Per creare un nuovo progetto in Visual Studio 2017 esistono più metodi. Nella pagina iniziale, è possibile digitare il nome di un modello di progetto nella casella **Cerca modelli di progetto** o selezionare il collegamento **Crea nuovo progetto** per aprire la finestra di dialogo **nuovo progetto** . A parte la pagina iniziale, è anche possibile selezionare **file**  >  **nuovo**  >  **progetto** nella barra dei menu o fare clic sul pulsante **nuovo progetto** sulla barra degli strumenti.

![Pagina iniziale e File > Nuovo > Progetto](./media/vside-newproject1.png)

## <a name="select-a-template-type"></a>Selezionare un tipo di modello

Nella finestra di dialogo **Nuovo progetto** i modelli di progetto disponibili vengono visualizzati in un elenco sotto la categoria **Modelli**. I modelli sono organizzati per linguaggio di programmazione e tipo di progetto, ad esempio Visual C#, JavaScript e Azure Data Lake.

![Finestra di dialogo Nuovo progetto](./media/vside-newproject-templates-list.png)

> [!NOTE]
> L'elenco delle lingue disponibili e i modelli di progetto visualizzati dipendono dalla versione di Visual Studio in esecuzione e dai carichi di lavoro installati. Per informazioni su come installare altri carichi di lavoro, vedere [Modificare Visual Studio aggiungendo o rimuovendo carichi di lavoro e componenti](../install/modify-visual-studio.md).

Visualizzare l'elenco dei modelli per il linguaggio di programmazione che si vuole usare facendo clic sul triangolo accanto al nome del linguaggio e quindi scegliendo una categoria di progetto, ad esempio Windows Desktop.

L'immagine seguente illustra i modelli di progetto disponibili per i progetti .NET Core di Visual C#:

![Modelli di progetto](./media/new-project-dialog-net-core.png)

## <a name="configure-your-project"></a>Configurare il progetto

Immettere il nome del nuovo progetto nella casella **Nome**. È possibile salvare il progetto nel percorso predefinito nel computer oppure fare clic sul pulsante **Sfoglia** per trovare un altro percorso. È anche possibile selezionare un nome di soluzione o aggiungere il nuovo progetto a un repository git selezionando **Aggiungi al controllo del codice sorgente**.

Fare clic su **OK** per creare la soluzione e il progetto.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="open-the-create-a-new-project-page"></a>Aprire la pagina Crea un nuovo progetto

Per creare un nuovo progetto in Visual Studio 2019 esistono più metodi. Quando si apre Visual Studio per la prima volta, viene visualizzata la finestra di avvio e da qui è possibile selezionare **Crea un nuovo progetto**.

![Creare un nuovo progetto dalla finestra di avvio in Visual Studio 2019](media/vs-2019/start-window-create-new-project.png)

Se l'ambiente di sviluppo di Visual Studio è già aperto, per creare un nuovo progetto è possibile scegliere **File** > **Nuovo** > **Progetto** sulla barra dei menu o fare clic sul pulsante **Nuovo progetto** sulla barra degli strumenti.

![Pulsante Nuovo progetto in Visual Studio 2019](media/vs-2019/new-project-button.png)

## <a name="select-a-template-type"></a>Selezionare un tipo di modello

Sul lato sinistro della pagina **Crea un nuovo progetto** viene visualizzato l'elenco dei modelli selezionati di recente. I modelli sono ordinati a partire da quello *usato più di recente*.

Se non si intende eseguire una selezione tra i modelli usati di recente, è possibile filtrare tutti i modelli di progetto disponibili per **Linguaggio**, ad esempio C# o C++, **Piattaforma**, ad esempio Windows o Azure e **Tipo di progetto**, ad esempio Desktop o Web. È anche possibile immettere testo nella casella di ricerca, ad esempio **asp.net**, per filtrare ulteriormente i modelli.

![Filtri per i modelli di progetto in Visual Studio 2019](media/vs-2019/create-new-project-filters.png)

I tag visualizzati sotto ogni modello corrispondono ai tre filtri a discesa (Linguaggio, Piattaforma e Tipo di progetto).

> [!TIP]
> Se non viene visualizzato il modello che si sta cercando, potrebbe mancare un carico di lavoro per Visual Studio. Per installare carichi di lavoro aggiuntivi, ad esempio **Sviluppo di Azure** o **Sviluppo di applicazioni per dispositivi mobili con .NET**, fare clic sul collegamento **Installa altri strumenti e funzionalità** per aprire il Programma di installazione di Visual Studio. Da qui, selezionare i carichi di lavoro che si vuole installare e quindi fare clic su **modifica**. Dopo questa operazione saranno disponibili modelli di progetto aggiuntivi da cui scegliere.
>
> ![Installare altri strumenti e funzionalità collegamento in Visual Studio 2019](media/vs-2019/install-more-tools-features.png)

Selezionare un modello e quindi fare clic su **Avanti**.

## <a name="configure-your-project"></a>Configurare il progetto

Nella pagina **Configura nuovo progetto** sono disponibili le opzioni per assegnare un nome al progetto (e alla soluzione), selezionare un percorso su disco e selezionare una versione del Framework (se applicabile al modello scelto).

![Configurare la pagina del nuovo progetto in Visual Studio 2019](media/vs-2019/configure-new-project.png)

> [!NOTE]
> Se si crea un nuovo progetto mentre in Visual Studio è già aperto un progetto o una soluzione, è disponibile un'opzione di configurazione aggiuntiva. È possibile scegliere di creare una nuova soluzione o di aggiungere il nuovo progetto alla soluzione già aperta.
>
> ![Crea nuova soluzione o Aggiungi alla soluzione esistente in Visual Studio 2019](media/vs-2019/configure-new-project-solution.png)

Fare clic su **Crea** per creare il nuovo progetto.

::: moniker-end

## <a name="add-additional-projects-to-a-solution"></a>Aggiungere altri progetti a una soluzione

Se si desidera aggiungere un progetto aggiuntivo a una soluzione, fare clic con il pulsante destro del mouse sul nodo della soluzione in **Esplora soluzioni** e scegliere **Aggiungi**  >  **nuovo progetto**.

> [!TIP]
> Per un esempio di progetto e di soluzione creato da zero, completate con istruzioni dettagliate e codice di esempio, vedere [Introduzione a progetti e soluzioni](../get-started/tutorial-projects-solutions.md).

## <a name="see-also"></a>Vedere anche

- [Usare soluzioni e progetti](creating-solutions-and-projects.md)
