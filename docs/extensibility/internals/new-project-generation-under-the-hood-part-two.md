---
title: 'Nuova Project generazione: Under the Hood, part two | Microsoft Docs'
description: Esaminare in dettaglio cosa accade nell'ambiente Visual Studio di sviluppo integrato (IDE) durante la creazione del proprio tipo di progetto (parte 2 di 2).
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 73ce91d8-0ab1-4a1f-bf12-4d3c49c01e13
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 56e1fa13846525221ec96dca3a8b744590e1dc8d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122042257"
---
# <a name="new-project-generation-under-the-hood-part-two"></a>Generazione nuovo progetto: Dietro le quinte, seconda parte

In New Project Generation: Under the Hood, Part One è stato illustrato come viene popolata la finestra di dialogo New Project.In [New Project Generation: Under the Hood, Part One](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) we saw how the New **Project** dialog Box is populated. Si supponga di aver selezionato un'applicazione **Visual C# Windows,**  compilato le caselle di testo Nome e **Posizione** e aver fatto clic su OK.

## <a name="generating-the-solution-files"></a>Generazione dei file di soluzione
 La scelta di un modello di applicazione indica di decomprimere e aprire il file con estensione vstemplate corrispondente e di avviare un modello per interpretare i [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] comandi XML in questo file. Questi comandi creano progetti ed elementi di progetto nella soluzione nuova o esistente.

 Il modello decomprime i file di origine, denominati modelli di elemento, dalla stessa .zip che contiene il file con estensione vstemplate. Il modello copia questi file nel nuovo progetto, personalizzandoli di conseguenza.

### <a name="template-parameter-replacement"></a>Sostituzione dei parametri del modello
 Quando il modello copia un modello di elemento in un nuovo progetto, sostituisce tutti i parametri del modello con stringhe per personalizzare il file. Un parametro di modello è un token speciale preceduto e seguito da un simbolo del dollaro, ad esempio $date$.

 Si esamini un modello di elemento di progetto tipico. Estrarre ed esaminare Program.cs nella cartella Programmi\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip.

```csharp
using System;
using System.Collections.Generic;
using System.Windows.Forms;

namespace $safeprojectname$
{
    static class Program
    {
        // source code deleted here for brevity
    }
}
```

Se si crea un nuovo Windows di applicazione denominato Simple, il modello sostituisce il parametro `$safeprojectname$` con il nome del progetto.

```csharp
using System;
using System.Collections.Generic;
using System.Windows.Forms;

namespace Simple
{
    static class Program
    {
        // source code deleted here for brevity
    }
}
```

 Per un elenco completo dei parametri di modello, vedere [Parametri del modello](../../ide/template-parameters.md).

## <a name="a-look-inside-a-vstemplate-file"></a>Un'occhiata all'interno di un oggetto . VSTemplate File
 Un file con estensione vstemplate di base ha questo formato

```xml
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">
    <TemplateData>
    </TemplateData>
    <TemplateContent>
    </TemplateContent>
</VSTemplate>
```

 È stata osservata \<TemplateData> la sezione in New Project [Generation: Under the Hood, Part One](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md). I tag in questa sezione vengono usati per controllare l'aspetto della finestra **di Project** di dialogo.

 I tag nella sezione \<TemplateContent> controllano la generazione di nuovi progetti ed elementi di progetto. Ecco la sezione \<TemplateContent> del file cswindowsapplication.vstemplate nella cartella \Programmi\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip.

```xml
<TemplateContent>
  <Project File="WindowsApplication.csproj" ReplaceParameters="true">
    <ProjectItem ReplaceParameters="true"
      TargetFileName="Properties\AssemblyInfo.cs">
      AssemblyInfo.cs
    </ProjectItem>
    <ProjectItem TargetFileName="Properties\Resources.resx">
      Resources.resx
    </ProjectItem>
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Resources.Designer.cs">
      Resources.Designer.cs
    </ProjectItem>
    <ProjectItem TargetFileName="Properties\Settings.settings">
      Settings.settings
    </ProjectItem>
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Settings.Designer.cs">
      Settings.Designer.cs
    </ProjectItem>
    <ProjectItem ReplaceParameters="true" OpenInEditor="true">
      Form1.cs
    </ProjectItem>
    <ProjectItem ReplaceParameters="true">
      Form1.Designer.cs
    </ProjectItem>
    <ProjectItem ReplaceParameters="true">
      Program.cs
    </ProjectItem>
  </Project>
</TemplateContent>
```

 Il \<Project> tag controlla la generazione di un progetto e il tag controlla la generazione di un elemento di \<ProjectItem> progetto. Se il parametro ReplaceParameters è true, il modello personalizza tutti i parametri del modello nel file o nell'elemento di progetto. In questo caso, tutti gli elementi del progetto vengono personalizzati, ad eccezione di Impostazioni.settings.

 Il parametro TargetFileName specifica il nome e il percorso relativo del file di progetto o dell'elemento risultante. In questo modo è possibile creare una struttura di cartelle per il progetto. Se non si specifica questo argomento, l'elemento di progetto avrà lo stesso nome del modello di elemento di progetto.

 La struttura Windows cartella dell'applicazione risultante è simile alla seguente:

 ![Screenshot della struttura Windows cartella dell'applicazione per la soluzione "Semplice" nel Visual Studio Esplora soluzioni.](../../extensibility/internals/media/simplesolution.png)

 Il primo \<Project> e l'unico tag nel modello sono:

```xml
<Project File="WindowsApplication.csproj" ReplaceParameters="true">
```

 Questo indica al modello New Project di creare il file di progetto Simple.csproj copiando e personalizzando l'elemento del modello windowsapplication.csproj.

### <a name="designers-and-references"></a>Finestre di progettazione e riferimenti
 È possibile vedere nel Esplora soluzioni che la cartella Proprietà è presente e contiene i file previsti. Ma per quanto riguarda i riferimenti al progetto e le dipendenze dei file di progettazione, ad esempio Resources.Designer.cs in Resources.resx e Form1.Designer.cs in Form1.cs?  Questi vengono impostati nel file Simple.csproj quando viene generato.

 Di seguito è riportato \<ItemGroup> il file simple.csproj che crea i riferimenti al progetto:

```xml
<ItemGroup>
    <Reference Include="System" />
    <Reference Include="System.Data" />
    <Reference Include="System.Deployment" />
    <Reference Include="System.Drawing" />
    <Reference Include="System.Windows.Forms" />
    <Reference Include="System.Xml" />
</ItemGroup>
```

 È possibile vedere che si tratta dei sei riferimenti al progetto visualizzati nel Esplora soluzioni. Ecco una sezione di un altro \<ItemGroup> oggetto . Molte righe di codice sono state eliminate per maggiore chiarezza. Questa sezione rende Impostazioni. Designer.cs dipende da Impostazioni.settings:

```xml
<ItemGroup>
    <Compile Include="Properties\Settings.Designer.cs">
        <DependentUpon>Settings.settings</DependentUpon>
    </Compile>
</ItemGroup>
```

## <a name="see-also"></a>Vedi anche

- [Generazione nuovo progetto: Dietro le quinte, prima parte](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)
- [MSBuild](../../msbuild/msbuild.md)
