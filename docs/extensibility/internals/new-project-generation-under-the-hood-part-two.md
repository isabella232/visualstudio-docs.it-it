---
title: 'Generazione nuovo progetto: Dietro le quinte, parte 2 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 73ce91d8-0ab1-4a1f-bf12-4d3c49c01e13
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ea614be39456f5d6a31ea6c9c12221b4db09bbd
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311015"
---
# <a name="new-project-generation-under-the-hood-part-two"></a>Generazione nuovo progetto: Dietro le quinte, seconda parte

In [nuova generazione progetto: Dietro le quinte, parte 1](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) abbiamo visto come il **nuovo progetto** inserite nella finestra di dialogo. Si supponga di aver selezionato una **applicazione di Windows Visual c#** , compilati il **Name** e **percorso** caselle di testo e fa clic su OK.

## <a name="generating-the-solution-files"></a>Per generare i file di soluzione
 Scelta di un modello di applicazione indirizza [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per decomprimere e aprire il file con estensione vstemplate corrispondente e per avviare un modello per interpretare i comandi XML in questo file. Questi comandi creano progetti ed elementi del progetto nella soluzione nuova o esistente.

 Il modello decompresso il file di origine, denominato modelli di elementi, dalla stessa cartella con estensione zip che contiene il file con estensione vstemplate. Il modello consente di copiare questi file per il nuovo progetto di personalizzazione di conseguenza questi.

### <a name="template-parameter-replacement"></a>Sostituzione dei parametri di modello
 Quando il modello copia un modello di elemento in un nuovo progetto, i parametri del modello viene sostituito con stringhe di personalizzare il file. Un parametro di modello è un token speciali che è preceduto o seguito da un segno di dollaro, ad esempio, $ $date.

 Verrà ora esaminato un modello di elemento di progetto tipico. Estrarre ed esaminare Program.cs nella cartella 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip Program Files\Microsoft Visual Studio.

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

Se si crea un nuovo progetto di applicazione Windows denominato "semplice", il modello sostituisce la `$safeprojectname$` parametro con il nome del progetto.

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

 Per un elenco completo dei parametri dei modelli, vedere [Parametri di modelli](../../ide/template-parameters.md).

## <a name="a-look-inside-a-vstemplate-file"></a>Uno sguardo all'interno di una. File con estensione VSTemplate
 Questo formato è un file vstemplate di base

```xml
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">
    <TemplateData>
    </TemplateData>
    <TemplateContent>
    </TemplateContent>
</VSTemplate>
```

 È stata esaminata la \<TemplateData > sezione la [nuova generazione progetto: Dietro le quinte, parte uno](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md). I tag in questa sezione vengono usati per controllare l'aspetto del **nuovo progetto** nella finestra di dialogo.

 I tag nel \<TemplateContent > sezione controllo la generazione di nuovi progetti ed elementi del progetto. Di seguito è riportato il \<TemplateContent > sezione dal file nella cartella \Programmi\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip cswindowsapplication.vstemplate.

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

 Il \<progetto > tag controlla la generazione di un progetto e il \<ProjectItem > tag controlla la generazione di un elemento del progetto. Se il parametro ReplaceParameters è true, il modello personalizzerà tutti i parametri del modello nel file di progetto o elemento. In questo caso, tutti gli elementi di progetto personalizzati, ad eccezione di Settings. Settings.

 Il parametro TargetFileName specifica il nome e percorso relativo del file di progetto risultante o dell'elemento. Ciò consente di creare una struttura di cartelle per il progetto. Se non si specifica questo argomento, l'elemento del progetto avrà lo stesso nome di modello di elemento di progetto.

 La struttura di cartelle dell'applicazione di Windows risulta è simile alla seguente:

 ![SimpleSolution](../../extensibility/internals/media/simplesolution.png "SimpleSolution")

 Il primo e unico \<progetto > tag in legge il modello:

```xml
<Project File="WindowsApplication.csproj" ReplaceParameters="true">
```

 Così facendo, il modello nuovo progetto per creare il file di progetto Simple.csproj copiando e personalizzazione windowsapplication.csproj l'elemento modello.

### <a name="designers-and-references"></a>Finestre di progettazione e riferimenti
 È possibile visualizzare in Esplora soluzioni che nella cartella proprietà sia presente e che contiene i file previsti. Ma per quanto riguarda progetto fa riferimento e dipendenze di file di progettazione, ad esempio Resources.Designer.cs a Resources. resx e Form1.Designer.cs per Form1.cs?  Questi vengono impostati nel file Simple.csproj quando vengono generati.

 Di seguito è riportato il \<ItemGroup > da Simple.csproj che crea i riferimenti al progetto:

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

 Si noterà che questi sono i riferimenti al sei progetto che vengono visualizzati in Esplora soluzioni. Di seguito è riportata una sezione da un altro \<ItemGroup >. Numero di righe di codice è stati eliminati per maggiore chiarezza. In questa sezione fa Settings.Designer.cs dipenda da Settings. Settings:

```xml
<ItemGroup>
    <Compile Include="Properties\Settings.Designer.cs">
        <DependentUpon>Settings.settings</DependentUpon>
    </Compile>
</ItemGroup>
```

## <a name="see-also"></a>Vedere anche

- [Generazione di un nuovo progetto: dietro le quinte, prima parte](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)
- [MSBuild](../../msbuild/msbuild.md)