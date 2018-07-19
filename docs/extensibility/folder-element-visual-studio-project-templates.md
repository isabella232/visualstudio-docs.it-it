---
title: Elemento Folder (modelli di progetto di Visual Studio) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Folder
helpviewer_keywords:
- Folder element [Visual Studio project templates]
ms.assetid: 558e3d41-0db5-4c44-82bb-6bb87892b093
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ec8a5520716f6073d49ab2b5a64becfb760092d2
ms.sourcegitcommit: f685fa5e2df9dc307bf1230dd9dc3288aaa408b5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36234923"
---
# <a name="folder-element-visual-studio-project-templates"></a>Elemento Folder (modelli di progetto Visual Studio)
Specifica una cartella in cui verrà aggiunto al progetto.  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<Project>  
 \<Cartella >  
  
## <a name="syntax"></a>Sintassi  
  
```  
<Folder Name="Project Folder">  
    <Folder> ... </Folder>  
    <ProjectItem> ... </ProjectItem>  
</Folder>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Name`|Attributo obbligatorio.<br /><br /> Il nome della cartella del progetto.|  
|`TargetFolderName`|Attributo facoltativo.<br /><br /> Specifica il nome da assegnare alla cartella quando viene creato un progetto dal modello. Questo attributo è utile per l'uso di sostituzione dei parametri per creare un nome di cartella o una cartella con una stringa internazionale di denominazione che non è possibile usare direttamente nel file con estensione zip.|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|`Folder`|Specifica una cartella da aggiungere al progetto. `Folder` gli elementi possono contenere figlio `Folder` elementi.|  
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|Specifica un file da aggiungere al progetto.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Progetto](../extensibility/project-element-visual-studio-templates.md)|Elemento figlio facoltativo degli [TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md).|  
  
## <a name="remarks"></a>Note  
 `Folder` è un elemento figlio facoltativo di `Project`.  
  
 Per organizzare gli elementi del progetto in cartelle in un modello, è possibile usare uno qualsiasi dei metodi seguenti:  
  
-   Includere le cartelle nel file zip del modello e aggiungerli al progetto nel file vstemplate, specificando il percorso del file nei `ProjectItem` elementi, con nessuna `Folder` elementi. Questo è il metodo consigliato. Ad esempio:  
  
     `...`  
  
     `<ProjectItem>\Folder\item.cs</ProjectItem>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
-   Includere le cartelle nel file zip del modello e aggiungerli al progetto nel file con estensione vstemplate con `Folder` elementi. Ad esempio:  
  
     `...`  
  
     `<Folder name="Folder">`  
  
     `<ProjectItem>item.cs</ProjectItem>`  
  
     `</Folder>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
-   Non includere le cartelle nel file zip del modello, ma aggiungere cartelle utilizzando il `TargetFileName` attributo del `ProjectItem` elemento. Ad esempio:  
  
     `...`  
  
     `<ProjectItem TargetFileName="\Folder\item.cs">item.cs</ProjectItem>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente vengono illustrati i metadati per un modello di progetto per un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] applicazione Windows.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyTemplate.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <Folder Name="Properties">  
                <ProjectItem>AssemblyInfo.cs</ProjectItem>  
                <ProjectItem>Resources.resx</ProjectItem>  
                <ProjectItem>Resources.Designer.cs</ProjectItem>  
                <ProjectItem>Settings.settings</ProjectItem>  
                <ProjectItem>Settings.Designer.cs</ProjectItem>  
            </Folder>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)   
 [Elemento ProjectItem (modelli di elemento di Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)