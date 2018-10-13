---
title: 'Procedura: Destinare una versione di .NET Framework | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], targeting .NET Framework version
ms.assetid: dea62d25-3d1b-492e-a6cc-b5154489800a
caps.latest.revision: 53
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3370c62535f2bb915115533ea79f4b913c3ac347
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49182364"
---
# <a name="how-to-target-a-version-of-the-net-framework"></a>Procedura: destinare una versione di .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questo documento viene descritto come scegliere una versione di destinazione di .NET Framework quando si crea un progetto e come modificare la versione di destinazione in un progetto di Visual Basic, Visual C# o Visual F# esistente.  
  
> [!IMPORTANT]
>  Per informazioni su come modificare la versione di destinazione per i progetti C++, vedere [Procedura: Modificare il framework di destinazione e il set di strumenti della piattaforma](http://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe).  
  
 **Contenuto dell'argomento**  
  
-   [Destinazione di una versione durante la creazione di un progetto](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_new)  
  
-   [Modifica della versione di destinazione](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_existing)  
  
##  <a name="bkmk_new"></a> Versione di destinazione durante la creazione di un progetto  
 Quando si crea un progetto, la versione di .NET Framework di destinazione determina i modelli che è possibile utilizzare.  
  
> [!NOTE]
>  Nelle edizioni Express di Visual Studio, è necessario creare prima il progetto e successivamente modificare la destinazione, come descritto più avanti nella sezione [Modifica della versione di destinazione](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_existing) di questo argomento.  
  
#### <a name="to-target-a-version-when-you-create-a-project"></a>Per scegliere una versione di destinazione durante la creazione di un progetto  
  
1.  Nella barra dei menu scegliere **File**, **Nuovo**, **Progetto**.  
  
2.  Nell'elenco che si trova nella parte superiore della finestra di dialogo **Nuovo progetto** scegliere la versione di .NET Framework a cui si vuole destinare il progetto.  
  
    > [!NOTE]
    >  In genere, viene installata una sola una versione di .NET Framework con Visual Studio. Se si desidera destinare il progetto a un'altra versione, è necessario innanzitutto verificare che sia installata. Vedere [Panoramica del multitargeting di Visual Studio](../ide/visual-studio-multi-targeting-overview.md).  
  
3.  Nell'elenco dei modelli installati, selezionare il tipo di progetto che si vuole creare, assegnare un nome al progetto e quindi scegliere **OK**.  
  
     Nell'elenco dei modelli vengono mostrati solo quei progetti che sono supportati dalla versione di .NET Framework selezionata.  
  
##  <a name="bkmk_existing"></a>Modifica della versione di destinazione  
 È possibile cambiare la versione di destinazione di .NET Framework in un progetto di Visual Basic, Visual C#, Visual F# seguendo la procedura seguente.  
  
#### <a name="to-change-the-targeted-version"></a>Per cambiare la versione di destinazione  
  
1.  In **Esplora soluzioni** aprire il menu di scelta rapida del progetto che si vuole modificare e scegliere **Proprietà**.  
  
     ![Proprietà Esplora soluzioni di Visual Studio](../ide/media/vs-slnexplorer-properties.png "vs_slnExplorer_Properties")  
  
    > [!IMPORTANT]
    >  Per informazioni su come modificare la versione di destinazione per i progetti C++, vedere [Procedura: Modificare il framework di destinazione e il set di strumenti della piattaforma](http://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe).  
  
2.  Nella colonna sinistra della finestra delle proprietà scegliere la scheda **Applicazione**.  
  
     ![Scheda applicazione delle proprietà dell'app di Visual Studio](../ide/media/vs-slnexplorer-properties-applicationtab.png "vs_slnExplorer_Properties_ApplicationTab")  
  
    > [!NOTE]
    >  Dopo aver creato un'app di Windows Store, non è possibile cambiare la versione di destinazione di Windows o di .NET Framework.  
  
3.  Nell'elenco **Framework di destinazione** selezionare la versione appropriata.  
  
4.  Nella finestra di dialogo di verifica visualizzata scegliere **Sì**.  
  
     Il progetto verrà scaricato. Una volta caricato nuovamente, il progetto sarà destinato alla versione di .NET Framework appena scelta.  
  
    > [!NOTE]
    >  Se il codice contiene riferimenti a una versione di .NET Framework diversa rispetto a quella di destinazione, è possibile che vengano visualizzati dei messaggi di errore durante la compilazione o l'esecuzione del codice. Per risolvere questi errori è necessario modificare i riferimenti. Vedere [Risoluzione dei problemi relativi agli errori di impostazione di .NET Framework come destinazione](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica del multitargeting di Visual Studio](../ide/visual-studio-multi-targeting-overview.md)   
 [.NET Framework Multi-Targeting for ASP.NET Web Projects](http://msdn.microsoft.com/library/8b8145a9-62f6-4fc4-8a83-47b0487cbe76)  (Multitargeting .NET Framework per progetti Web ASP.NET)  
 [Risoluzione dei problemi relativi agli errori di impostazione di .NET Framework come destinazione](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)   
 [Application Page, Project Designer (C#)](../ide/reference/application-page-project-designer-csharp.md)  (Applicazione (pagina), Creazione progetti (C#))  
 [Application Page, Project Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)  (Pagina Applicazione, Creazione progetti (Visual Basic))  
 [Configurazione dei progetti](http://msdn.microsoft.com/library/a1489abb-6294-4f8f-b71f-2cb126393526)   
 [Procedura: Modificare il framework di destinazione e il set di strumenti della piattaforma](http://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe)



