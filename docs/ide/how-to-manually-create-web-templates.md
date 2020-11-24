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
manager: jillfra
ms.openlocfilehash: 8546b1364248b5c419a32e8f8ed40abf0b69fb5a
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/24/2020
ms.locfileid: "95597080"
---
# <a name="how-to-manually-create-web-templates"></a>Procedura: Creare manualmente modelli Web

La creazione di un modello Web è diversa dalla creazione di altri tipi di modelli. Poiché i modelli di progetto Web vengono visualizzati nella finestra di dialogo **Aggiungi nuovo sito Web** e gli elementi del progetto Web sono classificati in base al linguaggio di programmazione, il file con estensione *vstemplate* deve specificare il modello come modello Web e identificare il linguaggio di programmazione.

> [!NOTE]
> I modelli Web devono contenere un file con *estensione webproj* vuoto ed è necessario farvi riferimento nel file *vstemplate* nell' `File` attributo dell' `Project` elemento. Sebbene i progetti Web non richiedano un file di progetto con *estensione proj* , è necessario creare questo file stub affinché il modello Web funzioni correttamente.

## <a name="to-manually-create-a-web-template"></a>Per creare manualmente un modello Web

1. Creare un progetto Web.

2. Modificare o eliminare i file nel progetto o aggiungere nuovi file al progetto.

3. Creare un file XML e salvarlo con un'estensione del nome di file *vstemplate* nella stessa directory del progetto. Non aggiungerlo al progetto in Visual Studio.

4. Modificare il file XML *vstemplate* per fornire i metadati del modello di progetto. Per altre informazioni, vedere l'[esempio riportato di seguito](#example).

5. Individuare l' `ProjectType` elemento nel file *vstemplate* e impostare il valore di testo su `Web` .

6. Dopo l'elemento `ProjectType` aggiungere un elemento `ProjectSubType` e impostare il valore di testo sul linguaggio di programmazione del modello. Il linguaggio di programmazione può essere uno dei valori seguenti:

   - CSharp
   - VisualBasic

     Ad esempio:

     ```xml
     <TemplateData>
       ...
       <ProjectType>Web</ProjectType>
       <ProjectSubType>CSharp</ProjectSubType>
       ...
     </TemplateData>
     ```

7. Selezionare i file nel modello (incluso il file *vstemplate* ), fare clic con il pulsante destro del mouse sulla selezione e scegliere **Invia a**  >  **cartella compressa**. I file verranno compressi in un file *zip*.

8. Inserire il file di modello *zip* nella directory dei modelli di progetti di Visual Studio. Per impostazione predefinita, questa directory è *%USERPROFILE%\Documents\Visual Studio \<Version\> \ProjectTemplates*.

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato un file con estensione *vstemplate* di base per un modello di progetto Web:

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

## <a name="see-also"></a>Vedere anche

- [Creare modelli di progetto e di elementi](../ide/creating-project-and-item-templates.md)
- [Informazioni di riferimento sullo schema dei modelli di Visual Studio (estendibilità)](../extensibility/visual-studio-template-schema-reference.md)
