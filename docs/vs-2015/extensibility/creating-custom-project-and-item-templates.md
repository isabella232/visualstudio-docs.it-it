---
title: Creazione progetto personalizzato e i modelli di elemento | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cd850cf73f9d7a9c443c374bd8a83e48c3470a31
ms.sourcegitcommit: aea5cdb76fbc7eb31d1e5cc3c8d6adb0c743220f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2018
ms.locfileid: "47590907"
---
# <a name="creating-custom-project-and-item-templates"></a>Creazione di modelli di progetto e di elemento personalizzati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [creazione Custom Project and Item Templates](https://docs.microsoft.com/visualstudio/extensibility/creating-custom-project-and-item-templates).  
  
Visual Studio SDK include modelli di progetto che creano un modello di progetto personalizzato e un modello di elemento personalizzati. Questi modelli includono alcune sostituzioni di parametro comune e build come file zip. Non vengono distribuiti automaticamente e non sono disponibili nell'istanza sperimentale. È necessario copiare il file zip al file nel percorso è  
  
 I modelli di creazione modello consentono di includere i modelli nelle estensioni di dimensioni maggiori. Ciò consente di implementare il controllo della versione nel file di origine e creare un gruppo di progetti di modello in un pacchetto VSIX.  
  
 Per scenari di creazione modello di base, è consigliabile usare la **Esporta modello** wizard, che invia l'output in un file compresso. Per altre informazioni sulla creazione del modello di base, vedere [creazione di Project and Item Templates](../ide/creating-project-and-item-templates.md).  
  
 A partire da Visual Studio "15" Preview 4, il rilevamento di progetto personalizzato e i modelli di elemento verrà non sarà più eseguita. Al contrario, l'estensione deve fornire i file manifesto che descrivono il percorso di installazione di questi modelli. È possibile utilizzare l'installazione dell'anteprima 2 per aggiornare le estensioni VSIX. Se si distribuisce l'estensione usando un file MSI, è necessario generare manualmente i file manifesto del modello. Per altre informazioni, vedere [l'aggiornamento Custom Project and Item Templates for Visual Studio "15"](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Schema del modello di manifesto è documentato in [Visual Studio modello Manifest Schema Reference](../extensibility/visual-studio-template-manifest-schema-reference.md).  
  
## <a name="creating-a-project-template"></a>Creazione di un modello di progetto  
  
1.  Creare un progetto di modello di progetto. È possibile trovare il modello di progetto di **nuovo progetto** finestra di dialogo, in Visual Basic o Visual c# **estendibilità** cartella.  
  
     Il modello genera un file di classe, un'icona, un file con estensione vstemplate, un file di progetto modificabile denominato ProjectTemplate o csproj e alcuni file che in genere vengono generati da altri tipi di progetto, questo tipo un file resources. resx, un AssemblyInfo file e un file Settings. Ogni file di codice contiene le sostituzioni dei parametri comuni nei casi appropriati.  
  
2.  Aggiungere e rimuovere elementi dal progetto in base alle esigenze per il progetto. Non rimuovere il file di progetto modificabile, il file AssemblyInfo o il file con estensione vstemplate.  
  
3.  Aggiornare il file con estensione vstemplate per riflettere eventuali aggiunte ed eliminazioni. Il [Project](../extensibility/project-element-visual-studio-templates.md) l'elemento deve contenere un [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) (elemento) per ogni file da includere nel modello.  
  
4.  Modificare i file del codice e altri contenuti agli utenti finali e aggiungere le sostituzioni dei parametri appropriati.  
  
5.  Modificare il contenuto generato in base alle esigenze.  
  
6.  Compilare il progetto.  
  
     Visual Studio crea un file con estensione zip che contiene il modello. Non è stato distribuito e non è disponibile nell'istanza sperimentale.  
  
## <a name="creating-an-item-template"></a>Creazione di un modello di elemento  
  
1.  Creare un progetto di modello di elemento.  
  
     Il modello genera un file di classe, un'icona, un file con estensione vstemplate e un file AssemblyInfo. Il file di classe contiene alcune sostituzioni di parametro comune.  
  
2.  Aggiungere e rimuovere elementi dal progetto in base alle esigenze per il progetto.  
  
3.  Aggiornare il file con estensione vstemplate per riflettere eventuali aggiunte ed eliminazioni. Il [Project](../extensibility/project-element-visual-studio-templates.md) l'elemento deve contenere un [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) (elemento) per ogni file da includere nel modello.  
  
4.  Modificare i file del codice e altri contenuti agli utenti finali e aggiungere le sostituzioni dei parametri appropriati.  
  
5.  Modificare il contenuto generato in base alle esigenze.  
  
6.  Compilare il progetto.  
  
     Visual Studio crea un file compresso che contiene il modello. Non è stato distribuito e non è disponibile nell'istanza sperimentale.  
  
## <a name="deployment"></a>Distribuzione  
  
#### <a name="to-deploy-the-project-or-item-template"></a>Per distribuire il modello di progetto o un elemento  
  
1.  Creare un progetto VSIX. Per altre informazioni, vedere [modello di progetto VSIX](../extensibility/vsix-project-template.md).  
  
2.  Impostare il progetto VSIX come progetto di avvio. Nel **Esplora soluzioni**, selezionare il nodo del progetto VSIX, pulsante destro del mouse e selezionare **imposta come progetto di avvio**.  
  
3.  Impostare il progetto di modello di progetto come un asset del progetto VSIX. Aprire il file con estensione vsixmanifest. Andare alla **Assets** scheda e fare clic su **New**.  
  
    1.  Impostare il **tipo** campo **Microsoft.VisualStudio.ProjectTemplate** oppure **Microsoft.VisualStudio.ItemTemplate**.  
  
    2.  Per l'origine, selezionare la **un progetto nella soluzione corrente** opzione e quindi selezionare il progetto che contiene il modello.  
  
4.  Compilare la soluzione e premere F5. Viene visualizzata l'istanza sperimentale.  
  
5.  Per un progetto di modello di progetto, verrà visualizzato il modello di progetto elencato nella **nuovo progetto** finestra di dialogo (**File / nuovo / progetto**), nel nodo Visual Basic o Visual c#. Per un progetto di modello di elemento, si dovrebbe essere elencato nella finestra di dialogo Aggiungi nuovo elemento del modello di elemento (nelle **Esplora soluzioni**, selezionare il nodo del progetto e fare clic su **Aggiungi / nuovo elemento**).  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti ai modelli di Visual Studio](../ide/visual-studio-template-reference.md)

