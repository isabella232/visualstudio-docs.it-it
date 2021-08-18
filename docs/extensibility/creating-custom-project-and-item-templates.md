---
title: Creazione di modelli Project e di elementi | Microsoft Docs
description: Informazioni su come i modelli di creazione di modelli in Visual Studio SDK consentono di includere modelli in estensioni più grandi.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: overview
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 7efc545ac298830d2dd3a5ce85649941eb16fdfe
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122133367"
---
# <a name="create-custom-project-and-item-templates"></a>Creare modelli di progetto ed elemento personalizzati

L Visual Studio SDK include modelli di progetto che creano un modello di progetto personalizzato e un modello di elemento personalizzato. Questi modelli includono alcune sostituzioni di parametri comuni e vengono compilati come file ZIP. Non vengono distribuiti automaticamente e non sono disponibili nell'istanza sperimentale. È necessario copiare il file ZIP generato nella directory del modello utente.

I modelli di creazione dei modelli consentono di includere modelli in estensioni più grandi. In questo modo è possibile implementare il controllo della versione nei file di origine e compilare un gruppo di progetti modello in un unico pacchetto VSIX.

È anche possibile configurare un modello per installare NuGet pacchetti. Per altre informazioni, vedere [NuGet pacchetti in Visual Studio modelli.](/nuget/visual-studio-extensibility/visual-studio-templates)

Per gli scenari di creazione di modelli di base, è consigliabile usare **l'Esportazione guidata** modelli, che restituisce l'output in un file compresso. Per altre informazioni sulla creazione di modelli di base, vedere [Creazione di modelli di progetto ed elemento.](../ide/creating-project-and-item-templates.md)

> [!NOTE]
> A partire Visual Studio 2017, l'analisi dei modelli di progetto ed elemento personalizzati non verrà più eseguita. Al contrario, l'estensione deve fornire file manifesto del modello che descrivono il percorso di installazione di questi modelli. È possibile usare Visual Studio 2017 per aggiornare le estensioni VSIX. Se si distribuisce l'estensione usando un'estensione MSI, è necessario generare manualmente i file manifesto del modello. Per altre informazioni, vedere [Upgrading custom project and item templates for Visual Studio 2017 (Aggiornamento](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md)di modelli di progetto ed elementi personalizzati per Visual Studio 2017). Lo schema del manifesto del modello è documentato nell'Visual Studio [dello schema del manifesto del modello.](../extensibility/visual-studio-template-manifest-schema-reference.md)

## <a name="create-a-project-template"></a>Creare un modello di progetto

1. Creare un Project modello personalizzato. È possibile trovare il modello di progetto nella finestra di dialogo **Nuovo Project,** cercando "modello di progetto" e selezionando la versione C# o Visual Basic progetto.

     Il modello genera un file di classe, un'icona, un file con estensione *vstemplate,* un file di progetto modificabile denominato *ProjectTemplate.vbproj* o *ProjectTemplate.csproj* e alcuni file in genere generati da altri tipi di progetto, ad esempio un file *resources.resx,* un file *AssemblyInfo* e un file con estensione *settings.* Ogni file di codice contiene sostituzioni di parametri comuni, dove appropriato.

![Selezione del progetto modello di progetto](media/project-template-selection.png)

2. Aggiungere e rimuovere elementi dal progetto come richiesto per il progetto. Non rimuovere il file di progetto modificabile, il file *AssemblyInfo* o il file *con estensione vstemplate.*

3. Aggiornare il file *con estensione vstemplate* per riflettere eventuali aggiunte ed eliminazioni. [L Project elemento](../extensibility/project-element-visual-studio-templates.md) deve contenere un elemento [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) per ogni file da includere nel modello.

4. Modificare i file di codice e altro contenuto rivolto all'utente e aggiungere le sostituzioni di parametri appropriate.

5. Modificare il contenuto generato in base alle esigenze.

6. Compilare il progetto.

     Visual Studio crea un *.zip* file contenente il modello. Non viene distribuito e non è disponibile nell'istanza sperimentale.

## <a name="create-an-item-template"></a>Creare un modello di elemento

1. Creare un progetto modello di elemento.

     Il modello genera un file di classe, un'icona, un file con estensione *vstemplate* e un file *AssemblyInfo.* Il file di classe contiene alcune sostituzioni di parametri comuni.

2. Aggiungere e rimuovere elementi dal progetto come richiesto per il progetto.

3. Aggiornare il file *con estensione vstemplate* per riflettere eventuali aggiunte ed eliminazioni. [L Project elemento](../extensibility/project-element-visual-studio-templates.md) deve contenere un elemento [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) per ogni file da includere nel modello.

4. Modificare i file di codice e altro contenuto rivolto all'utente e aggiungere le sostituzioni di parametri appropriate.

5. Modificare il contenuto generato in base alle esigenze.

6. Compilare il progetto.

     Visual Studio crea un file compresso che contiene il modello. Non viene distribuito e non è disponibile nell'istanza sperimentale.

## <a name="deployment"></a>Distribuzione

### <a name="to-deploy-the-project-or-item-template"></a>Per distribuire il progetto o il modello di elemento

1. Creare un progetto VSIX. Per altre informazioni, vedere [Modello di progetto VSIX.](../extensibility/vsix-project-template.md)

2. Impostare il progetto VSIX come progetto di avvio. Nella finestra **Esplora soluzioni** selezionare il nodo del progetto VSIX, fare clic con il pulsante destro del mouse e scegliere **Imposta come** avvio Project .

3. Impostare il progetto modello di progetto come asset del progetto VSIX. Aprire il file *con estensione vsixmanifest.* Passare alla **scheda Asset e** selezionare **Nuovo.**

    1. Impostare il **campo Tipo** su **Microsoft.VisualStudio.ProjectTemplate** o **Microsoft.VisualStudio.ItemTemplate.**

    2. Per origine, selezionare **l'opzione Un** progetto nella soluzione corrente e quindi selezionare il progetto che contiene il modello.

4. Compilare la soluzione e premere **F5.** Viene visualizzata l'istanza sperimentale.

5. Per un progetto di modello di progetto, il modello di progetto dovrebbe essere elencato nella finestra di dialogo Nuovo **Project** (**File** Nuovo Project ), nel nodo  >    >  Visual C# o Visual Basic progetto. Per un progetto di modello di elemento, il modello di elemento dovrebbe essere elencato nella **finestra di dialogo Aggiungi nuovo** elemento. Per visualizzare la **finestra di dialogo Aggiungi** nuovo elemento, nella Esplora soluzioni selezionare il nodo **del** progetto e **selezionare Aggiungi** nuovo  >  **elemento**.

## <a name="see-also"></a>Vedi anche

- [Visual Studio riferimento al modello](../ide/creating-project-and-item-templates.md)
- [Pacchetti NuGet nei modelli di Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)
