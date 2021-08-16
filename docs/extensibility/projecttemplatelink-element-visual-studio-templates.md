---
title: Elemento ProjectTemplateLink (Visual Studio) | Microsoft Docs
description: Informazioni sull'elemento e su come specifica il percorso del file con estensione vstemplate di <element> un progetto in un modello multi-progetto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectTemplateLink
helpviewer_keywords:
- <ProjectTemplateLink> element [Visual Studio Templates]
- ProjectTemplateLink element [Visual Studio Templates]
ms.assetid: b0449111-8b48-45a1-a031-ea24b765e969
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ee72057957df7c7296b64845fe2daaa1d23d0f10bc0f6b28321dd40dfc18c805
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121359039"
---
# <a name="projecttemplatelink-element-visual-studio-templates"></a>Elemento ProjectTemplateLink (modelli di Visual Studio)
Specifica il percorso del file *con estensione vstemplate* di un progetto in un modello multi-progetto.

 \<VSTemplate> \<TemplateContent>
 \<ProjectCollection>
 \<ProjectTemplateLink>
-oppure- \<VSTemplate>
 \<TemplateContent>
 \<ProjectCollection>
 \<SolutionFolder>
 \<ProjectTemplateLink>

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
|`ProjectName`|Attributo facoltativo.<br /><br /> Specifica il nome di ogni singolo progetto in un modello multiprogetto. La **finestra di dialogo Project** non può assegnare nomi a singoli progetti.|
|`CopyParameters`|Consente la copia di tutte le variabili nel modello del gruppo centrale in ognuno dei modelli collegati.<br /><br /> I parametri nei modelli collegati dispongono del prefisso `"$ext_*$"`. Ad esempio, se nel modello di gruppo padre il parametro ha un valore `$projectname$` **ExampleProject1**, quando il modello collegato ottiene il proprio turno da eseguire, acquisisce un parametro , che è una copia del parametro dal modello di gruppo `$ext_projectname$` `$projectname$` padre.<br /><br /> In questo modo i modelli collegati possono condividere alcuni parametri comuni, che possono essere facilmente creati solo nel modello del gruppo padre.<br /><br /> Questo attributo è facoltativo ed è automaticamente impostato su `false` quando non è incluso.<br /><br /> Introdotto in Visual Studio 2013 Update 2. Per fare riferimento alla versione corretta del prodotto, vedere Assembly di riferimento recapitati [in Visual Studio 2013 SDK Update 2.](/previous-versions/dn632168(v=vs.120))|

### <a name="child-elements"></a>Elementi figlio
 Nessuno.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Specifica l'organizzazione e i contenuti dei modelli multiprogetto.|
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|Raggruppa i progetti in modelli multiprogetto.|

## <a name="text-value"></a>Valore di testo
 È necessario specificare un valore di testo.

 Questo testo specifica il percorso del file *con estensione vstemplate* del modello.

## <a name="remarks"></a>Commenti
 I modelli multiprogetto fungono da contenitori per due o più progetti. `ProjectTemplateLink`L'elemento viene usato per specificare il percorso del file con estensione *vstemplate* per uno dei progetti nel modello. Il file *con estensione vstemplate* di un modello multi-progetto contiene un `ProjectTemplateLink` elemento per ogni progetto nel modello. Per altre informazioni sui modelli multi-progetto, vedere [Procedura: Creare modelli multi-progetto](../ide/how-to-create-multi-project-templates.md).

## <a name="example"></a>Esempio
 Questo esempio mostra un semplice file con estensione vstemplate radice *multi-progetto.* In questo esempio, il modello contiene due progetti `My Windows Application` e `My Class Library`. L'attributo `ProjectName` nell'elemento `ProjectTemplateLink` imposta il nome per [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] da assegnare a questo progetto. Se l'attributo non esiste, come nome del progetto viene usato il nome del file con estensione `ProjectName` *vstemplate.*

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

## <a name="see-also"></a>Vedi anche
- [Visual Studio riferimento allo schema del modello](../extensibility/visual-studio-template-schema-reference.md)
- [Creare modelli di progetto e di elementi](../ide/creating-project-and-item-templates.md)
- [Procedura: Creare modelli multi-progetto](../ide/how-to-create-multi-project-templates.md)