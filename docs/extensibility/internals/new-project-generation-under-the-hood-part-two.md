---
title: 'Nuova generazione di progetti: sotto il cofano, seconda parte Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 73ce91d8-0ab1-4a1f-bf12-4d3c49c01e13
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8692f2012e5f2733982f04e35a7fed415e49c636
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707013"
---
# <a name="new-project-generation-under-the-hood-part-two"></a>Generazione di un nuovo progetto: dietro le quinte, parte 2

In [New Project Generation: Sotto il cofano, la prima parte](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) abbiamo visto come viene popolata la finestra di dialogo Nuovo **progetto.** Si supponga di aver selezionato **un'applicazione Windows di Visual C,** compilato le **caselle** di testo Nome e **percorso** e si è fatto clic su OK.

## <a name="generating-the-solution-files"></a>Generazione dei file di soluzione
 La scelta di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] un modello di applicazione indica di decomprimere e aprire il file .vstemplate corrispondente e di avviare un modello per interpretare i comandi XML in questo file. Questi comandi creano progetti ed elementi di progetto nella soluzione nuova o esistente.

 Il modello decomprime i file di origine, denominati modelli di elemento, dalla stessa cartella .zip che contiene il file .vstemplate. Il modello copia questi file nel nuovo progetto, personalizzandoli di conseguenza.

### <a name="template-parameter-replacement"></a>Sostituzione dei parametri del modello
 Quando il modello copia un modello di elemento in un nuovo progetto, sostituisce tutti i parametri del modello con stringhe per personalizzare il file. Un parametro di modello è un token speciale preceduto e seguito da un simbolo del dollaro, ad esempio, $date.

 Esaminiamo un modello tipico di elemento di progetto. Estrarre ed esaminare Program.cs nella cartella File di programma , Microsoft Visual Studio 8 , Common7 , IDE , Project Templates , CSharp , Windows , 1033 , WindowsApplication.zip .

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

Se si crea un nuovo progetto di applicazione `$safeprojectname$` Windows denominato Simple, il modello sostituisce il parametro con il nome del progetto.

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

 Per un elenco completo dei parametri di modello, vedere [Parametri modello](../../ide/template-parameters.md).

## <a name="a-look-inside-a-vstemplate-file"></a>Uno sguardo all'interno di un file . VSTemplate File
 Un file .vstemplate di base ha questo formato

```xml
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">
    <TemplateData>
    </TemplateData>
    <TemplateContent>
    </TemplateContent>
</VSTemplate>
```

 Abbiamo esaminato \<la sezione templateData> nella sezione [New Project Generation: Under the Hood, Part One](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md). I tag in questa sezione vengono utilizzati per controllare l'aspetto della finestra di dialogo **Nuovo progetto.**

 I tag \<nella sezione> TemplateContent controllano la generazione di nuovi progetti ed elementi di progetto. Di seguito \<è riportata la sezione TemplateContent> del file cswindowsapplication.vstemplate nella cartella .

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
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Resources.Designer.cs">
      Resources.Designer.cs
    </ProjectItem>
    <ProjectItem TargetFileName="Properties\Settings.settings">
      Settings.settings
    </ProjectItem>
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Settings.Designer.cs">
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

 Il \<tag Project> controlla la generazione \<di un progetto, quindi il tag ProjectItem> controlla la generazione di un elemento di progetto. Se il parametro ReplaceParameters è true, il modello customizerà tutti i parametri del modello nel file o nell'elemento di progetto. In questo caso, tutti gli elementi del progetto vengono personalizzati, ad eccezione di Settings.settings.

 Il parametro TargetFileName consente di specificare il nome e il percorso relativo del file o dell'elemento di progetto risultante. Ciò consente di creare una struttura di cartelle per il progetto. Se non si specifica questo argomento, l'elemento di progetto avrà lo stesso nome del modello di elemento di progetto.

 La struttura di cartelle dell'applicazione Windows risultante è simile alla seguente:The resulting Windows application folder structure looks like this:

 ![SimpleSolution](../../extensibility/internals/media/simplesolution.png "SimpleSolution")

 Il primo \<e unico tag Project> nel modello legge:

```xml
<Project File="WindowsApplication.csproj" ReplaceParameters="true">
```

 In questo modo si indica al modello Nuovo progetto di creare il file di progetto Simple.csproj copiando e personalizzando l'elemento modello windowsapplication.csproj.

### <a name="designers-and-references"></a>Designer e riferimenti
 È possibile vedere in Esplora soluzioni che la cartella Proprietà è presente e contiene i file previsti. Ma per quanto riguarda i riferimenti al progetto e le dipendenze dei file della finestra di progettazione, ad esempio Resources.Designer.cs in Resources.resx, e Form1.Designer.cs per Form1.cs?  Questi vengono impostati nel file Simple.csproj quando viene generato.

 Ecco il \<> ItemGroup da Simple.csproj che crea i riferimenti al progetto:Here's the ItemGroup> from Simple.csproj that creates the project references:

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

 È possibile vedere che questi sono i sei riferimenti al progetto che vengono visualizzati in Esplora soluzioni. Ecco una sezione da \<un'altra> ItemGroup.Here's a section from another ItemGroup>. Molte righe di codice sono state eliminate per chiarezza. Questa sezione Settings.Designer.cs dipende da Settings.settings:

```xml
<ItemGroup>
    <Compile Include="Properties\Settings.Designer.cs">
        <DependentUpon>Settings.settings</DependentUpon>
    </Compile>
</ItemGroup>
```

## <a name="see-also"></a>Vedere anche

- [Generazione di un nuovo progetto: dietro le quinte, parte 1](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)
- [MSBuild](../../msbuild/msbuild.md)
