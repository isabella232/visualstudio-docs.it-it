---
title: Riferimenti allo schema del manifesto del modello di Visual Studio Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dbe46851d9df85569be796b4147217bd7db450ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697978"
---
# <a name="visual-studio-template-manifest-schema-reference"></a>Informazioni di riferimento sullo schema del manifesto del modello di Visual StudioVisual Studio template manifest schema reference
In questo schema viene descritto il formato dei file di manifesto del modello di Visual Studio (*con estensione vstman*) generati per i modelli di progetto o di elemento di Visual Studio. Lo schema descrive anche il percorso e altre informazioni rilevanti sul modello.

 : poiché sono presenti directory separate di modelli di progetto e di elemento, un manifesto non deve mai avere una combinazione di modelli di elemento e di progetto.

> [!IMPORTANT]
> Questo manifesto è disponibile a partire da Visual Studio 2017.This manifest is available starting in Visual Studio 2017.

## <a name="vstemplatemanifest-element"></a>VSTemplateManifest (elemento)
 Elemento radice del manifesto.

### <a name="attributes"></a>Attributi

- **Versione**: Una stringa che rappresenta la versione del manifesto del modello. Obbligatorio.

- **Locale**: stringa che rappresenta le impostazioni locali o le impostazioni locali del manifesto del modello. Il valore delle impostazioni locali si applica a tutti i modelli. È necessario utilizzare un manifesto separato per ogni impostazione locale. Facoltativa.

### <a name="child-elements"></a>Elementi figlio

- **VSTemplateContainer** Opzionale.

- **VSTemplateDir** Opzionale.

### <a name="parent-element"></a>Elemento padre
 No.

## <a name="vstemplatecontainer"></a>VSTemplateContainer
 Contenitore degli elementi del manifesto del modello. Un manifesto ha un contenitore di modelli per ogni modello che definisce.

### <a name="attributes"></a>Attributi
 **VSTemplateType**: valore stringa che specifica il`"Project"`tipo `"Item"`del `"ProjectGroup"`modello ( , , o ). Obbligatoria

### <a name="child-elements"></a>Elementi figlio

- **RelativePathOnDisk**: il percorso relativo del file modello su disco. Questa posizione definisce anche la posizione del modello nell'albero del modello mostrato nella finestra di dialogo **Nuovo progetto** o **Nuovo elemento.** Per i modelli distribuiti come directory e singoli file, questo percorso fa riferimento alla directory contenente i file modello. Per i modelli distribuiti come file *con estensione zip,* questo percorso deve essere il percorso del file *con estensione zip.*

- Un elemento [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) che descrive l'intestazione.

### <a name="parent-element"></a>Elemento padre
 **VSTemplateManifest**

## <a name="vstemplatedir"></a>VSTemplateDir
 Descrive la directory in cui si trova il modello. Un manifesto può contenere più **voci VSTemplateDir** per fornire il nome localizzato e l'ordinamento per le directory per controllarne l'aspetto nell'albero delle categorie di modelli.

 A causa della loro progettazione, le voci **VSTemplateDir** devono essere visualizzate solo nei manifesti specificati non per le impostazioni locali.

### <a name="attributes"></a>Attributi
 No.

### <a name="child-elements"></a>Elementi figlio

- **RelativePath**: Il percorso del modello. Ci può essere una sola voce per percorso, quindi la prima vincerà per tutti i manifesti.

- **LocalizedName**: Un elemento **NameDescriptionIcon** che specifica il nome localizzato. Facoltativa.

- **SortOrder**: Una stringa che specifica l'ordinamento. Facoltativa.

- **ParentFolderOverrideName**: il nome sottoposto a override della cartella padre. Facoltativa. Questo elemento ha un **Name** attributo, che è un valore stringa che specifica il nome.

### <a name="parent-element"></a>Elemento padre
 **VSTemplateManifest**

## <a name="namedescriptionicon"></a>NomeDescrizioneIcona
 Specifica il nome e la descrizione, possibilmente per i modelli localizzati. Vedere **LocalizedName** sopra.

### <a name="attributes"></a>Attributi

- **Package**: Un valore stringa che specifica il pacchetto. Facoltativa.

- **ID**: Un valore stringa che specifica l'ID. Facoltativa.

### <a name="child-elements"></a>Elementi figlio
 No.

### <a name="parent-element"></a>Elemento padre
 **LocalizedName (Nome localizzato)**

## <a name="examples"></a>Esempi
 Il codice seguente è un esempio di un file *con estensione vstman* del modello di progetto.

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Project">
    <RelativePathOnDisk>CSharp\1033\TestProjectTemplate</RelativePathOnDisk>
    <TemplateFileName>TestProjectTemplate.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>TestProjectTemplate</Name>
        <Description>TestProjectTemplate</Description>
        <Icon>TestProjectTemplate.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <SortOrder>1000</SortOrder>
        <TemplateID>aac0aeea-7883-4003-992f-937d53d70ab1</TemplateID>
        <CreateNewFolder>true</CreateNewFolder>
        <DefaultName>TestProjectTemplate</DefaultName>
        <ProvideDefaultName>true</ProvideDefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>

```

 Il codice seguente è un esempio di un file *con estensione vstman* del modello di elemento.

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Item">
    <RelativePathOnDisk>CSharp\1033\ItemTemplate1</RelativePathOnDisk>
    <TemplateFileName>ItemTemplate1.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>ItemTemplate1</Name>
        <Description>ItemTemplate1</Description>
        <Icon>ItemTemplate1.ico</Icon>
        <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
        <DefaultName>Class.cs</DefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>

```
