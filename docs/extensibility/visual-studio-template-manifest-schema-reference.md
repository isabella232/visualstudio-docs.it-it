---
title: Visual Studio riferimento allo schema del manifesto del modello | Microsoft Docs
description: Questo riferimento allo schema descrive il formato dei file manifesto Visual Studio modello generati per i Visual Studio di progetto o di elemento.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 259d2dd050f4681053f331bfd4ec39dd7b214059
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905384"
---
# <a name="visual-studio-template-manifest-schema-reference"></a>Visual Studio sullo schema del manifesto del modello
Questo schema descrive il formato dei file Visual Studio del modello di distribuzione (con estensione *vstman)* generati per i Visual Studio di progetto o di elemento. Lo schema descrive anche il percorso e altre informazioni rilevanti sul modello.

 : poiché sono presenti directory di modelli di elemento e di progetto separate, un manifesto non deve mai avere una combinazione di modelli di elemento e di progetto.

> [!IMPORTANT]
> Questo manifesto è disponibile a partire Visual Studio 2017.

## <a name="vstemplatemanifest-element"></a>Elemento VSTemplateManifest
 Elemento radice del manifesto.

### <a name="attributes"></a>Attributi

- **Version:** stringa che rappresenta la versione del manifesto del modello. Obbligatorio.

- **Locale:** stringa che rappresenta le impostazioni locali o le impostazioni locali del manifesto del modello. Il valore delle impostazioni locali si applica a tutti i modelli. È necessario usare un manifesto separato per ogni impostazione locale. facoltativo.

### <a name="child-elements"></a>Elementi figlio

- **VsTemplateContainer** Opzionale.

- **VSTemplateDir** Opzionale.

### <a name="parent-element"></a>Elemento padre
 Nessuno.

## <a name="vstemplatecontainer"></a>VsTemplateContainer
 Contenitore degli elementi del manifesto del modello. Un manifesto ha un contenitore di modelli per ogni modello definito.

### <a name="attributes"></a>Attributi
 **VSTemplateType:** valore stringa che specifica il tipo del modello ( `"Project"` `"Item"` , o `"ProjectGroup"` ). Obbligatoria

### <a name="child-elements"></a>Elementi figlio

- **RelativePathOnDisk:** percorso relativo del file modello su disco. Questo percorso definisce anche la posizione del modello nell'albero del modello visualizzato nella **finestra di dialogo Nuovo progetto** o **Nuovo** elemento. Per i modelli distribuiti come directory e singoli file, questo percorso fa riferimento alla directory contenente i file modello. Per i modelli distribuiti *come file.zip,* questo percorso deve essere il percorso del file *.zip.*

- **VSTemplateHeader: elemento [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) che descrive l'intestazione.

### <a name="parent-element"></a>Elemento padre
 **VSTemplateManifest**

## <a name="vstemplatedir"></a>VSTemplateDir
 Descrive la directory in cui si trova il modello. Un manifesto può contenere più **voci VSTemplateDir** per fornire il nome localizzato e l'ordinamento per consentire alle directory di controllarne l'aspetto nell'albero delle categorie del modello.

 A causa della progettazione, **le voci VSTemplateDir** dovrebbero essere visualizzate solo nei manifesti non specificati dalle impostazioni locali.

### <a name="attributes"></a>Attributi
 Nessuno.

### <a name="child-elements"></a>Elementi figlio

- **RelativePath:** percorso del modello. Può essere presente una sola voce per ogni percorso, quindi la prima verrà vinca per tutti i manifesti.

- **LocalizedName:** elemento **NameDescriptionIcon** che specifica il nome localizzato. facoltativo.

- **SortOrder:** stringa che specifica l'ordinamento. facoltativo.

- **ParentFolderOverrideName:** nome sottoposto a override della cartella padre. facoltativo. Questo elemento ha un **attributo Name,** ovvero un valore stringa che specifica il nome.

### <a name="parent-element"></a>Elemento padre
 **VSTemplateManifest**

## <a name="namedescriptionicon"></a>NameDescriptionIcon
 Specifica il nome e la descrizione, possibilmente per i modelli localizzati. Vedere **LocalizedName sopra.**

### <a name="attributes"></a>Attributi

- **Package:** valore stringa che specifica il pacchetto. facoltativo.

- **ID:** valore stringa che specifica l'ID. facoltativo.

### <a name="child-elements"></a>Elementi figlio
 Nessuno.

### <a name="parent-element"></a>Elemento padre
 **LocalizedName**

## <a name="examples"></a>Esempio
 Il codice seguente è un esempio di file con estensione *vstman* del modello di progetto.

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

 Il codice seguente è un esempio di file con estensione *vstman* del modello di elemento.

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
