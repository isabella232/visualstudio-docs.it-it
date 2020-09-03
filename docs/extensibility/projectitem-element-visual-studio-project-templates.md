---
title: Elemento ProjectItem (modelli di progetto di Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
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
ms.openlocfilehash: 943f50823892e3cd942709bdcd4556b65c006b58
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85770314"
---
# <a name="projectitem-element-visual-studio-project-templates"></a>Elemento ProjectItem (modelli di progetto di Visual Studio)
Specifica un file incluso nel modello di progetto.

> [!NOTE]
> L' `ProjectItem` elemento accetta attributi diversi a seconda che il modello sia per un progetto o un elemento. In questo argomento viene illustrato l' `ProjectItem` elemento per i modelli di progetto. Per una spiegazione dell' `ProjectItem` elemento per i modelli di elemento, vedere [elemento ProjectItem (modelli di elemento di Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md).

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

### <a name="attributes"></a>Attributes

| Attributo | Descrizione |
|---------------------| - |
| `TargetFileName` | Attributo facoltativo.<br /><br /> Specifica il nome e il percorso dell'elemento di progetto quando viene creato un progetto dal modello. Questo attributo è utile per creare una struttura di directory diversa dalla struttura di directory nel file con *estensione zip* del modello oppure per usare la sostituzione dei parametri per creare un nome di elemento. |
| `ReplaceParameters` | Attributo facoltativo.<br /><br /> Valore booleano che specifica se l'elemento contiene valori di parametro che devono essere sostituiti quando viene creato un progetto dal modello. Il valore predefinito è `false`. |
| `OpenInEditor` | Attributo facoltativo.<br /><br /> Valore booleano che specifica se l'elemento deve essere aperto nel rispettivo editor in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] quando viene creato un progetto dal modello.<br /><br /> Gli `OpenInWebBrowser` `OpenInHelpBrowser` attributi e vengono ignorati in un elemento con un `OpenInEditor` valore di `true` .<br /><br /> Il valore predefinito è `false`. |
| `OpenInWebBrowser` | Attributo facoltativo.<br /><br /> Valore booleano che specifica se l'elemento deve essere aperto Web browser quando viene creato un progetto dal modello.<br /><br /> Nel Web browser è possibile aprire solo file HTML e file di testo locali per il progetto. Non è possibile aprire URL esterni con questo attributo.<br /><br /> Il valore predefinito è `false`. |
| `OpenInHelpBrowser` | Attributo facoltativo.<br /><br /> Valore booleano che specifica se l'elemento deve essere aperto nel Visualizzatore della guida quando viene creato un progetto dal modello.<br /><br /> Solo i file HTML e i file di testo locali per il progetto possono essere aperti nel browser della guida. Non è possibile aprire URL esterni con questo attributo.<br /><br /> Il valore predefinito è `false`. |
| `OpenOrder` | Attributo facoltativo.<br /><br /> Specifica un valore numerico che rappresenta l'ordine in cui gli elementi verranno aperti nei rispettivi editor. Tutti i valori devono essere multipli di 10. Gli elementi con `OpenOrder` valori più alti vengono aperti per primi. |

### <a name="child-elements"></a>Elementi figlio
 Nessuno.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Progetto](../extensibility/project-element-visual-studio-templates.md)|Specifica i file o le directory da aggiungere al progetto.|

## <a name="text-value"></a>Valore di testo
 È necessario specificare un valore di testo.

 Oggetto `string` che rappresenta il nome o il percorso di un file nel file con *estensione zip* del modello.

## <a name="remarks"></a>Osservazioni
 `ProjectItem` è un elemento figlio facoltativo di `Project` .

 L' `TargetFileName` attributo può essere usato per creare una struttura di directory diversa dalla struttura di directory nel file con *estensione zip* del modello. Se, ad esempio, il file MyFile *. vb* è presente nella radice del file con estensione *zip* del modello, ma si vuole inserire il file in una directory denominata *CustomFiles* in tutti i progetti creati dal modello, usare il codice XML seguente:

```xml
<ProjectItem TargetFileName="CustomFiles\MyFile.vb">MyFile.vb</ProjectItem>
```

 L' `TargetFileName` attributo può essere usato anche per rinominare i file che contengono caratteri internazionali nei rispettivi nomi file. Un file con estensione *zip* di un modello, ad esempio, non può contenere nomi di file con caratteri Unicode, quindi il file deve essere rinominato prima di poter essere compresso in un file con *estensione zip* . L' `TargetFileName` attributo può essere utilizzato per impostare di nuovo il nome file sul nome del file Unicode originale.

 L' `TargetFileName` attributo può essere utilizzato anche per rinominare i file con parametri. Nella procedura seguente viene illustrato come rinominare il file MyFile *. vb*, presente nella directory radice del file con estensione *zip* del modello, in un nome di file in base al nome del progetto.

### <a name="to-rename-files-with-parameters"></a>Per rinominare i file con parametri

1. Usare il codice XML seguente nel file con *estensione vstemplate* :

   ```xml
   <ProjectItem TargetFileName="$safeprojectname$.vb">MyFile.vb</ProjectItem>
   ```

2. Aprire il file di progetto (*VBPROJ* per un [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] progetto) in un editor di testo o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

3. Individuare la riga nel file di progetto simile al codice XML seguente:

   ```xml
   <Compile Include="MyFile.vb">
   ```

4. Sostituire la riga di codice con il codice XML seguente:

   ```xml
   <Compile Include="$safeprojectname$.vb">
   ```

    Quando viene creato un progetto da questo modello, il nome del file sarà basato sul nome immesso dall'utente nella finestra di dialogo **nuovo progetto** , con tutti i caratteri e gli spazi unsafe rimossi. Per ulteriori informazioni, vedere [parametri di modello](../ide/template-parameters.md).

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono illustrati i metadati per un modello di progetto per un' [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] applicazione.

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
- [Riferimento allo schema di modello di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creare modelli di progetto e di elementi](../ide/creating-project-and-item-templates.md)
- [Parametri di modelli](../ide/template-parameters.md)
- [Elemento ProjectItem (modelli di elemento di Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)
