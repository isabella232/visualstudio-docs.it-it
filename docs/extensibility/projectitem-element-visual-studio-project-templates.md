---
title: Elemento ProjectItem (modelli di progetto Visual Studio) Documenti Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- ProjectItem element [Visual Studio project templates]
- <ProjectItem> element [Visual Studio project templates]
ms.assetid: 82879fbe-7756-42cd-9a07-c10edf5b4673
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11052d8e585f1d06f6d787402001cfbbe2b6810f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701844"
---
# <a name="projectitem-element-visual-studio-project-templates"></a>Elemento ProjectItem (modelli di progetto Visual Studio)
Specifica un file incluso nel modello di progetto.

> [!NOTE]
> L'elemento `ProjectItem` accetta attributi diversi a seconda che il modello sia per un progetto o un elemento. In questo argomento `ProjectItem` viene illustrato l'elemento per i modelli di progetto. Per una spiegazione dell'elemento per i `ProjectItem` modelli di elemento, vedere Elemento [ProjectItem (modelli di elemento](../extensibility/projectitem-element-visual-studio-item-templates.md)di Visual Studio) .

 \<VSTemplate \<> TemplateContent \< \<> progetto> ProjectItem>

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
| `TargetFileName` | Attributo facoltativo.<br /><br /> Specifica il nome e il percorso dell'elemento di progetto quando viene creato un progetto dal modello. Questo attributo è utile per creare una struttura di directory diversa dalla struttura di directory nel file *.zip* del modello o per utilizzare la sostituzione dei parametri per creare un nome di elemento. |
| `ReplaceParameters` | Attributo facoltativo.<br /><br /> Valore booleano che specifica se l'elemento dispone di valori di parametro che devono essere sostituiti quando viene creato un progetto dal modello. Il valore predefinito è `false`. |
| `OpenInEditor` | Attributo facoltativo.<br /><br /> Valore booleano che specifica se l'elemento deve [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] essere aperto nel rispettivo editor quando viene creato un progetto dal modello.<br /><br /> Gli `OpenInWebBrowser` `OpenInHelpBrowser` attributi e vengono ignorati `OpenInEditor` su `true`un elemento con valore di .<br /><br /> Il valore predefinito è `false`. |
| `OpenInWebBrowser` | Attributo facoltativo.<br /><br /> Valore booleano che specifica se l'elemento deve essere aperto nel browser Web quando viene creato un progetto dal modello.<br /><br /> Solo i file HTML e i file di testo locali al progetto possono essere aperti nel browser Web. Gli URL esterni non possono essere aperti con questo attributo.<br /><br /> Il valore predefinito è `false`. |
| `OpenInHelpBrowser` | Attributo facoltativo.<br /><br /> Valore booleano che specifica se l'elemento deve essere aperto nel visualizzatore della Guida quando viene creato un progetto dal modello.<br /><br /> Solo i file HTML e i file di testo locali al progetto possono essere aperti nel browser della Guida. Gli URL esterni non possono essere aperti con questo attributo.<br /><br /> Il valore predefinito è `false`. |
| `OpenOrder` | Attributo facoltativo.<br /><br /> Specifica un valore numerico che rappresenta l'ordine in cui gli elementi verranno aperti nei rispettivi editor. Tutti i valori devono essere multipli di 10.All values must be multiples of 10. Gli elementi `OpenOrder` con valori più alti vengono aperti per primi. |

### <a name="child-elements"></a>Elementi figlio
 No.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Project](../extensibility/project-element-visual-studio-templates.md)|Specifica i file o le directory da aggiungere al progetto.|

## <a name="text-value"></a>Valore di testo
 È necessario specificare un valore di testo.

 Oggetto `string` che rappresenta il nome o il percorso di un file nel file *.zip* del modello.

## <a name="remarks"></a>Osservazioni
 `ProjectItem`è un elemento `Project`figlio facoltativo di .

 L'attributo `TargetFileName` può essere utilizzato per creare una struttura di directory diversa dalla struttura di directory nel file *.zip* del modello. Ad esempio, se il file *MyFile.vb* è presente nella radice del file *.zip* del modello, ma si desidera che il file venga inserito in una directory denominata *CustomFiles* in tutti i progetti creati dal modello, utilizzare il seguente codice XML:

```xml
<ProjectItem TargetFileName="CustomFiles\MyFile.vb">MyFile.vb</ProjectItem>
```

 L'attributo `TargetFileName` può essere utilizzato anche per rinominare i file che contengono caratteri internazionali nei relativi nomi di file. Ad esempio, un file *.zip* modello non può contenere nomi di file con caratteri Unicode, pertanto il file deve essere rinominato prima di poter essere compresso in un file *con estensione zip.* L'attributo `TargetFileName` può essere utilizzato per impostare il nome del file sul nome del file Unicode originale.

 L'attributo `TargetFileName` può essere utilizzato anche per rinominare i file con parametri. Nella procedura riportata di seguito viene illustrato come rinominare il file *MyFile.vb*, presente nella directory radice del file *con estensione zip* del modello, in un nome di file basato sul nome del progetto.

### <a name="to-rename-files-with-parameters"></a>Per rinominare i file con parametri

1. Utilizzare il seguente codice XML nel file *.vstemplate:*

   ```xml
   <ProjectItem TargetFileName="$safeprojectname$.vb">MyFile.vb</ProjectItem>
   ```

2. Aprire il file di progetto (*.vbproj* per un [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] progetto) in un editor di testo o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

3. Individuare la riga nel file di progetto simile al codice XML seguente:

   ```xml
   <Compile Include="MyFile.vb">
   ```

4. Sostituire la riga di codice con il codice XML seguente:

   ```xml
   <Compile Include="$safeprojectname$.vb">
   ```

    Quando viene creato un progetto da questo modello, il nome del file sarà basato sul nome immesso dall'utente nella finestra di dialogo **Nuovo progetto,** con tutti i caratteri non sicuri e gli spazi rimossi. Per ulteriori informazioni, vedere [Parametri del modello](../ide/template-parameters.md).

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono illustrati i [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] metadati per un modello di progetto per un'applicazione.

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

## <a name="see-also"></a>Vedere anche
- [Informazioni di riferimento sullo schema del modello di Visual StudioVisual Studio template schema reference](../extensibility/visual-studio-template-schema-reference.md)
- [Creare modelli di progetto e di elementi](../ide/creating-project-and-item-templates.md)
- [Parametri di modelli](../ide/template-parameters.md)
- [Elemento ProjectItem (modelli di elemento di Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)
