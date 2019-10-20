---
title: Creare un nuovo progetto
ms.date: 03/19/2019
ms.topic: conceptual
f1_keywords:
- vs.newproject
helpviewer_keywords:
- projects [Visual Studio], creating
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a35302e8f749563ab173e7be15e944f8462fdb18
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652657"
---
# <a name="create-a-new-project-in-visual-studio"></a>Creare un nuovo progetto in Visual Studio

::: moniker range="vs-2017"

## <a name="open-the-new-project-dialog"></a>Aprire la finestra di dialogo Nuovo progetto

Per creare un nuovo progetto in Visual Studio 2017 esistono più metodi. Nella pagina iniziale è possibile immettere il nome di un modello di progetto nella casella **Cerca modelli di progetto** o scegliere il collegamento **Crea nuovo progetto** per aprire la finestra di dialogo **Nuovo progetto**. Al di fuori della pagina iniziale, è anche possibile scegliere **File** > **Nuovo** > **Progetto** sulla barra dei menu o fare clic sul pulsante **Nuovo progetto** sulla barra degli strumenti.

![Pagina iniziale e File > Nuovo > Progetto](./media/vside-newproject1.png)

## <a name="select-a-template-type"></a>Selezionare un tipo di modello

Nella finestra di dialogo **Nuovo progetto** i modelli di progetto disponibili vengono visualizzati in un elenco sotto la categoria **Modelli**. I modelli sono organizzati per linguaggio di programmazione e tipo di progetto, ad esempio Visual C#, JavaScript e Azure Data Lake.

![Finestra di dialogo Nuovo progetto](./media/vside-newproject-templates-list.png)

> [!NOTE]
> L'elenco delle lingue disponibili e i modelli di progetto visualizzati dipendono dalla versione di Visual Studio in esecuzione e dai carichi di lavoro installati. Per informazioni su come installare altri carichi di lavoro, vedere [Modificare Visual Studio aggiungendo o rimuovendo carichi di lavoro e componenti](../install/modify-visual-studio.md).

Visualizzare l'elenco dei modelli per il linguaggio di programmazione che si vuole usare facendo clic sul triangolo accanto al nome del linguaggio e quindi scegliendo una categoria di progetto, ad esempio Windows Desktop.

L'immagine seguente illustra i modelli di progetto disponibili per i progetti .NET Core di Visual C#:

![Modelli di progetto](./media/new-project-dialog-net-core.png)

## <a name="configure-your-project"></a>Configurazione del progetto

Immettere il nome del nuovo progetto nella casella **Nome**. È possibile salvare il progetto nel percorso predefinito nel computer oppure fare clic sul pulsante **Sfoglia** per trovare un altro percorso. È anche possibile scegliere un nome di soluzione o aggiungere il nuovo progetto a un repository Git scegliendo **Aggiungi al controllo del codice sorgente**.

Fare clic su **OK** per creare la soluzione e il progetto.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="open-the-create-a-new-project-page"></a>Aprire la pagina Crea un nuovo progetto

Per creare un nuovo progetto in Visual Studio 2019 esistono più metodi. Quando si apre Visual Studio per la prima volta, viene visualizzata la finestra iniziale, da cui è possibile scegliere **Crea un nuovo progetto**.

![Creare un nuovo progetto dalla finestra iniziale in VS 2019](media/vs-2019/start-window-create-new-project.png)

Se l'ambiente di sviluppo di Visual Studio è già aperto, per creare un nuovo progetto è possibile scegliere **File** > **Nuovo** > **Progetto** sulla barra dei menu o fare clic sul pulsante **Nuovo progetto** sulla barra degli strumenti.

![Pulsante Nuovo progetto in Visual Studio 2019](media/vs-2019/new-project-button.png)

## <a name="select-a-template-type"></a>Selezionare un tipo di modello

Sul lato sinistro della pagina **Crea un nuovo progetto** viene visualizzato l'elenco dei modelli selezionati di recente. I modelli sono ordinati a partire da quello *usato più di recente*.

Se non si intende eseguire una selezione tra i modelli usati di recente, è possibile filtrare tutti i modelli di progetto disponibili per **Linguaggio**, ad esempio C# o C++, **Piattaforma**, ad esempio Windows o Azure e **Tipo di progetto**, ad esempio Desktop o Web. È anche possibile immettere testo nella casella di ricerca, ad esempio **asp.net**, per filtrare ulteriormente i modelli.

![Filtri per i modelli di progetto in Visual Studio 2019](media/vs-2019/create-new-project-filters.png)

I tag visualizzati sotto ogni modello corrispondono ai tre filtri a discesa (Linguaggio, Piattaforma e Tipo di progetto).

> [!TIP]
> Se il modello che si sta cercando non viene visualizzato, è possibile che manchi un carico di lavoro per Visual Studio. Per installare carichi di lavoro aggiuntivi, ad esempio **Sviluppo di Azure** o **Sviluppo di applicazioni per dispositivi mobili con .NET**, fare clic sul collegamento **Installa altri strumenti e funzionalità** per aprire il Programma di installazione di Visual Studio. All'interno di questo programma selezionare i carichi di lavoro da installare e quindi scegliere **Modifica**. Dopo questa operazione saranno disponibili modelli di progetto aggiuntivi da cui scegliere.
>
> ![Collegamento Installa altri strumenti e funzionalità in VS 2019](media/vs-2019/install-more-tools-features.png)

Selezionare un modello e quindi fare clic su **Avanti**.

## <a name="configure-your-project"></a>Configurazione del progetto

La pagina **Configura il nuovo progetto** contiene opzioni per l'assegnazione di un nome al progetto e alla soluzione, scegliere un percorso su disco e selezionare una versione del framework, se applicabile al modello scelto.

![Pagina Configura il nuovo progetto in VS 2019](media/vs-2019/configure-new-project.png)

> [!NOTE]
> Se si crea un nuovo progetto mentre in Visual Studio è già aperto un progetto o una soluzione, è disponibile un'opzione di configurazione aggiuntiva. È possibile scegliere di creare una nuova soluzione o di aggiungere il nuovo progetto alla soluzione già aperta.
>
> ![Creare una nuova soluzione o aggiungere il progetto alla soluzione esistente in VS 2019](media/vs-2019/configure-new-project-solution.png)

Fare clic su **Crea** per creare il nuovo progetto.

::: moniker-end

## <a name="add-additional-projects-to-a-solution"></a>Aggiungere altri progetti a una soluzione

Se si vuole aggiungere un altro progetto a una soluzione, fare clic con il pulsante destro del mouse sul nodo della soluzione in **Esplora soluzioni** e scegliere **Aggiungi** > **Nuovo progetto**.

## <a name="see-also"></a>Vedere anche

- [Creare soluzioni e progetti](creating-solutions-and-projects.md)
