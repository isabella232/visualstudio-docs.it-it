---
title: Creare progetti & soluzioni
description: Informazioni su come creare e usare Visual Studio soluzioni e progetti per archiviare gli elementi.
ms.custom: SEO-VS-2020, contperf-fy21q2
ms.date: 06/14/2021
ms.topic: how-to
f1_keywords:
- vs.openprojectfromweb
helpviewer_keywords:
- solutions [Visual Studio], creating
- projects [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f05a940787c2ab601b0b29db8ec5004c621a16b8
ms.sourcegitcommit: d856c46d78638be609e7045621ed1bd7521a6dcc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/16/2021
ms.locfileid: "114283840"
---
# <a name="create-work-with-and-delete-visual-studio-projects-and-solutions"></a>Creare, usare ed eliminare progetti Visual Studio soluzioni

In questo articolo si apprenderà come creare e usare Visual Studio da zero per archiviare gli elementi necessari per compilare le app.  Se non si ha familiarità con i progetti in Visual Studio, vedere questa panoramica di [Progetti e soluzioni](solutions-and-projects-in-visual-studio.md).  Per informazioni su come creare rapidamente un progetto da un modello, vedere [Creare un progetto da un modello](create-new-project.md).

I *progetti* contengono gli elementi necessari per compilare l'app in Visual Studio, ad esempio file di codice sorgente, bitmap, icone e riferimenti a componenti e servizi. Quando si crea un nuovo progetto, Visual Studio crea una *soluzione* per ospitarlo. Se necessario è quindi possibile aggiungere altri progetti nuovi o esistenti alla soluzione. È anche possibile creare [soluzioni vuote o vuote.](#create-empty-solutions) Le soluzioni possono anche contenere file non connessi ad alcun progetto specifico.

![Diagramma che mostra la gerarchia di soluzioni e progetti.](./media/vside-proj-soln.png)

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Creare progetti in Visual Studio per Mac](/visualstudio/mac/create-new-projects).

È possibile visualizzare le soluzioni e i progetti in una finestra degli strumenti denominata **Esplora soluzioni**. La schermata seguente visualizza un esempio di soluzione in **Esplora soluzioni** (**BikeSharing.Xamarin-UWP**) contenente due progetti: **BikeSharing.Clients.Core** e **BikeSharing.Clients.Windows**. Ogni progetto contiene più file, cartelle e riferimenti. Il nome del progetto in grassetto indica il *progetto di avvio*, ovvero il progetto che viene avviato quando si esegue l'app. È possibile specificare quale progetto è il progetto di avvio.

![Screenshot della Esplora soluzioni con due progetti.](./media/vside-solution-explorer-projects.png)

È possibile creare autonomamente un progetto aggiungendo i file necessari. In alternativa Visual Studio offre una selezione di modelli di progetto per semplificare le fasi iniziali. Se si usa un modello è possibile ottenere un progetto con tutti gli elementi essenziali per il tipo di progetto scelto e rinominare i file o aggiungere codice nuovo o esistente e altre risorse in base alle esigenze.

In ogni caso non è obbligatorio usare le soluzioni e i progetti per sviluppare app in Visual Studio. È possibile aprire direttamente codice clonato da Git o scaricato da un'altra origine. Per altre informazioni, vedere [Sviluppare codice in Visual Studio senza progetti o soluzioni](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="create-a-project-from-a-project-template"></a>Creare un progetto da un modello di progetto

Per informazioni su come selezionare un modello per creare un nuovo progetto, vedere [Creare un nuovo](create-new-project.md)progetto in Visual Studio . Per un esempio di un progetto e di una soluzione creati da zero, completi di istruzioni dettagliate e codice di esempio, vedere Introduzione a progetti [e soluzioni.](../get-started/tutorial-projects-solutions.md)

## <a name="create-a-project-from-existing-code-files"></a>Creare un progetto da file di codice esistenti

Se è presente una raccolta di file di origine di codice è possibile aggiungerli facilmente a un progetto.

1. Nel menu selezionare **File**  >  **nuovo Project** da codice  >  **esistente**.

1. Nella procedura **guidata** Crea Project da file di codice esistenti selezionare il tipo di progetto desiderato nella casella di riepilogo a discesa Quale tipo di progetto si vuole **creare?** e quindi selezionare il **pulsante** Avanti.

1. Nella procedura guidata, passare al percorso dei file e immettere un nome per il nuovo progetto nella casella **Nome**. Al termine, selezionare il **pulsante** Fine.

> [!NOTE]
> Questa opzione risulta più adatta per raccolte di file relativamente semplici. Attualmente sono supportati solo i tipi di progetto C++, Apache Cordova, Visual Basic e C#.

## <a name="add-files-to-a-solution"></a>Aggiungere file a una soluzione

Se è presente un file che può essere usato per più progetti, ad esempio un file Leggimi per la soluzione o altri file che appartengono al livello della soluzione più che a un progetto specifico, è possibile aggiungerli alla soluzione stessa. Per aggiungere un elemento a una soluzione, nel menu di scelta rapida (fare clic con il pulsante destro del mouse) del nodo della soluzione in Esplora soluzioni selezionare **Aggiungi** nuovo elemento o Aggiungi  >     >  **elemento esistente**.

> [!TIP]
> Un file di soluzione è una struttura per organizzare i progetti in Visual Studio. Contiene lo stato di queste informazioni in due file: un file *sln* (basato su testo, condiviso) e un file con estensione *suo* (binario, nascosto, opzioni di soluzione specifiche dell'utente). Di conseguenza, una soluzione non è un elemento che deve essere copiato e rinominato. è invece meglio creare una nuova soluzione e quindi aggiungerne elementi esistenti.

## <a name="create-a-net-project-that-targets-a-specific-version-of-the-net-framework"></a>Creare un progetto .NET che usa una specifica versione di .NET Framework

Quando si crea un progetto .NET Framework è possibile indicare la versione specifica di .NET Framework che si vuole usare nel progetto. Quando invece si crea un progetto .NET Core, non si specifica una versione del framework.

::: moniker range="vs-2017"

Per specificare una .NET Framework, selezionare il menu a discesa **Framework** nella finestra di **dialogo Project** nuova versione.

![Screenshot dell'elenco a discesa Framework nella finestra di dialogo Project finestra di dialogo.](./media/vside-newproject-framework.png)

> [!NOTE]
> Per l'accesso alle versioni di .NET Framework precedenti a .NET Framework 4 è necessario che nel computer sia installato .NET Framework 3.5.

::: moniker-end

::: moniker range=">=vs-2019"

Per specificare una .NET Framework, selezionare il menu a discesa **Framework** nella **pagina Crea un nuovo** progetto.

![Screenshot del selettore Framework nella finestra di dialogo "Configura nuovo progetto".](media/vs-2019/configure-new-project-framework.png)

::: moniker-end

## <a name="create-empty-solutions"></a>Creare soluzioni vuote

È anche possibile creare soluzioni vuote che non includono alcun progetto. Questa opzione può risultare preferibile quando si vuole creare da zero la soluzione e i progetti.

### <a name="to-create-an-empty-solution"></a>Per creare una soluzione vuota

1. Nella barra dei menu selezionare **File**  >  **nuovo**  >  **Project**.

::: moniker range="vs-2017"

2. Nel riquadro sinistro (**Modelli**) selezionare **Altri Project tipi** Visual Studio soluzioni > **nell'elenco** espanso.

3. Nel riquadro centrale selezionare **Soluzione vuota**.

4. Immettere **i** valori **nome e** percorso per la soluzione e quindi selezionare **OK.**

::: moniker-end

::: moniker range=">=vs-2019"

2. Nella casella di ricerca nella pagina **Crea un nuovo progetto** digitare **soluzione**.

3. Selezionare il modello **Soluzione vuota** e quindi fare clic su **Avanti**.

4. Immettere **i** valori **nome e** percorso per la soluzione e quindi selezionare **Crea**.

::: moniker-end

Dopo aver creato una soluzione vuota, è possibile aggiungervi progetti o elementi nuovi o esistenti scegliendo **Aggiungi nuovo elemento** o **Aggiungi elemento esistente** nel menu **Progetto**.

Come detto in precedenza, è anche possibile aprire file di codice senza usare un progetto o una soluzione. Per altre informazioni su questa modalità di sviluppo di codice, vedere [Sviluppare codice in Visual Studio senza progetti o soluzioni](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

::: moniker range="vs-2017"

## <a name="create-a-temporary-project"></a>Creare un progetto temporaneo

(solo C# e Visual Basic)

Se si crea un progetto basato su .NET senza specificare un percorso su disco, il progetto è temporaneo. I progetti temporanei consentono di acquisire familiarità con i progetti .NET. In qualsiasi momento mentre si lavora con il progetto temporaneo è possibile scegliere di salvarlo o rimuoverlo.

Per creare un progetto temporaneo, passare prima **a** Strumenti Opzioni Progetti e soluzioni Generali e deselezionare la casella di controllo Salva nuovi  >    >    >  progetti **al momento della** creazione. Aprire la finestra di dialogo **Nuovo progetto** come di consueto.

::: moniker-end

## <a name="delete-a-solution-project-or-item"></a>Eliminare una soluzione, un progetto o un elemento

È possibile usare il menu di scelta rapida per eliminare o rimuovere soluzioni, progetti o elementi in Visual Studio, ma questo li rimuove solo dalla soluzione o dal progetto corrente.

Per eliminare definitivamente una soluzione o altri componenti dal sistema, usare Esplora file **in** Windows per eliminare la cartella che contiene i file della soluzione *sln* e *suo.* Prima di eliminare una soluzione, è consigliabile eseguire il backup dei progetti e dei file nel caso in cui sia necessario.

> [!NOTE]
> Il file *suo* è un file nascosto che non viene visualizzato nelle impostazioni Esplora file predefinite. Per visualizzare i file nascosti, nel menu **Visualizza** di Esplora file selezionare la casella di controllo **Elementi nascosti**.

### <a name="permanently-delete-a-solution"></a>Eliminare una soluzione in modo permanente

È possibile accedere Esplora file in Windows usando Esplora soluzioni in Visual Studio. Ecco come.

1. In **Esplora soluzioni**, nel menu di scelta rapida della soluzione che si vuole eliminare fare clic con il pulsante destro del **mouse, selezionare Apri** cartella in Esplora file .

1. In Esplora file spostarsi in alto di un livello.

1. Selezionare la cartella che contiene la soluzione e quindi premere **CANC.**

## <a name="see-also"></a>Vedi anche

- [Introduzione a progetti e soluzioni](../get-started/tutorial-projects-solutions.md)
- [Gestire le proprietà di progetti e soluzioni](managing-project-and-solution-properties.md)
- [Soluzioni filtrate in Visual Studio](filtered-solutions.md)
- [Repository open source Microsoft su GitHub](https://github.com/Microsoft)
- [Esempi di codice per sviluppatori](https://code.msdn.microsoft.com/)
- [Risorse per la risoluzione Visual Studio errori dell'IDE](./reference/resources-for-troubleshooting-integrated-development-environment-errors.md)
