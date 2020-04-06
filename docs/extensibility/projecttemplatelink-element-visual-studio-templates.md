---
title: Elemento ProjectTemplateLink (modelli di Visual Studio) Documenti Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectTemplateLink
helpviewer_keywords:
- <ProjectTemplateLink> element [Visual Studio Templates]
- ProjectTemplateLink element [Visual Studio Templates]
ms.assetid: b0449111-8b48-45a1-a031-ea24b765e969
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e6d402b6605f2e01a20d400c2c33573c686a1cdd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701814"
---
# <a name="projecttemplatelink-element-visual-studio-templates"></a>Elemento ProjectTemplateLink (modelli di Visual Studio)
Specifica il percorso del file *.vstemplate* di un progetto in un modello multiprogetto.

 \<VSTemplate \<> \<TemplateContent> \<ProjectCollection> ProjectTemplateLink> \<-or- VSTemplate> \<TemplateContent> \<ProjectCollection> \<SolutionFolder> \<ProjectTemplateLink>

## <a name="syntax"></a>Sintassi

```xml
<ProjectTemplateLink ProjectName="Name">
    PathToTemplateFile
</ProjectTemplateLink>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|`ProjectName`|Attributo facoltativo.<br /><br /> Specifica il nome di ogni singolo progetto in un modello multiprogetto. La finestra di dialogo **Nuovo progetto** non può assegnare nomi ai singoli progetti.|
|`CopyParameters`|Consente la copia di tutte le variabili nel modello del gruppo centrale in ognuno dei modelli collegati.<br /><br /> I parametri nei modelli collegati dispongono del prefisso `"$ext_*$"`. Ad esempio, se nel modello `$projectname$` di gruppo padre il parametro ha un valore **ExampleProject1**, quando `$ext_projectname$`il modello collegato `$projectname$` ottiene il turno per essere eseguito, acquisisce un parametro , che è una copia del parametro dal modello del gruppo padre.<br /><br /> In questo modo i modelli collegati possono condividere alcuni parametri comuni, che possono essere facilmente creati solo nel modello del gruppo padre.<br /><br /> Questo attributo è facoltativo ed è automaticamente impostato su `false` quando non è incluso.<br /><br /> Introdotto in Visual Studio 2013 Update 2. Per fare riferimento alla versione corretta del prodotto, vedere Assembly di [riferimento forniti in Visual Studio 2013 SDK Update 2](https://msdn.microsoft.com/library/42b65c3e-e42b-4c39-98c8-bea285f25ffb).|

### <a name="child-elements"></a>Elementi figlio
 No.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Specifica l'organizzazione e i contenuti dei modelli multiprogetto.|
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|Raggruppa i progetti in modelli multiprogetto.|

## <a name="text-value"></a>Valore di testo
 È necessario specificare un valore di testo.

 Questo testo specifica il percorso del file *.vstemplate* del modello.

## <a name="remarks"></a>Osservazioni
 I modelli multiprogetto fungono da contenitori per due o più progetti. L'elemento `ProjectTemplateLink` viene utilizzato per specificare il percorso del file *.vstemplate* per uno dei progetti nel modello. Il file *.vstemplate* di un modello `ProjectTemplateLink` multiprogetto contiene un elemento per ogni progetto nel modello. Per ulteriori informazioni sui modelli multiprogetto, vedere [Procedura: creare modelli multiprogetto](../ide/how-to-create-multi-project-templates.md).

## <a name="example"></a>Esempio
 In questo esempio viene illustrato un semplice file *.vstemplate .vstemplate* radice multiprogetto. In questo esempio, il modello contiene due progetti `My Windows Application` e `My Class Library`. L'attributo `ProjectName` nell'elemento `ProjectTemplateLink` imposta il nome per [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] da assegnare a questo progetto. Se `ProjectName` l'attributo non esiste, il nome del file *.vstemplate* viene utilizzato come nome del progetto.

```
<VSTemplate Version="3.0.0" Type="ProjectGroup"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>Multi-Project Template Sample</Name>
        <Description>An example of a multi-project template</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>VisualBasic</ProjectType>
    </TemplateData>
    <TemplateContent>
        <ProjectCollection>
            <ProjectTemplateLink ProjectName="My Windows Application">
                WindowsApp\MyTemplate.vstemplate
            </ProjectTemplateLink>
            <ProjectTemplateLink ProjectName="My Class Library" CopyParameters="true">
                ClassLib\MyTemplate.vstemplate
            </ProjectTemplateLink>
        </ProjectCollection>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Vedere anche
- [Informazioni di riferimento sullo schema del modello di Visual StudioVisual Studio template schema reference](../extensibility/visual-studio-template-schema-reference.md)
- [Creare modelli di progetto e di elementi](../ide/creating-project-and-item-templates.md)
- [Procedura: creare modelli multiprogettoHow to: Create multi-project templates](../ide/how-to-create-multi-project-templates.md)
