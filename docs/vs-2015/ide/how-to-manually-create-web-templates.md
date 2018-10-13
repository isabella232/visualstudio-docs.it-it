---
title: 'Procedura: Creare manualmente modelli Web | Microsoft Docs'
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
- Visual Studio templates, Web
- templates [Visual Studio], Web
- Web templates [Visual Studio]
- project templates [Visual Studio], Web
ms.assetid: 731c4027-a152-48c5-bfc4-93490bf1949f
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d4496c42bfcc0baecd69770ff529c189d85da026
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49220870"
---
# <a name="how-to-manually-create-web-templates"></a>Procedura: creare manualmente modelli Web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La creazione di un modello Web è diversa dalla creazione di altri tipi di modelli. Poiché i modelli di progetto Web vengono visualizzati nella finestra di dialogo **Aggiungi nuovo sito Web** e gli elementi di progetto Web vengono classificati in base al linguaggio di programmazione, il file con estensione vstemplate deve specificare il modello come modello Web e identificare il linguaggio di programmazione.  
  
> [!NOTE]
>  I modelli Web devono contenere un file con estensione webproj vuoto che viene specificato usando l'attributo `File` dell'elemento `Project`. Anche se i progetti Web non richiedono file di progetto, questo file è necessario affinché un modello Web funzioni correttamente.  
  
### <a name="to-manually-create-a-web-template"></a>Per creare manualmente un modello Web  
  
1.  Creare un progetto Web.  
  
2.  Modificare o eliminare i file nel progetto o aggiungere nuovi file al progetto.  
  
3.  Creare un file XML e salvarlo con estensione vstemplate nella stessa directory del progetto. Non aggiungerlo al progetto in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
4.  Creare il file XML con estensione vstemplate per fornire i metadati del modello di progetto. Per altre informazioni, vedere l'esempio nella sezione successiva.  
  
5.  Individuare l'elemento `ProjectType` nel file con estensione vstemplate e impostare il valore di testo su `Web`.  
  
6.  Dopo l'elemento `ProjectType` aggiungere un elemento `ProjectSubType` e impostare il valore di testo sul linguaggio di programmazione del modello. Il linguaggio di programmazione può essere uno dei valori seguenti:  
  
    -   CSharp  
  
    -   VisualBasic  
  
     Ad esempio:  
  
    ```  
    <TemplateData>  
        ...  
        <ProjectType>Web</ProjectType>  
        <ProjectSubType>CSharp</ProjectSubType>  
        ...  
    </TemplateData>  
    ```  
  
7.  Selezionare i file nel modello (incluso il file con estensione vstemplate), fare clic con il pulsante destro del mouse sulla selezione, scegliere **Invia a** e quindi fare clic su **Cartella compressa**. I file verranno compressi in un file ZIP.  
  
8.  Inserire il file di modello con estensione zip nella directory dei modelli di progetto [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Per impostazione predefinita, la directory è \Documenti\Visual Studio *Versione*\My Exported Templates\\.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente illustra un file con estensione vstemplate di base per un modello di progetto Web.  
  
```  
<VSTemplate Version="2.0.0" Type="Project"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>  
    <TemplateData>  
        <Name>MyWebProjecStarterKit</Name>  
        <Description>A simple Web template</Description>  
        <Icon>icon.ico</Icon>  
        <ProjectType>Web</ProjectType>  
        <ProjectSubType>CSharp</ProjectSubType>  
        <DefaultName>WebSite</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="WebApplication.webproj">  
            <ProjectItem>icon.ico</ProjectItem>  
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>  
            <ProjectItem>Default.aspx.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)   
 [Riferimenti sullo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)



