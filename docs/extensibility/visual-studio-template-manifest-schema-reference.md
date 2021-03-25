---
title: Riferimenti allo schema del manifesto dei modelli di Visual Studio | Microsoft Docs
description: Questo riferimento allo schema descrive il formato dei file manifesto dei modelli di Visual Studio generati per i modelli di progetto o di elemento di Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 033e735b93a534164d96cf47d6412c609525ad8f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062499"
---
# <a name="visual-studio-template-manifest-schema-reference"></a>Riferimento allo schema del manifesto del modello di Visual Studio
Questo schema descrive il formato dei file manifesto del modello di Visual Studio (con *estensione vstman*) generati per i modelli di progetto o di elemento di Visual Studio. Lo schema descrive anche il percorso e altre informazioni rilevanti sul modello.

 : Poiché sono presenti directory di modelli di elemento e di progetto separate, un manifesto non deve mai includere una combinazione di modelli di elemento e di progetto.

> [!IMPORTANT]
> Questo manifesto è disponibile a partire da Visual Studio 2017.

## <a name="vstemplatemanifest-element"></a>Elemento VSTemplateManifest
 Elemento radice del manifesto.

### <a name="attributes"></a>Attributi

- **Version**: stringa che rappresenta la versione del manifesto del modello. Obbligatorio.

- **Locale**: stringa che rappresenta le impostazioni locali o le impostazioni locali del manifesto del modello. Il valore delle impostazioni locali si applica a tutti i modelli. È necessario utilizzare un manifesto separato per ogni impostazione locale. facoltativo.

### <a name="child-elements"></a>Elementi figlio

- **VSTemplateContainer** Opzionale.

- **VSTemplateDir** Opzionale.

### <a name="parent-element"></a>Elemento padre
 Nessuna.

## <a name="vstemplatecontainer"></a>VSTemplateContainer
 Contenitore degli elementi del manifesto del modello. Un manifesto dispone di un contenitore di modelli per ogni modello definito.

### <a name="attributes"></a>Attributi
 **VSTemplateType**: valore stringa che specifica il tipo del modello ( `"Project"` , `"Item"` o `"ProjectGroup"` ). Necessario

### <a name="child-elements"></a>Elementi figlio

- **RelativePathOnDisk**: percorso relativo del file modello su disco. Questo percorso definisce anche il posizionamento del modello nell'albero dei modelli visualizzato nella finestra di dialogo **nuovo progetto** o **nuovo elemento** . Per i modelli distribuiti come una directory e singoli file, questo percorso si riferisce alla directory contenente i file modello. Per i modelli distribuiti come file con *estensione zip* , questo percorso deve corrispondere al percorso del file con *estensione zip* .

- * * VSTemplateHeader: elemento [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) che descrive l'intestazione.

### <a name="parent-element"></a>Elemento padre
 **VSTemplateManifest**

## <a name="vstemplatedir"></a>VSTemplateDir
 Descrive la directory in cui si trova il modello. Un manifesto può contenere più voci **VSTemplateDir** per fornire il nome localizzato e l'ordinamento delle directory per controllarne l'aspetto nell'albero delle categorie di modelli.

 A causa della loro progettazione, le voci **VSTemplateDir** dovrebbero essere visualizzate solo in manifesti non locali specificati.

### <a name="attributes"></a>Attributi
 Nessuna.

### <a name="child-elements"></a>Elementi figlio

- **RelativePath**: percorso del modello. Può essere presente una sola voce per ogni percorso, quindi il primo vincerà per tutti i manifesti.

- **Localizzated**: elemento **NameDescriptionIcon** che specifica il nome localizzato. facoltativo.

- **SortOrder**: stringa che specifica il tipo di ordinamento. facoltativo.

- **ParentFolderOverrideName**: nome sottoposto a override della cartella padre. facoltativo. Questo elemento ha un attributo **Name** , che è un valore stringa che specifica il nome.

### <a name="parent-element"></a>Elemento padre
 **VSTemplateManifest**

## <a name="namedescriptionicon"></a>NameDescriptionIcon
 Specifica il nome e la descrizione, possibilmente per i modelli localizzati. Vedere **localizzaname** sopra.

### <a name="attributes"></a>Attributi

- **Package**: valore stringa che specifica il pacchetto. facoltativo.

- **ID**: valore stringa che specifica l'ID. facoltativo.

### <a name="child-elements"></a>Elementi figlio
 Nessuna.

### <a name="parent-element"></a>Elemento padre
 **LocalizedName**

## <a name="examples"></a>Esempio
 Il codice seguente è un esempio di un file template *. vstman* del modello di progetto.

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

 Il codice seguente è un esempio di un file template *. vstman* di elemento.

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
