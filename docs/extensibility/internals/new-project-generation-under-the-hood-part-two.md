---
title: 'New Project Generation: Under the Hood, Part Two | Microsoft Docs'
description: Esaminare in dettaglio cosa accade nell'ambiente di sviluppo integrato (IDE) di Visual Studio quando si crea un tipo di progetto personalizzato (parte 2 di 2).
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
ms.openlocfilehash: 77ee63fbc49554ad3d9037f7d5bf3d19e4cf29f16ec43d384a0489da9ec06184
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121432352"
---
# <a name="new-project-generation-under-the-hood-part-two"></a>Generazione nuovo progetto: Dietro le quinte, seconda parte

In [New Project Generation: Under the Hood, Part One](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) è stato illustrato il modo in cui viene popolata la finestra di dialogo **Project** nuova generazione. Si supponga di aver selezionato un'applicazione **Visual C# Windows**,  di  aver compilato le caselle di testo Nome e Percorso e aver fatto clic su OK.

## <a name="generating-the-solution-files"></a>Generazione dei file della soluzione
 La scelta di un modello di applicazione indica di decomprimere e aprire il file con estensione vstemplate corrispondente e di avviare un modello per interpretare i [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] comandi XML in questo file. Questi comandi creano progetti ed elementi di progetto nella soluzione nuova o esistente.

 Il modello decomprime i file di origine, denominati modelli di elemento, dalla stessa .zip che contiene il file con estensione vstemplate. Il modello copia questi file nel nuovo progetto, personalizzandoli di conseguenza.

### <a name="template-parameter-replacement"></a>Sostituzione dei parametri di modello
 Quando il modello copia un modello di elemento in un nuovo progetto, sostituisce tutti i parametri del modello con stringhe per personalizzare il file. Un parametro di modello è un token speciale preceduto e seguito da un segno di dollaro, ad esempio $date$.

 Si esamini ora un tipico modello di elemento di progetto. Estrarre ed esaminare Program.cs nella cartella Programmi\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip.

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

Se si crea un nuovo Windows progetto di applicazione semplice, il modello sostituisce il `$safeprojectname$` parametro con il nome del progetto.

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

 Per un elenco completo dei parametri del modello, vedere [Parametri del modello.](../../ide/template-parameters.md)

## <a name="a-look-inside-a-vstemplate-file"></a>Oggetto che si trova all'interno di un oggetto . VSTemplate File
 Un file con estensione vstemplate di base ha questo formato

```xml
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">
    <TemplateData>
    </TemplateData>
    <TemplateContent>
    </TemplateContent>
</VSTemplate>
```

 È stata osservata \<TemplateData> la sezione in New Project [Generation: Under the Hood, Part One](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md). I tag in questa sezione vengono usati per controllare l'aspetto della finestra di **dialogo Project** nuova finestra di dialogo.

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

 Il \<Project> tag controlla la generazione di un progetto e il tag controlla la generazione di un elemento di \<ProjectItem> progetto. Se il parametro ReplaceParameters è true, il modello personalizza tutti i parametri del modello nel file di progetto o nell'elemento. In questo caso, tutti gli elementi del progetto vengono personalizzati, ad eccezione di Impostazioni.settings.

 Il parametro TargetFileName specifica il nome e il percorso relativo del file di progetto o dell'elemento risultante. In questo modo è possibile creare una struttura di cartelle per il progetto. Se non si specifica questo argomento, l'elemento di progetto avrà lo stesso nome del modello di elemento di progetto.

 La struttura di Windows dell'applicazione risultante è simile alla seguente:

 ![Screenshot della struttura Windows cartelle dell'applicazione per la soluzione "Semplice" nella Visual Studio Esplora soluzioni.](../../extensibility/internals/media/simplesolution.png)

 Il primo e \<Project> l'unico tag nel modello sono:

```xml
<Project File="WindowsApplication.csproj" ReplaceParameters="true">
```

 Questo indica al modello New Project di creare il file di progetto Simple.csproj copiando e personalizzando l'elemento modello windowsapplication.csproj.

### <a name="designers-and-references"></a>Finestre di progettazione e riferimenti
 È possibile vedere nel Esplora soluzioni che la cartella Proprietà è presente e contiene i file previsti. Ma quali sono i riferimenti al progetto e le dipendenze dei file di progettazione, ad esempio Da Resources.Designer.cs a Resources.resx e Da Form1.Designer.cs a Form1.cs?  Questi vengono impostati nel file Simple.csproj quando viene generato.

 Di seguito è riportato \<ItemGroup> il file di Simple.csproj che crea i riferimenti al progetto:

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

 È possibile vedere che si tratta dei sei riferimenti al progetto visualizzati nel Esplora soluzioni. Ecco una sezione di un altro \<ItemGroup> . Molte righe di codice sono state eliminate per maggiore chiarezza. In questa sezione vengono Impostazioni. Designer.cs dipende da Impostazioni.settings:

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
