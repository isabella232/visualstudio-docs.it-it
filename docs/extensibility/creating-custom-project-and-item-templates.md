---
title: Creazione di modelli di progetto e di elemento personalizzati Documenti Microsoft
ms.date: 3/16/2019
ms.topic: conceptual
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ae404004f2660048ef7581a661d8f785495ed95a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739447"
---
# <a name="create-custom-project-and-item-templates"></a>Creare modelli di progetto e di elemento personalizzati

Visual Studio SDK include modelli di progetto che creano un modello di progetto personalizzato e un modello di elemento personalizzato. Questi modelli includono alcune sostituzioni di parametri comuni e compila come file zip. Non vengono distribuiti automaticamente e non sono disponibili nell'istanza sperimentale. È necessario copiare il file zip generato nella directory dei modelli utente.

I modelli di creazione dei modelli consentono di includere modelli in estensioni più grandi. In questo modo è possibile implementare il controllo della versione nei file di origine e compilare un gruppo di progetti di modello in un pacchetto VSIX.

È anche possibile configurare un modello per installare i pacchetti NuGet.You can also configure a template to install NuGet packages. Per ulteriori informazioni, vedere [Pacchetti NuGet nei modelli](/nuget/visual-studio-extensibility/visual-studio-templates)di Visual Studio .

Per gli scenari di creazione di modelli di base, è necessario utilizzare la procedura guidata **Esporta modello,** che restituisce un file compresso. Per ulteriori informazioni sulla creazione di modelli di base, consultate Creazione di modelli di [progetto e di elemento.](../ide/creating-project-and-item-templates.md)

> [!NOTE]
> A partire da Visual Studio 2017, l'analisi dei modelli di progetto ed elemento personalizzati non verrà più eseguita. Al contrario, l'estensione deve fornire i file manifesto del modello che descrivono il percorso di installazione di questi modelli. È possibile usare Visual Studio 2017 per aggiornare le estensioni VSIX. Se si distribuisce l'estensione utilizzando un file MSI, è necessario generare manualmente i file manifesto del modello. Per ulteriori informazioni, vedere Aggiornamento di modelli di [progetto e di elemento personalizzati per Visual Studio 2017.](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md) Lo schema del manifesto del modello è documentato in [Riferimento allo schema del manifesto del modello](../extensibility/visual-studio-template-manifest-schema-reference.md)di Visual Studio .

## <a name="create-a-project-template"></a>Creare un modello di progetto

1. Creare un progetto modello di progetto. È possibile trovare il modello di progetto nella finestra di dialogo **Nuovo progetto,** cercando "modello di progetto" e selezionando la versione di C , o Visual Basic.

     Il modello genera un file di classe, un'icona, un file con *estensione vstemplate,* un file di progetto modificabile denominato *ProjectTemplate.vbproj* o *ProjectTemplate.csproj*e alcuni file generati in genere da altri tipi di progetto, ad esempio un file *resources.resx,* un file *AssemblyInfo* e un file *con estensione settings.* Ogni file di codice contiene sostituzioni di parametri comuni, se appropriato.

![selezione del progetto modello di progetto](media/project-template-selection.png)

2. Aggiungere e rimuovere elementi dal progetto in base alle esigenze del progetto. Non rimuovere il file di progetto modificabile, il file *AssemblyInfo* o il file *.vstemplate.*

3. Aggiornare il file *.vstemplate* per riflettere eventuali aggiunte ed eliminazioni. L'elemento [Project](../extensibility/project-element-visual-studio-templates.md) deve contenere un elemento [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) per ogni file da includere nel modello.

4. Modificare i file di codice e altro contenuto rivolto all'utente e aggiungere le sostituzioni di parametri appropriate.

5. Modificare il contenuto generato in base alle esigenze.

6. Compilare il progetto.

     Visual Studio crea un file *con estensione zip* che contiene il modello. Non viene distribuito e non è disponibile nell'istanza sperimentale.

## <a name="create-an-item-template"></a>Creare un modello di elemento

1. Creare un progetto modello di elemento.

     Il modello genera un file di classe, un'icona, un file *.vstemplate* e un file *AssemblyInfo.* Il file di classe contiene alcune sostituzioni di parametri comuni.

2. Aggiungere e rimuovere elementi dal progetto in base alle esigenze del progetto.

3. Aggiornare il file *.vstemplate* per riflettere eventuali aggiunte ed eliminazioni. L'elemento [Project](../extensibility/project-element-visual-studio-templates.md) deve contenere un elemento [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) per ogni file da includere nel modello.

4. Modificare i file di codice e altro contenuto rivolto all'utente e aggiungere le sostituzioni di parametri appropriate.

5. Modificare il contenuto generato in base alle esigenze.

6. Compilare il progetto.

     Visual Studio crea un file compresso che contiene il modello. Non viene distribuito e non è disponibile nell'istanza sperimentale.

## <a name="deployment"></a>Distribuzione

### <a name="to-deploy-the-project-or-item-template"></a>Per distribuire il modello di progetto o di elementoTo deploy the project or item template

1. Creare un progetto VSIX. Per ulteriori informazioni, vedere modello di [progetto VSIX](../extensibility/vsix-project-template.md).

2. Impostare il progetto VSIX come progetto di avvio. In **Esplora soluzioni**selezionare il nodo del progetto VSIX , fare clic con il pulsante destro del mouse e scegliere Imposta come progetto di **avvio**.

3. Impostare il progetto di modello di progetto come risorsa del progetto VSIX. Aprire il file *vsixmanifest.* Passare alla scheda **Risorse** e fare clic su **Nuovo**.

    1. Impostare il campo **Type** su **Microsoft.VisualStudio.ProjectTemplate** o **Microsoft.VisualStudio.ItemTemplate**.

    2. Per l'origine, selezionare l'opzione **Un progetto nella soluzione corrente** e quindi selezionare il progetto che contiene il modello.

4. Compilare la soluzione e premere **F5**. Viene visualizzata l'istanza sperimentale.

5. Per un progetto di modello di progetto, il modello di progetto dovrebbe essere elencato nella finestra di dialogo **Nuovo progetto** (**File** > **nuovo** > **progetto**), nel nodo Visual C. Per un progetto di modello di elemento, si dovrebbe vedere il modello di elemento elencato nella finestra di dialogo **Aggiungi nuovo elemento.** Per visualizzare la finestra di dialogo **Aggiungi nuovo elemento,** in **Esplora soluzioni**selezionare il nodo del progetto e fare clic su **Aggiungi** > **nuovo elemento**.

## <a name="see-also"></a>Vedere anche

- [Informazioni di riferimento sui modelli di Visual StudioVisual Studio template reference](../ide/creating-project-and-item-templates.md)
- [Pacchetti NuGet nei modelli di Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)
