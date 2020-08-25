---
title: Creazione di modelli di progetto e di elemento personalizzati | Microsoft Docs
ms.date: 3/16/2019
ms.topic: overview
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eb6bcd63896a11f9ca1eabddddc17b3e52865e5b
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/25/2020
ms.locfileid: "88801256"
---
# <a name="create-custom-project-and-item-templates"></a>Creare modelli di progetto e di elemento personalizzati

Visual Studio SDK include modelli di progetto per la creazione di un modello di progetto personalizzato e di un modello di elemento personalizzato. Questi modelli includono alcune sostituzioni di parametro comuni e vengono compilate come file zip. Non vengono distribuiti automaticamente e non sono disponibili nell'istanza sperimentale. È necessario copiare il file ZIP generato nella directory dei modelli utente.

I modelli di creazione del modello consentono di includere i modelli in estensioni più grandi. In questo modo è possibile implementare il controllo della versione nei file di origine e compilare un gruppo di progetti modello in un unico pacchetto VSIX.

È anche possibile configurare un modello per l'installazione dei pacchetti NuGet. Per altre informazioni, vedere [pacchetti NuGet nei modelli di Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates).

Per gli scenari di creazione di modelli di base, è consigliabile usare l' **esportazione guidata modelli** , che restituisce un file compresso. Per ulteriori informazioni sulla creazione di modelli di base, vedere [creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md).

> [!NOTE]
> A partire da Visual Studio 2017, l'analisi dei modelli di progetto e di elemento personalizzati non verrà più eseguita. L'estensione deve invece fornire file manifesto del modello che descrivono il percorso di installazione di questi modelli. È possibile usare Visual Studio 2017 per aggiornare le estensioni VSIX. Se si distribuisce l'estensione utilizzando un file MSI, è necessario generare manualmente i file manifesto del modello. Per altre informazioni, vedere [aggiornamento di modelli di progetto e di elemento personalizzati per Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Lo schema del manifesto del modello è documentato in [riferimenti allo schema del manifesto del modello di Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="create-a-project-template"></a>Creare un modello di progetto

1. Creare un progetto di modello di progetto. È possibile trovare il modello di progetto nella finestra di dialogo **nuovo progetto** , cercando "modello di progetto" e selezionando la versione C# o Visual Basic.

     Il modello genera un file di classe, un'icona, un file con *estensione vstemplate* , un file di progetto modificabile denominato *ProjectTemplate. vbproj* o *ProjectTemplate. csproj*e alcuni file che vengono in genere generati da altri tipi di progetto, ad esempio un file *Resources. resx* , un file *AssemblyInfo* e un file con *estensione Settings* . Ogni file di codice contiene le sostituzioni di parametro comuni laddove appropriato.

![Selezione progetto modello di progetto](media/project-template-selection.png)

2. Aggiungere e rimuovere elementi dal progetto come richiesto per il progetto. Non rimuovere il file di progetto modificabile, il file *AssemblyInfo* o il file con *estensione vstemplate* .

3. Aggiornare il file con *estensione vstemplate* in modo da riflettere eventuali aggiunte ed eliminazioni. L'elemento [Project](../extensibility/project-element-visual-studio-templates.md) deve contenere un elemento [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) per ogni file da includere nel modello.

4. Modificare i file di codice e altri contenuti rivolte all'utente e aggiungere le sostituzioni dei parametri appropriate.

5. Modificare il contenuto generato come richiesto.

6. Compilare il progetto.

     Visual Studio crea un file con *estensione zip* che contiene il modello. Non è distribuito e non è disponibile nell'istanza sperimentale.

## <a name="create-an-item-template"></a>Creare un modello di elemento

1. Creare un progetto di modello di elemento.

     Il modello genera un file di classe, un'icona, un file con *estensione vstemplate* e un file *AssemblyInfo* . Il file di classe contiene alcune sostituzioni di parametro comuni.

2. Aggiungere e rimuovere elementi dal progetto come richiesto per il progetto.

3. Aggiornare il file con *estensione vstemplate* in modo da riflettere eventuali aggiunte ed eliminazioni. L'elemento [Project](../extensibility/project-element-visual-studio-templates.md) deve contenere un elemento [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) per ogni file da includere nel modello.

4. Modificare i file di codice e altri contenuti rivolte all'utente e aggiungere le sostituzioni dei parametri appropriate.

5. Modificare il contenuto generato in modo obbligatorio.

6. Compilare il progetto.

     Visual Studio crea un file compresso che contiene il modello. Non è distribuito e non è disponibile nell'istanza sperimentale.

## <a name="deployment"></a>Distribuzione

### <a name="to-deploy-the-project-or-item-template"></a>Per distribuire il modello di progetto o di elemento

1. Creare un progetto VSIX. Per altre informazioni, vedere [modello di progetto VSIX](../extensibility/vsix-project-template.md).

2. Impostare il progetto VSIX come progetto di avvio. Nella **Esplora soluzioni**selezionare il nodo progetto VSIX, fare clic con il pulsante destro del mouse e scegliere **Imposta come progetto di avvio**.

3. Impostare il progetto di modello di progetto come asset del progetto VSIX. Aprire il file con *estensione vsixmanifest* . Passare alla scheda **Asset** e selezionare **nuovo**.

    1. Impostare il campo **tipo** su **Microsoft. VisualStudio. ProjectTemplate** o **Microsoft. VisualStudio. ItemTemplate**.

    2. In origine selezionare l'opzione **progetto in una soluzione corrente** e quindi selezionare il progetto che contiene il modello.

4. Compilare la soluzione e premere **F5**. Viene visualizzata l'istanza sperimentale.

5. Per un progetto di modello di progetto, il modello di progetto dovrebbe essere visualizzato nella finestra di dialogo **nuovo progetto** (**file**  >  **nuovo**  >  **progetto**), nel nodo Visual C# o Visual Basic. Per un progetto di modello di elemento, il modello di elemento verrà visualizzato nella finestra di dialogo **Aggiungi nuovo elemento** . Per visualizzare la finestra di dialogo **Aggiungi nuovo elemento** , dal **Esplora soluzioni**Selezionare il nodo del progetto e selezionare **Aggiungi**  >  **nuovo elemento**.

## <a name="see-also"></a>Vedere anche

- [Informazioni di riferimento sui modelli di Visual Studio](../ide/creating-project-and-item-templates.md)
- [Pacchetti NuGet nei modelli di Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)
