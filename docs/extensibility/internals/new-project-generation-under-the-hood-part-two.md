---
title: 'Creazione di un nuovo progetto: dietro le quinte, parte 2 | Microsoft Docs'
description: Esaminare in modo dettagliato cosa accade in Visual Studio Integrated Development Environment (IDE) quando si crea un tipo di progetto personalizzato (parte 2 di 2).
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 73ce91d8-0ab1-4a1f-bf12-4d3c49c01e13
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7891cb6a40e6b7de48ba11871688881625b9c68d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895609"
---
# <a name="new-project-generation-under-the-hood-part-two"></a>Generazione nuovo progetto: Dietro le quinte, seconda parte

Nella [generazione di un nuovo progetto: dietro le quinte](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) è stata illustrata la modalità di popolamento della finestra di dialogo **nuovo progetto** . Si supponga di aver selezionato un' **applicazione Windows Visual C#**, compilato le caselle di testo **nome** e **percorso** e fare clic su OK.

## <a name="generating-the-solution-files"></a>Generazione dei file della soluzione
 La scelta di un modello di applicazione indica [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a decomprimere e aprire il file con estensione vstemplate corrispondente e di avviare un modello per interpretare i comandi XML in questo file. Questi comandi creano progetti ed elementi di progetto nella soluzione nuova o esistente.

 Il modello decomprime i file di origine, denominati modelli di elemento, dalla stessa cartella zip che include il file con estensione vstemplate. Il modello copia questi file nel nuovo progetto, personalizzando di conseguenza.

### <a name="template-parameter-replacement"></a>Sostituzione parametri modello
 Quando il modello copia un modello di elemento in un nuovo progetto, sostituisce tutti i parametri di modello con stringhe per personalizzare il file. Un parametro di modello è un token speciale che è preceduto e seguito da un segno di dollaro, ad esempio $date $.

 Viene ora esaminato un modello di elemento di progetto tipico. Estrarre ed esaminare Program.cs nella cartella Programmi\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip.

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

Se si crea un nuovo progetto di applicazione Windows denominato Simple, il modello sostituisce il `$safeprojectname$` parametro con il nome del progetto.

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

 Per un elenco completo dei parametri del modello, vedere [parametri di modello](../../ide/template-parameters.md).

## <a name="a-look-inside-a-vstemplate-file"></a>Un aspetto all'interno di un oggetto. File VSTemplate
 Il formato di un file con estensione vstemplate di base è il seguente

```xml
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">
    <TemplateData>
    </TemplateData>
    <TemplateContent>
    </TemplateContent>
</VSTemplate>
```

 È stata esaminata la \<TemplateData> sezione nella [generazione del nuovo progetto: dietro le quinte, parte 1](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md). I tag in questa sezione vengono utilizzati per controllare l'aspetto della finestra di dialogo **nuovo progetto** .

 I tag nella \<TemplateContent> sezione controllano la generazione di nuovi progetti ed elementi di progetto. Di seguito è illustrata la \<TemplateContent> sezione del file cswindowsapplication. vstemplate nella cartella \Programmi\microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip.

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

 Il \<Project> tag controlla la generazione di un progetto e il \<ProjectItem> tag controlla la generazione di un elemento di progetto. Se il parametro l'ReplaceParameters è true, il modello Personalizza tutti i parametri del modello nel file o nell'elemento del progetto. In questo caso, tutti gli elementi del progetto vengono personalizzati, ad eccezione di Settings. Settings.

 Il parametro TargetFileName specifica il nome e il percorso relativo del file di progetto o dell'elemento risultante. In questo modo è possibile creare una struttura di cartelle per il progetto. Se non si specifica questo argomento, l'elemento del progetto avrà lo stesso nome del modello di elemento di progetto.

 La struttura di cartelle dell'applicazione Windows risultante ha un aspetto simile al seguente:

 ![Screenshot della struttura di cartelle delle applicazioni Windows per la soluzione ' Simple ' in Visual Studio Esplora soluzioni.](../../extensibility/internals/media/simplesolution.png)

 Il primo e unico \<Project> tag del modello viene letto:

```xml
<Project File="WindowsApplication.csproj" ReplaceParameters="true">
```

 In questo modo viene indicato al nuovo modello di progetto di creare il file di progetto con estensione csproj semplice copiando e personalizzando l'elemento del modello WindowsApplication. csproj.

### <a name="designers-and-references"></a>Finestre di progettazione e riferimenti
 È possibile vedere nella Esplora soluzioni che la cartella Properties è presente e che contiene i file previsti. Ma cosa accade per i riferimenti al progetto e le dipendenze dei file di progettazione, ad esempio Resources.Designer.cs in resources. resx e Form1.Designer.cs a Form1.cs?  Queste impostazioni vengono configurate nel file con estensione csproj semplice quando viene generato.

 Di seguito è riportato il \<ItemGroup> da Simple. csproj che consente di creare i riferimenti al progetto:

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

 Si noterà che si tratta dei sei riferimenti del progetto presenti nel Esplora soluzioni. Ecco una sezione di un altro \<ItemGroup> . Molte righe di codice sono state eliminate per maggiore chiarezza. Questa sezione rende Settings.Designer.cs dipendente da Settings. Settings:

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
