---
title: Creazione progetto personalizzato e i modelli di elemento | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: eeea0f92fc846b6ed51673d22450b22e01b348eb
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2018
ms.locfileid: "39497862"
---
# <a name="create-custom-project-and-item-templates"></a>Creare modelli di progetto ed elemento personalizzati

Visual Studio SDK include modelli di progetto che creano un modello di progetto personalizzato e un modello di elemento personalizzati. Questi modelli includono alcune sostituzioni di parametro comune e build come file zip. Non vengono distribuiti automaticamente e non sono disponibili nell'istanza sperimentale. È necessario copiare il file zip generati alla directory dei modelli utente.
  
I modelli di creazione modello consentono di includere i modelli nelle estensioni di dimensioni maggiori. Ciò consente di implementare il controllo della versione nel file di origine e creare un gruppo di progetti di modello in un pacchetto VSIX.  
  
È anche possibile configurare un modello per installare i pacchetti NuGet. Per altre informazioni, vedere [pacchetti NuGet nei modelli di Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates).

Per scenari di creazione modello di base, è consigliabile usare la **Esporta modello** wizard, che invia l'output in un file compresso. Per altre informazioni sulla creazione del modello di base, vedere [creazione di modelli di progetto ed elemento](../ide/creating-project-and-item-templates.md).  

> [!NOTE]
> A partire da Visual Studio 2017, l'analisi per progetto personalizzato e i modelli di elemento verrà non sarà più eseguita. Al contrario, l'estensione deve fornire i file manifesto che descrivono il percorso di installazione di questi modelli. È possibile usare Visual Studio 2017 per aggiornare le estensioni VSIX. Se si distribuisce l'estensione usando un file MSI, è necessario generare manualmente i file manifesto del modello. Per altre informazioni, vedere [aggiornamento per progetti ed elementi di modelli personalizzati per Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Schema del modello di manifesto è documentato in [riferimenti dello schema del manifesto dei modelli di Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="create-a-project-template"></a>Creare un modello di progetto  
  
1.  Creare un progetto di modello di progetto. È possibile trovare il modello di progetto di **nuovo progetto** finestra di dialogo, in Visual Basic o Visual c# *estendibilità* cartella.  
  
     Il modello genera un file di classe, un'icona, una *vstemplate* del file, un file di progetto modificabile denominato *ProjectTemplate* oppure *csproj*e alcuni i file che in genere vengono generati da altri tipi di progetto, questo tipo una *Resources. resx* file, un *AssemblyInfo* file e un *Settings* file. Ogni file di codice contiene le sostituzioni dei parametri comuni nei casi appropriati.  
  
2.  Aggiungere e rimuovere elementi dal progetto in base alle esigenze per il progetto. Non rimuovere il file di progetto modificabile, il *AssemblyInfo* file o la *vstemplate* file.  
  
3.  Aggiorna il *vstemplate* file in modo da riflettere eventuali aggiunte ed eliminazioni. Il [Project](../extensibility/project-element-visual-studio-templates.md) l'elemento deve contenere un [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) (elemento) per ogni file da includere nel modello.  
  
4.  Modificare i file del codice e altri contenuti agli utenti finali e aggiungere le sostituzioni dei parametri appropriati.  
  
5.  Modificare il contenuto generato in base alle esigenze.  
  
6.  Compilare il progetto.  
  
     Visual Studio crea una *zip* file che contiene il modello. Non è stato distribuito e non è disponibile nell'istanza sperimentale.  
  
## <a name="create-an-item-template"></a>Creare un modello di elemento  
  
1.  Creare un progetto di modello di elemento.  
  
     Il modello genera un file di classe, un'icona, una *vstemplate* file e un *AssemblyInfo* file. Il file di classe contiene alcune sostituzioni di parametro comune.  
  
2.  Aggiungere e rimuovere elementi dal progetto in base alle esigenze per il progetto.  
  
3.  Aggiorna il *vstemplate* file in modo da riflettere eventuali aggiunte ed eliminazioni. Il [Project](../extensibility/project-element-visual-studio-templates.md) l'elemento deve contenere un [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) (elemento) per ogni file da includere nel modello.  
  
4.  Modificare i file del codice e altri contenuti agli utenti finali e aggiungere le sostituzioni dei parametri appropriati.  
  
5.  Modificare il contenuto generato in base alle esigenze.  
  
6.  Compilare il progetto.  
  
     Visual Studio crea un file compresso che contiene il modello. Non è stato distribuito e non è disponibile nell'istanza sperimentale.  
  
## <a name="deployment"></a>Distribuzione  
  
### <a name="to-deploy-the-project-or-item-template"></a>Per distribuire il modello di progetto o un elemento  
  
1.  Creare un progetto VSIX. Per altre informazioni, vedere [modello di progetto VSIX](../extensibility/vsix-project-template.md).  
  
2.  Impostare il progetto VSIX come progetto di avvio. Nel **Esplora soluzioni**, selezionare il nodo del progetto VSIX, pulsante destro del mouse e selezionare **imposta come progetto di avvio**.  
  
3.  Impostare il progetto di modello di progetto come un asset del progetto VSIX. Aprire il *vsixmanifest* file. Andare alla **Assets** scheda e fare clic su **New**.  
  
    1.  Impostare il **tipo** campo **Microsoft.VisualStudio.ProjectTemplate** oppure **Microsoft.VisualStudio.ItemTemplate**.  
  
    2.  Per l'origine, selezionare la **un progetto nella soluzione corrente** opzione e quindi selezionare il progetto che contiene il modello.  
  
4.  Compilare la soluzione e premere **F5**. Viene visualizzata l'istanza sperimentale.  
  
5.  Per un progetto di modello di progetto, verrà visualizzato il modello di progetto elencato nella **nuovo progetto** finestra di dialogo (**File** > **nuovo**  >  **Progetto**), nel nodo Visual Basic o Visual c#. Per un progetto di modello di elemento, verrà visualizzato il modello di elemento elencato nella **Aggiungi nuovo elemento** finestra di dialogo. Per visualizzare il **Aggiungi nuovo elemento** finestra di dialogo dalle **Esplora soluzioni**, selezionare il nodo del progetto e fare clic su **Add** > **nuovo elemento**).  
  
## <a name="see-also"></a>Vedere anche

[Riferimento al modello di Visual Studio](../ide/visual-studio-template-reference.md)  
[Pacchetti NuGet nei modelli di Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)