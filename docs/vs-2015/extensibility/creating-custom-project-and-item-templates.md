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
ms.openlocfilehash: 2e04ca6afaa8e5a290e6c2a3419bb4fa28fd46e6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58968240"
---
# <a name="creating-custom-project-and-item-templates"></a>Creazione di modelli di progetto e di elemento personalizzati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio SDK include modelli di progetto che creano un modello di progetto personalizzato e un modello di elemento personalizzati. Questi modelli includono alcune sostituzioni di parametro comune e build come file zip. Non vengono distribuiti automaticamente e non sono disponibili nell'istanza sperimentale. Copiare il file zip al file nel percorso è

I modelli di creazione modello consentono di includere i modelli nelle estensioni di dimensioni maggiori. Inclusi i modelli nelle estensioni consente di implementare il controllo della versione nel file di origine e creare un gruppo di progetti di modello in un pacchetto VSIX.

Per scenari di creazione modello di base, è consigliabile usare la **Esporta modello** wizard, che invia l'output in un file compresso. Per altre informazioni sulla creazione del modello di base, vedere [creazione di Project and Item Templates](../ide/creating-project-and-item-templates.md).

A partire da Visual Studio 2017, l'analisi per progetto personalizzato e i modelli di elemento non viene più eseguito. Al contrario, l'estensione deve fornire i file manifesto che descrivono il percorso di installazione di questi modelli. È possibile utilizzare l'installazione dell'anteprima 2 per aggiornare le estensioni VSIX. Se si distribuisce l'estensione usando un file MSI, è necessario generare manualmente i file manifesto del modello. Per altre informazioni, vedere [esegue l'aggiornamento di un progetto personalizzato e modelli di elementi per Visual Studio 2017](/visualstudio/extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017?view=vs-2015). Schema del modello di manifesto è documentato in [Visual Studio modello Manifest Schema Reference](/visualstudio/extensibility/visual-studio-template-manifest-schema-reference).

## <a name="create-a-project-template"></a>Creare un modello di progetto

1.  Creare un progetto di modello di progetto. È possibile trovare il modello di progetto di **nuovo progetto** finestra di dialogo, in Visual Basic o Visual c# **estendibilità** cartella.

     Il modello genera un file di classe, un'icona, un file con estensione vstemplate, un file di progetto modificabile denominato ProjectTemplate o csproj e alcuni file che in genere vengono generati da altri tipi di progetto, questo tipo un file resources. resx, un AssemblyInfo file e un file Settings. Ogni file di codice contiene le sostituzioni dei parametri comuni nei casi appropriati.

2.  Aggiungere e rimuovere elementi dal progetto in base alle esigenze per il progetto. Non rimuovere il file di progetto modificabile, il file AssemblyInfo o il file con estensione vstemplate.

3.  Aggiornare il file con estensione vstemplate per riflettere eventuali aggiunte ed eliminazioni. Il [Project](../extensibility/project-element-visual-studio-templates.md) l'elemento deve contenere un [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) (elemento) per ogni file da includere nel modello.

4.  Modificare i file del codice e altri contenuti agli utenti finali e aggiungere le sostituzioni dei parametri appropriati.

5.  Modificare il contenuto generato in base alle esigenze.

6.  Compilare il progetto.

     Visual Studio crea un file con estensione zip che contiene il modello. Non è stato distribuito e non è disponibile nell'istanza sperimentale.

## <a name="create-an-item-template"></a>Creare un modello di elemento

1.  Creare un progetto di modello di elemento.

     Il modello genera un file di classe, un'icona, un file con estensione vstemplate e un file AssemblyInfo. Il file di classe contiene alcune sostituzioni di parametro comune.

2.  Aggiungere e rimuovere elementi dal progetto in base alle esigenze per il progetto.

3.  Aggiornare il file con estensione vstemplate per riflettere eventuali aggiunte ed eliminazioni. Il [Project](../extensibility/project-element-visual-studio-templates.md) l'elemento deve contenere un [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) (elemento) per ogni file da includere nel modello.

4.  Modificare i file del codice e altri contenuti agli utenti finali e aggiungere le sostituzioni dei parametri appropriati.

5.  Modificare il contenuto generato in base alle esigenze.

6.  Compilare il progetto.

     Visual Studio crea un file compresso che contiene il modello. Non è stato distribuito e non è disponibile nell'istanza sperimentale.

## <a name="deploy-the-project-or-item-template"></a>Distribuire il modello di progetto o un elemento

1.  Creare un progetto VSIX. Per altre informazioni, vedere [modello di progetto VSIX](../extensibility/vsix-project-template.md).

2.  Impostare il progetto VSIX come progetto di avvio. Nel **Esplora soluzioni**, selezionare il nodo del progetto VSIX, pulsante destro del mouse e selezionare **imposta come progetto di avvio**.

3.  Impostare il progetto di modello di progetto come un asset del progetto VSIX. Aprire il file con estensione vsixmanifest. Andare alla **Assets** scheda e fare clic su **New**.

    1.  Impostare il **tipo** campo **Microsoft.VisualStudio.ProjectTemplate** oppure **Microsoft.VisualStudio.ItemTemplate**.

    2.  Per l'origine, selezionare la **un progetto nella soluzione corrente** opzione e quindi selezionare il progetto che contiene il modello.

4.  Compilare la soluzione e premere F5. Viene visualizzata l'istanza sperimentale.

5.  Per un progetto di modello di progetto, verrà visualizzato il modello di progetto elencato nella **nuovo progetto** finestra di dialogo (**File / nuovo / progetto**), nel nodo Visual Basic o Visual c#. Per un progetto di modello di elemento, si dovrebbe essere elencato nella finestra di dialogo Aggiungi nuovo elemento del modello di elemento (nelle **Esplora soluzioni**, selezionare il nodo del progetto e fare clic su **Aggiungi / nuovo elemento**).

## <a name="see-also"></a>Vedere anche

- [Riferimenti ai modelli di Visual Studio](../ide/visual-studio-template-reference.md)