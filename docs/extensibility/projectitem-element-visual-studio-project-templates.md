---
title: Elemento ProjectItem (modelli Visual Studio Project) | Microsoft Docs
description: Informazioni sull'elemento ProjectItem per i modelli di progetto e su come accetta attributi diversi a seconda che il modello sia per un progetto o un elemento.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- ProjectItem element [Visual Studio project templates]
- <ProjectItem> element [Visual Studio project templates]
ms.assetid: 82879fbe-7756-42cd-9a07-c10edf5b4673
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d72272da255d51e5ef3423806744ef7c95e00193e6895daa9d96e702b48ef206
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121305295"
---
# <a name="projectitem-element-visual-studio-project-templates"></a>Elemento ProjectItem (Visual Studio di progetto)
Specifica un file incluso nel modello di progetto.

> [!NOTE]
> `ProjectItem`L'elemento accetta attributi diversi a seconda che il modello sia per un progetto o un elemento. In questo argomento viene illustrato `ProjectItem` l'elemento per i modelli di progetto. Per una spiegazione `ProjectItem` dell'elemento per i modelli di elemento, vedere Elemento [ProjectItem (Visual Studio Item Templates).](../extensibility/projectitem-element-visual-studio-item-templates.md)

 \<VSTemplate> \<TemplateContent>
 \<Project>
 \<ProjectItem>

## <a name="syntax"></a>Sintassi

```
<ProjectItem
    TargetFileName="TargetFileName.ext"
    ReplaceParameters="true/false"
    OpenInEditor="true/false"
    OpenInWebBrowser="true/false"
    OpenInHelpBrowser="true/false"
    OpenOrder="Value">
        FileName.ext
</ProjectItem>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

| Attributo | Descrizione |
|---------------------| - |
| `TargetFileName` | Attributo facoltativo.<br /><br /> Specifica il nome e il percorso dell'elemento di progetto quando viene creato un progetto dal modello. Questo attributo è utile per la creazione di una struttura di directory diversa dalla struttura di directory nel file *di.zip* modello o per l'uso della sostituzione dei parametri per creare un nome di elemento. |
| `ReplaceParameters` | Attributo facoltativo.<br /><br /> Valore booleano che specifica se l'elemento dispone di valori di parametro che devono essere sostituiti quando viene creato un progetto dal modello. Il valore predefinito è `false`. |
| `OpenInEditor` | Attributo facoltativo.<br /><br /> Valore booleano che specifica se l'elemento deve essere aperto nel rispettivo editor in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] quando viene creato un progetto dal modello.<br /><br /> Gli `OpenInWebBrowser` attributi e vengono `OpenInHelpBrowser` ignorati in un elemento con valore `OpenInEditor` `true` .<br /><br /> Il valore predefinito è `false`. |
| `OpenInWebBrowser` | Attributo facoltativo.<br /><br /> Valore booleano che specifica se l'elemento deve essere aperto Web browser quando viene creato un progetto dal modello.<br /><br /> Solo i file HTML e i file di testo locali del progetto possono essere aperti nel Web browser. Non è possibile aprire URL esterni con questo attributo.<br /><br /> Il valore predefinito è `false`. |
| `OpenInHelpBrowser` | Attributo facoltativo.<br /><br /> Valore booleano che specifica se l'elemento deve essere aperto nel visualizzatore della Guida quando viene creato un progetto dal modello.<br /><br /> Solo i file HTML e i file di testo locali del progetto possono essere aperti nel browser della Guida. Non è possibile aprire URL esterni con questo attributo.<br /><br /> Il valore predefinito è `false`. |
| `OpenOrder` | Attributo facoltativo.<br /><br /> Specifica un valore numerico che rappresenta l'ordine in cui gli elementi verranno aperti nei rispettivi editor. Tutti i valori devono essere multipli di 10. Gli elementi con `OpenOrder` valori superiori vengono aperti per primi. |

### <a name="child-elements"></a>Elementi figlio
 Nessuno.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Progetto](../extensibility/project-element-visual-studio-templates.md)|Specifica i file o le directory da aggiungere al progetto.|

## <a name="text-value"></a>Valore di testo
 È necessario specificare un valore di testo.

 Oggetto che rappresenta il nome o il percorso di un file nel modello `string` *.zip* file.

## <a name="remarks"></a>Commenti
 `ProjectItem` è un elemento figlio facoltativo di `Project` .

 L'attributo può essere usato per creare una struttura di directory diversa dalla struttura di directory nel `TargetFileName` file *.zip* modello. Ad esempio, se il file *MyFile.vb* esiste nella radice del file *.zip* del modello, ma si vuole che il file sia inserito in una directory denominata *CustomFiles* in tutti i progetti creati dal modello, usare il codice XML seguente:

```xml
<ProjectItem TargetFileName="CustomFiles\MyFile.vb">MyFile.vb</ProjectItem>
```

 `TargetFileName`L'attributo può essere usato anche per rinominare i file che contengono caratteri internazionali nei relativi nomi file. Ad esempio, un file *.zip* modello non può contenere nomi di file con caratteri Unicode, quindi il file deve essere rinominato prima di poter essere compresso in un file *.zip.* `TargetFileName`L'attributo può essere usato per impostare nuovamente il nome del file sul nome del file Unicode originale.

 `TargetFileName`L'attributo può essere usato anche per rinominare i file con parametri. La procedura seguente illustra come rinominare il file *MyFile.vb,* presente nella directory radice del file.zipmodello, *in* un nome di file basato sul nome del progetto.

### <a name="to-rename-files-with-parameters"></a>Per rinominare i file con parametri

1. Usare il codice XML seguente nel file *con estensione vstemplate:*

   ```xml
   <ProjectItem TargetFileName="$safeprojectname$.vb">MyFile.vb</ProjectItem>
   ```

2. Aprire il file di progetto *(con estensione vbproj* per [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] un progetto) in un editor di testo o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

3. Individuare la riga nel file di progetto simile al codice XML seguente:

   ```xml
   <Compile Include="MyFile.vb">
   ```

4. Sostituire la riga di codice con il codice XML seguente:

   ```xml
   <Compile Include="$safeprojectname$.vb">
   ```

    Quando viene creato un progetto da questo modello, il nome del file sarà basato sul nome immesso dall'utente nella finestra di dialogo Nuovo **Project,** con tutti gli spazi e i caratteri non sicuri rimossi. Per altre informazioni, vedere [Parametri del modello.](../ide/template-parameters.md)

## <a name="example"></a>Esempio
 L'esempio seguente mostra i metadati per un modello di progetto per [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] un'applicazione.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyStarterKit.csproj">
            <ProjectItem ReplaceParameters="true">Form1.cs<ProjectItem>
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
- [Creare modelli di progetto e di elementi](../ide/creating-project-and-item-templates.md)
- [Parametri di modelli](../ide/template-parameters.md)
- [Elemento ProjectItem (modelli di elemento di Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)
