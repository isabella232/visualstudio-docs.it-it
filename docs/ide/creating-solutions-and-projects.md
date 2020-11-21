---
title: Creare soluzioni e progetti
description: Informazioni sulla differenza tra soluzioni e progetti e su come usarli in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/06/2018
ms.topic: how-to
f1_keywords:
- vs.openprojectfromweb
- VS.ToolsOptionsPages.Projects.General
- SolutionItemsProject
helpviewer_keywords:
- solutions [Visual Studio], creating
- projects [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7bd893c06da9bc2c2c8d95fc4c085affa815edd2
ms.sourcegitcommit: 66cda27b63c9b55782b1db223a6dbda9f8cabe13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2020
ms.locfileid: "95006445"
---
# <a name="create-solutions-and-projects"></a>Creare soluzioni e progetti

I *progetti* contengono gli elementi necessari per compilare l'app in Visual Studio, ad esempio file di codice sorgente, bitmap, icone e riferimenti a componenti e servizi. Quando si crea un nuovo progetto, Visual Studio crea una *soluzione* per ospitarlo. Se necessario è quindi possibile aggiungere altri progetti nuovi o esistenti alla soluzione. Le soluzioni possono anche contenere file non connessi ad alcun progetto specifico.

![Gerarchia soluzione/progetto](./media/vside-proj-soln.png)

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Creare progetti in Visual Studio per Mac](/visualstudio/mac/create-new-projects).

È possibile visualizzare le soluzioni e i progetti in una finestra degli strumenti denominata **Esplora soluzioni**. La schermata seguente visualizza un esempio di soluzione in **Esplora soluzioni** (**BikeSharing.Xamarin-UWP**) contenente due progetti: **BikeSharing.Clients.Core** e **BikeSharing.Clients.Windows**. Ogni progetto contiene più file, cartelle e riferimenti. Il nome del progetto in grassetto indica il *progetto di avvio*, ovvero il progetto che viene avviato quando si esegue l'app. È possibile specificare quale progetto è il progetto di avvio.

![Esplora soluzioni con progetti](./media/vside-solution-explorer-projects.png)

È possibile creare autonomamente un progetto aggiungendo i file necessari. In alternativa Visual Studio offre una selezione di modelli di progetto per semplificare le fasi iniziali. Se si usa un modello è possibile ottenere un progetto con tutti gli elementi essenziali per il tipo di progetto scelto e rinominare i file o aggiungere codice nuovo o esistente e altre risorse in base alle esigenze.

In ogni caso non è obbligatorio usare le soluzioni e i progetti per sviluppare app in Visual Studio. È possibile aprire direttamente codice clonato da Git o scaricato da un'altra origine. Per altre informazioni, vedere [Sviluppare codice in Visual Studio senza progetti o soluzioni](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="create-a-project-from-a-project-template"></a>Creare un progetto da un modello di progetto

Per informazioni sulla creazione di un nuovo progetto da un modello, vedere [Creare un nuovo progetto in Visual Studio](create-new-project.md).

## <a name="create-a-project-from-existing-code-files"></a>Creare un progetto da file di codice esistenti

Se è presente una raccolta di file di origine di codice è possibile aggiungerli facilmente a un progetto.

1. Dal menu scegliere **file**  >  **nuovo**  >  **progetto da codice esistente**.

1. In **Creazione guidata nuovo progetto da file di codice esistenti** scegliere il tipo di progetto desiderato nella casella di riepilogo a discesa **Specificare il tipo di progetto che si vuole creare** e quindi scegliere **Avanti**.

1. Nella procedura guidata, passare al percorso dei file e immettere un nome per il nuovo progetto nella casella **Nome**. Al termine scegliere il pulsante **Fine**.

> [!NOTE]
> Questa opzione risulta più adatta per raccolte di file relativamente semplici. Attualmente sono supportati solo i tipi di progetto C++, Apache Cordova, Visual Basic e C#.

## <a name="add-files-to-a-solution"></a>Aggiungere file a una soluzione

Se è presente un file che può essere usato per più progetti, ad esempio un file Leggimi per la soluzione o altri file che appartengono al livello della soluzione più che a un progetto specifico, è possibile aggiungerli alla soluzione stessa. Per aggiungere un elemento a una soluzione fare clic con il pulsante destro del mouse sul nodo della soluzione in **Esplora soluzioni** e scegliere **Aggiungi** > **Nuovo elemento** o **Aggiungi** > **Elemento esistente**.

## <a name="create-a-net-project-that-targets-a-specific-version-of-the-net-framework"></a>Creare un progetto .NET che usa una specifica versione di .NET Framework

Quando si crea un progetto .NET Framework è possibile indicare la versione specifica di .NET Framework che si vuole usare nel progetto. Quando invece si crea un progetto .NET Core, non si specifica una versione del framework.

::: moniker range="vs-2017"

Per specificare una versione di .NET Framework, scegliere il menu a discesa **Framework** nella finestra di dialogo **nuovo progetto** .

![Elenco a discesa Framework nella finestra di dialogo Nuovo progetto](./media/vside-newproject-framework.png)

> [!NOTE]
> Per l'accesso alle versioni di .NET Framework precedenti a .NET Framework 4 è necessario che nel computer sia installato .NET Framework 3.5.

::: moniker-end

::: moniker range=">=vs-2019"

Per specificare una versione di .NET Framework, scegliere il menu a discesa **Framework** nella pagina **Crea un nuovo progetto** .

![Selettore Framework nella configurazione di un nuovo progetto](media/vs-2019/configure-new-project-framework.png)

::: moniker-end

## <a name="create-empty-solutions"></a>Creare soluzioni vuote

È anche possibile creare soluzioni vuote che non includono alcun progetto. Questa opzione può risultare preferibile quando si vuole creare da zero la soluzione e i progetti.

### <a name="to-create-an-empty-solution"></a>Per creare una soluzione vuota

1. Sulla barra dei menu scegliere **file**  >  **nuovo**  >  **progetto**.

::: moniker range="vs-2017"

2. Nel riquadro a sinistra (**Modelli**) scegliere **Altri tipi di progetto** > **Soluzioni di Visual Studio** nell'elenco espanso.

3. Nel riquadro centrale scegliere **Soluzione vuota**.

4. Immettere i valori **Nome** e **Percorso** per la soluzione e quindi scegliere **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

2. Nella casella di ricerca nella pagina **Crea un nuovo progetto** digitare **soluzione**.

3. Selezionare il modello **Soluzione vuota** e quindi fare clic su **Avanti**.

4. Immettere i valori **Nome** e **Percorso** per la soluzione e quindi scegliere **Crea**.

::: moniker-end

Dopo aver creato una soluzione vuota, è possibile aggiungervi progetti o elementi nuovi o esistenti scegliendo **Aggiungi nuovo elemento** o **Aggiungi elemento esistente** nel menu **Progetto**.

Come detto in precedenza, è anche possibile aprire file di codice senza usare un progetto o una soluzione. Per altre informazioni su questa modalità di sviluppo di codice, vedere [Sviluppare codice in Visual Studio senza progetti o soluzioni](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

::: moniker range="vs-2017"

## <a name="create-a-temporary-project"></a>Creare un progetto temporaneo

(solo C# e Visual Basic)

Se si crea un progetto basato su .NET senza specificare un percorso su disco, il progetto è temporaneo. I progetti temporanei consentono di acquisire familiarità con i progetti .NET. In qualsiasi momento mentre si lavora con il progetto temporaneo è possibile scegliere di salvarlo o rimuoverlo.

Per creare un progetto temporaneo, passare prima a **strumenti**  >  **Opzioni**  >  **progetti e soluzioni**  >  **generale** e deselezionare la casella di controllo **Salva nuovi progetti al momento della creazione** . Aprire la finestra di dialogo **Nuovo progetto** come di consueto.

::: moniker-end

## <a name="delete-a-solution-project-or-item"></a>Eliminare una soluzione, un progetto o un elemento

È possibile eliminare definitivamente le soluzioni e il relativo contenuto, ma questa operazione non può essere eseguita con l'IDE Visual Studio. Quando si eliminano elementi all'interno di Visual Studio, questi vengono rimossi solo dalla soluzione o dal progetto corrente. Per eliminare definitivamente una soluzione o un altro componente dal sistema usare Esplora File per eliminare la cartella che contiene i file della soluzione con estensione *sln* e *suo*. Prima di eliminare definitivamente una soluzione è tuttavia consigliabile eseguire il backup dei progetti o dei file, che potrebbero tornare utili in futuro.

> [!NOTE]
> Il file con estensione *suo* è un file nascosto che non viene visualizzato nelle impostazioni predefinite di Esplora file. Per visualizzare i file nascosti, nel menu **Visualizza** di Esplora file selezionare la casella di controllo **Elementi nascosti**.

### <a name="permanently-delete-a-solution"></a>Eliminare una soluzione in modo permanente

1. In **Esplora soluzioni** scegliere **Apri cartella in Esplora file** dal menu di scelta rapida della soluzione da eliminare.

1. In Esplora file spostarsi in alto di un livello.

1. Scegliere la cartella contenente la soluzione e quindi premere **Canc**.

## <a name="see-also"></a>Vedi anche

- [Soluzioni e progetti](../ide/solutions-and-projects-in-visual-studio.md)
- [Repository open source Microsoft su GitHub](https://github.com/Microsoft)
- [Esempi di codice per sviluppatori](https://code.msdn.microsoft.com/)
- [Creare progetti (Visual Studio per Mac)](/visualstudio/mac/create-new-projects)
