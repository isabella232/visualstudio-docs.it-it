---
title: Creazione di modelli di progetto e di elemento personalizzati
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c6875e13baa83d349020f50a3fe448a87ec5fd30
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197394"
---
# <a name="creating-custom-project-and-item-templates"></a>Creazione di modelli di progetto e di elemento personalizzati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio SDK include modelli di progetto per la creazione di un modello di progetto personalizzato e di un modello di elemento personalizzato. Questi modelli includono alcune sostituzioni di parametro comuni e vengono compilate come file zip. Non vengono distribuiti automaticamente e non sono disponibili nell'istanza sperimentale. Copiare il file zip nel percorso

I modelli di creazione del modello consentono di includere i modelli in estensioni più grandi. L'inclusione dei modelli nelle estensioni consente di implementare il controllo della versione nei file di origine e di creare un gruppo di progetti modello in un unico pacchetto VSIX.

Per gli scenari di creazione di modelli di base, è consigliabile usare l' **esportazione guidata modelli** , che restituisce un file compresso. Per ulteriori informazioni sulla creazione di modelli di base, vedere [creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md).

A partire da Visual Studio 2017, l'analisi dei modelli di progetto e di elemento personalizzati non viene più eseguita. L'estensione deve invece fornire file manifesto del modello che descrivono il percorso di installazione di questi modelli. Per aggiornare le estensioni VSIX, è possibile usare l'installazione dell'anteprima 2. Se si distribuisce l'estensione utilizzando un file MSI, è necessario generare manualmente i file manifesto del modello. Per altre informazioni, vedere [upgrade Custom Modelli di progetti ed elementi per Visual Studio 2017](/visualstudio/extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017?view=vs-2015). Lo schema del manifesto del modello è documentato in [riferimenti allo schema del manifesto del modello di Visual Studio](/visualstudio/extensibility/visual-studio-template-manifest-schema-reference).

## <a name="create-a-project-template"></a>Creare un modello di progetto

1. Creare un progetto di modello di progetto. È possibile trovare il modello di progetto nella finestra di dialogo **nuovo progetto** , nella cartella Visual Basic o Visual C# **Extensibility** .

     Il modello genera un file di classe, un'icona, un file con estensione vstemplate, un file di progetto modificabile denominato ProjectTemplate. vbproj o ProjectTemplate. csproj e alcuni file che vengono in genere generati da altri tipi di progetto, ad esempio un file resources. resx, un file AssemblyInfo e un file con estensione Settings. Ogni file di codice contiene le sostituzioni di parametro comuni laddove appropriato.

2. Aggiungere e rimuovere elementi dal progetto come richiesto per il progetto. Non rimuovere il file di progetto modificabile, il file AssemblyInfo o il file con estensione vstemplate.

3. Aggiornare il file con estensione vstemplate in modo da riflettere eventuali aggiunte ed eliminazioni. L'elemento [Project](../extensibility/project-element-visual-studio-templates.md) deve contenere un elemento [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) per ogni file da includere nel modello.

4. Modificare i file di codice e altri contenuti rivolte all'utente e aggiungere le sostituzioni dei parametri appropriate.

5. Modificare il contenuto generato come richiesto.

6. Compilare il progetto.

     Visual Studio crea un file con estensione zip che contiene il modello. Non è distribuito e non è disponibile nell'istanza sperimentale.

## <a name="create-an-item-template"></a>Creare un modello di elemento

1. Creare un progetto di modello di elemento.

     Il modello genera un file di classe, un'icona, un file con estensione vstemplate e un file AssemblyInfo. Il file di classe contiene alcune sostituzioni di parametro comuni.

2. Aggiungere e rimuovere elementi dal progetto come richiesto per il progetto.

3. Aggiornare il file con estensione vstemplate in modo da riflettere eventuali aggiunte ed eliminazioni. L'elemento [Project](../extensibility/project-element-visual-studio-templates.md) deve contenere un elemento [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) per ogni file da includere nel modello.

4. Modificare i file di codice e altri contenuti rivolte all'utente e aggiungere le sostituzioni dei parametri appropriate.

5. Modificare il contenuto generato in modo obbligatorio.

6. Compilare il progetto.

     Visual Studio crea un file compresso che contiene il modello. Non è distribuito e non è disponibile nell'istanza sperimentale.

## <a name="deploy-the-project-or-item-template"></a>Distribuire il modello di progetto o di elemento

1. Creare un progetto VSIX. Per altre informazioni, vedere [modello di progetto VSIX](../extensibility/vsix-project-template.md).

2. Impostare il progetto VSIX come progetto di avvio. Nella **Esplora soluzioni**selezionare il nodo progetto VSIX, fare clic con il pulsante destro del mouse e scegliere **Imposta come progetto di avvio**.

3. Impostare il progetto di modello di progetto come asset del progetto VSIX. Aprire il file con estensione vsixmanifest. Passare alla scheda **Asset** e fare clic su **nuovo**.

    1. Impostare il campo **tipo** su **Microsoft. VisualStudio. ProjectTemplate** o **Microsoft. VisualStudio. ItemTemplate**.

    2. In origine selezionare l'opzione **progetto in una soluzione corrente** e quindi selezionare il progetto che contiene il modello.

4. Compilare la soluzione e premere F5. Viene visualizzata l'istanza sperimentale.

5. Per un progetto di modello di progetto, il modello di progetto dovrebbe essere visualizzato nella finestra di dialogo **nuovo progetto** (**file/nuovo/progetto**), nel nodo Visual C# o Visual Basic. Per un progetto di modello di elemento, dovrebbe essere visualizzato il modello di elemento elencato nella finestra di dialogo Aggiungi nuovo elemento (nella **Esplora soluzioni**selezionare il nodo del progetto e fare clic su **Aggiungi/nuovo elemento**).

## <a name="see-also"></a>Vedere anche

- [Riferimenti ai modelli di Visual Studio](../ide/visual-studio-template-reference.md)