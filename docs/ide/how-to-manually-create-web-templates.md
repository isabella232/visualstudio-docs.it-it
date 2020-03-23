---
title: Creare modelli Web
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, Web
- templates [Visual Studio], Web
- Web templates [Visual Studio]
- project templates [Visual Studio], Web
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 245b20dd9cad465129d6c79c38e53b6379c2c09c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591008"
---
# <a name="how-to-manually-create-web-templates"></a>Procedura: Creare manualmente modelli Web

La creazione di un modello Web è diversa dalla creazione di altri tipi di modelli. Poiché i modelli di progetto Web vengono visualizzati nella finestra di dialogo **Aggiungi nuovo sito Web** e gli elementi del progetto Web sono classificati in base al linguaggio di programmazione, il file *vstemplate* deve specificare il modello come modello Web e identificare il linguaggio di programmazione.

> [!NOTE]
> I modelli Web devono contenere un file *con estensione webproj* vuoto e devono `Project` essere indicati nel file *vstemplate* nell'attributo `File` dell'elemento. Anche se i progetti Web non richiedono un file di progetto *con estensione proj,* è necessario creare questo file stub per il corretto funzionamento del modello Web.

## <a name="to-manually-create-a-web-template"></a>Per creare manualmente un modello Web

1. Creare un progetto Web.

2. Modificare o eliminare i file nel progetto o aggiungere nuovi file al progetto.

3. Creare un file XML e salvarlo con un'estensione *vstemplate,* nella stessa directory del progetto. Non aggiungerlo al progetto in Visual Studio.

4. Modificare il file XML *vstemplate* per fornire i metadati del modello di progetto. Per altre informazioni, vedere l'[esempio riportato di seguito](#example).

5. Individuare `ProjectType` l'elemento nel file *vstemplate* e `Web`impostare il valore di testo su .

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

7. Selezionare i file nel modello (inclusi il file *vstemplate),* fare clic con il pulsante destro del mouse sulla selezione e scegliere **Invia a** > **cartella compressa .** I file verranno compressi in un file *zip*.

8. Inserire il file di modello *zip* nella directory dei modelli di progetti di Visual Studio. Per impostazione predefinita la directory è * %USERPROFILE%\Documents\Visual Studio \<Version\>\ProjectTemplates*.

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato un file *vstemplate* di base per un modello di progetto Web:

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

- [Creare modelli di progetto e di elemento](../ide/creating-project-and-item-templates.md)
- [Informazioni di riferimento sullo schema dei modelli di Visual Studio (estendibilità)](../extensibility/visual-studio-template-schema-reference.md)
