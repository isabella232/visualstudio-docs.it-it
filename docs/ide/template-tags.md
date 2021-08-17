---
title: Aggiungere o modificare tag nei modelli di progetto
description: Informazioni su come aggiungere o modificare tag nei modelli di progetto in Visual Studio.
ms.date: 04/30/2019
author: minsa110
ms.author: somin
manager: jmartens
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- item templates, updating
- Visual Studio templates, updating
- project templates, updating
- updating templates [Visual Studio]
- template tagging, updating
- template tags, updating
ms.openlocfilehash: 515d6ff5e489ce7d586eb29682b817d63008fd0bf90e2f3eda7a7138e7dd0240
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121386967"
---
# <a name="add-tags-to-project-templates"></a>Aggiungere tag ai modelli di progetto

A partire da [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/) versione 16.1 Preview 2, è possibile aggiungere tag per il linguaggio, la piattaforma e il tipo di progetto ai modelli di progetto. 

I tag vengono usati in due posizioni nella **finestra di dialogo Project** nuova finestra di dialogo:

- I tag vengono visualizzati sotto la descrizione del modello.

   ![Modello di progetto con i tag nella finestra di dialogo Nuovo progetto](media/npd-item-with-template-tags.png)

- I tag consentono operazioni di ricerca e filtro per i modelli.

   ![Ricerca e filtro nella finestra di dialogo Nuovo progetto](media/npd-search-and-filter.png)

È possibile aggiungere tag aggiornando il file XML con estensione *vstemplate*. È possibile usare i tag modello inclusi in Visual Studio o creare tag modello personalizzati. I tag modello vengono visualizzati solo nella finestra di dialogo **Nuovo progetto** di Visual Studio 2019. I tag modello non influiscono sulla modalità di rendering del modello nelle versioni precedenti di Visual Studio.

## <a name="add-or-edit-tags"></a>Aggiungere o modificare tag

È possibile aggiungere o modificare tag nel file XML con estensione *vstemplate* del modello di progetto quando si esegue una delle azioni seguenti:

* [Creare un nuovo modello di progetto](how-to-create-project-templates.md) usando l'Esportazione guidata modelli.
* [Aggiornare il modello di progetto esistente.](how-to-update-existing-templates.md)
* [Creare un nuovo modello di progetto VSIX.](../extensibility/getting-started-with-the-vsix-project-template.md)

## <a name="syntax"></a>Sintassi

```xml
<LanguageTag> Language Name </LanguageTag>
<PlatformTag> Platform Name </PlatformTag>
<ProjectTypeTag> Project Type </ProjectTypeTag>
```

## <a name="attributes"></a>Attributi

È possibile usare gli attributi facoltativi seguenti in scenari utente avanzati:

|Attributo|Descrizione|
|---------------|-----------------|
|`Package`|GUID che specifica l'ID del pacchetto di Visual Studio.|
|`ID`|Specifica l'ID di risorsa di Visual Studio.|

Sintassi:

```xml
<LanguageTag Package="{PackageID}" ID="ResourceID" />
<PlatformTag Package="{PackageID}" ID="ResourceID" />
<ProjectTypeTag Package="{PackageID}" ID="ResourceID" />
```

## <a name="elements"></a>Elementi

### <a name="child-elements"></a>Elementi figlio

Nessuno.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|(Obbligatorio) Classifica il modello in base alla categoria e ne definisce la modalità di visualizzazione nella finestra di dialogo **Nuovo progetto** o **Aggiungi nuovo elemento**.|

## <a name="text-value"></a>Valore di testo

È richiesto un valore di testo, a meno che non si usino gli attributi `Package` e `ID`.

Il testo fornisce il nome del modello.

## <a name="built-in-tags"></a>Tag predefiniti

Visual Studio offre un elenco di tag predefiniti. Quando si aggiunge un tag predefinito, il tag esegue il rendering di una risorsa localizzata. 

L'elenco seguente include i tag predefiniti disponibili in Visual Studio. I valori corrispondenti sono visualizzati tra parentesi.

| Tag di lingua | Tag della piattaforma | Project tipo di tag |
| -- | -- | -- |
| C++ (`cpp`) | Android (`android`) | Cloud (`cloud`) |
| C# (`csharp`) | Azure (`azure`) | Console (`console`) |
| F# (`fsharp`) | iOS (`ios`) | Desktop (`desktop`) |
| Java (`java`) | Linux (`linux`) | Estensioni (`extension`) |
| JavaScript (`javascript`) | macOS (`macos`) | Giochi (`games`) |
| Python (`python`) | tvOS (`tvos`) | IoT (`iot`) |
| Query Language (`querylanguage`) | Windows (`windows`) | Libreria (`library`) |
| TypeScript (`typescript`) | Xbox (`xbox`) | Machine Learning (`machinelearning`) |
| Visual Basic (`visualbasic`) | | Dispositivi mobili (`mobile`) |
| | | Office (`office`) |
| | | Altro (`other`) |
| | | Servizio (`service`) |
| | | Test (`test`) |
| | | UWP (`uwp`) |
| | | Web (`web`) |

## <a name="example"></a>Esempio

L'esempio seguente mostra i metadati per un modello di progetto per un'applicazione Visual C#:

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>csharp</ProjectType>
        <LanguageTag>csharp</LanguageTag>
        <PlatformTag>windows</PlatformTag>
        <PlatformTag>linux</PlatformTag>
        <PlatformTag>My Platform</PlatformTag>
        <ProjectTypeTag>console</ProjectTypeTag>
        <ProjectTypeTag>desktop</ProjectTypeTag>
    </TemplateData>
    <TemplateContent>
        <Project File="MyTemplate.csproj">
            <ProjectItem>Form1.cs<ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>
            <ProjectItem>Properties\Resources.resx</ProjectItem>
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>
            <ProjectItem>Properties\Settings.settings</ProjectItem>
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Vedi anche

- [Visual Studio sullo schema del modello](../extensibility/visual-studio-template-schema-reference.md)
- [Creare modelli di progetto e di elementi](creating-project-and-item-templates.md)
- [Personalizzare modelli di progetto e modelli di elemento](customizing-project-and-item-templates.md)
- [Introduzione al modello di progetto VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)
