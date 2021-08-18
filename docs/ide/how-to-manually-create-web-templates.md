---
title: Creare modelli Web
description: Informazioni su come creare manualmente un modello Web e identificare il linguaggio di programmazione utilizzato dal modello.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: how-to
helpviewer_keywords:
- Visual Studio templates, Web
- templates [Visual Studio], Web
- Web templates [Visual Studio]
- project templates [Visual Studio], Web
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.openlocfilehash: 05a3bbe59c290ade7871d63a7a89d900638c5afe
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122101700"
---
# <a name="how-to-manually-create-web-templates"></a>Procedura: Creare manualmente modelli Web

La creazione di un modello Web è diversa dalla creazione di altri tipi di modelli. Poiché i modelli di progetto Web vengono visualizzati nella finestra di dialogo Aggiungi nuovo sito Web e gli elementi del progetto Web sono suddivisi in categorie in base al linguaggio di programmazione, il file *vstemplate* deve specificare il modello come modello **Web** e identificare il linguaggio di programmazione.

> [!NOTE]
> I modelli Web devono contenere un file con estensione *webproj* vuoto e farvi riferimento nel file *vstemplate* nell'attributo `File` `Project` dell'elemento . Anche se i progetti Web non richiedono un file di progetto con estensione *proj,* è necessario creare questo file stub per il corretto funzionamento del modello Web.

## <a name="to-manually-create-a-web-template"></a>Per creare manualmente un modello Web

1. Creare un progetto Web.

2. Modificare o eliminare i file nel progetto o aggiungere nuovi file al progetto.

3. Creare un file XML e salvarlo con *un'estensione vstemplate,* nella stessa directory del progetto. Non aggiungerlo al progetto in Visual Studio.

4. Modificare il file *XML vstemplate* per fornire i metadati del modello di progetto. Per altre informazioni, vedere l'[esempio riportato di seguito](#example).

5. Individuare `ProjectType` l'elemento nel file *vstemplate* e impostare il valore di testo su `Web` .

6. Dopo l'elemento `ProjectType` aggiungere un elemento `ProjectSubType` e impostare il valore di testo sul linguaggio di programmazione del modello. Il linguaggio di programmazione può essere uno dei valori seguenti:

   - CSharp
   - VisualBasic

     Esempio:

     ```xml
     <TemplateData>
       ...
       <ProjectType>Web</ProjectType>
       <ProjectSubType>CSharp</ProjectSubType>
       ...
     </TemplateData>
     ```

7. Selezionare i file nel modello (incluso il file *vstemplate),* fare clic con il pulsante destro del mouse sulla selezione e scegliere **Invia** alla cartella  >  **compressa**. I file verranno compressi in un file *zip*.

8. Inserire il file di modello *zip* nella directory dei modelli di progetti di Visual Studio. Per impostazione predefinita, questa directory è *%USERPROFILE%\Documents\Visual Studio \<Version\> \ProjectTemplates*.

## <a name="example"></a>Esempio

L'esempio seguente illustra un file *vstemplate* di base per un modello di progetto Web:

```xml
<VSTemplate Version="2.0.0" Type="Project"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyWebProjecStarterKit</Name>
        <Description>A simple web template</Description>
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

## <a name="see-also"></a>Vedi anche

- [Creare modelli di progetto e di elementi](../ide/creating-project-and-item-templates.md)
- [Informazioni di riferimento sullo schema dei modelli di Visual Studio (estendibilità)](../extensibility/visual-studio-template-schema-reference.md)
