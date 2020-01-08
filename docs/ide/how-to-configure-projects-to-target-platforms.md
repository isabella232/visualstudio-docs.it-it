---
title: 'Procedura: configurare progetti per le piattaforme di destinazione'
ms.date: 08/16/2019
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- project settings [Visual Studio], targeting platforms
- platforms, targeting specific CPUs
- project properties [Visual Studio], targeting platforms
- projects [Visual Studio], targeting platforms
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- CPUs, targeting specific
- 64-bit applications [Visual Studio]
ms.assetid: 845302fc-273d-4f81-820a-7296ce91bd76
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9ba79bb199bba6c606ac603816cadc2dd2042057
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595319"
---
# <a name="how-to-configure-projects-to-target-platforms"></a>Procedura: configurare progetti per le piattaforme di destinazione

Visual Studio consente di configurare le applicazioni per diverse piattaforme di destinazione, tra cui le piattaforme a 64 bit. Per altre informazioni sul supporto delle piattaforme a 64 bit in Visual Studio, vedere [Applicazioni a 64 bit](/dotnet/framework/64-bit-apps).

## <a name="target-platforms-with-the-configuration-manager"></a>Individuazione delle piattaforme di destinazione con Gestione configurazione

La **Gestione configurazione** consente di aggiungere rapidamente una nuova piattaforma di destinazione al progetto. Se si seleziona una delle piattaforme incluse in Visual Studio, le proprietà del progetto vengono modificate per compilare il progetto per la piattaforma selezionata.

### <a name="to-configure-a-project-to-target-a-64-bit-platform"></a>Per configurare un progetto per una piattaforma a 64 bit

1. Nella barra dei menu scegliere **Compilazione** > **Gestione configurazione**.

2. Nell'elenco **Piattaforma soluzione attiva** scegliere una piattaforma a 64 bit di destinazione per la soluzione e quindi scegliere il pulsante **Chiudi**.

    1. Se la piattaforma non compare nell'elenco **Piattaforma soluzione attiva**, scegliere **Nuovo**.

         Viene visualizzata la finestra di dialogo **Nuova piattaforma soluzione**.

    2. Nell'elenco **Digitare o selezionare la nuova piattaforma** scegliere **x64**.

        > [!NOTE]
        > Se si specifica un nuovo nome per la configurazione, potrebbe essere necessario modificare le impostazioni in **Creazione progetti** per la piattaforma corretta.

    3. Se si vuole copiare le impostazioni da una configurazione di piattaforma corrente, selezionarla e quindi fare clic sul pulsante **OK**.

Le proprietà per tutti i progetti destinati alla piattaforma a 64 bit vengono aggiornate e la compilazione successiva del progetto verrà ottimizzata per le piattaforme a 64 bit.

## <a name="target-platforms-in-the-project-designer"></a>Individuazione delle piattaforme di destinazione in Progettazione progetti

Anche **Progettazione progetti** consente di creare diverse piattaforme di destinazione per il progetto. Se la selezione di una delle piattaforme incluse nell'elenco della finestra di dialogo **Nuova piattaforma soluzione** non è applicabile alla soluzione, è possibile creare un nome di configurazione personalizzato e modificare le impostazioni in **Creazione progetti** per la piattaforma di destinazione corretta.

L'esecuzione di questa attività varia in base al linguaggio di programmazione usato. Per altre informazioni, accedere ai collegamenti seguenti:

- Per i progetti [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], vedere [/platform (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/platform).

- Per i progetti [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], vedere [Pagina Compilazione, Creazione progetti (C#)](../ide/reference/build-page-project-designer-csharp.md).

- Per i progetti [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], vedere [/clr (Compilazione Common Language Runtime)](/cpp/build/reference/clr-common-language-runtime-compilation).

## <a name="manually-editing-the-project-file"></a>Modifica manuale del file di progetto

In alcuni casi è necessario modificare manualmente il file di progetto per applicare una configurazione personalizzata. Un esempio è la presenza di condizioni che non possono essere specificate nell'IDE, ad esempio un riferimento diverso per due piattaforme differenti, come nell'esempio seguente.

### <a name="example-referencing-x86-and-x64-assemblies-and-dlls"></a>Esempio: riferimento a assembly e dll x86 e x64

Potrebbe essere disponibile un assembly o una DLL .NET con entrambe le versioni x86 e x64. Per configurare il progetto in modo da usare questi riferimenti, aggiungere prima di tutto il riferimento, quindi aprire il file di progetto e modificarlo per aggiungere un `ItemGroup` con una condizione che fa riferimento sia alla configurazione che alla piattaforma di destinazione.  Si supponga, ad esempio, che il file binario a cui si fa riferimento sia ClassLibrary1 e che ci siano percorsi diversi per le configurazioni di debug e di versione, nonché per le versioni x86 e x64.  Usare quindi quattro elementi `ItemGroup` con tutte le combinazioni di impostazioni, come indicato di seguito:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.0</TargetFramework>
    <Platforms>AnyCPU;x64;x86</Platforms>
  </PropertyGroup>

  <ItemGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x64'">
    <Reference Include="ClassLibrary1">
      <HintPath>..\..\ClassLibrary1\ClassLibrary1\bin\x64\Debug\netstandard2.0\ClassLibrary1.dll</HintPath>
    </Reference>
  </ItemGroup>

  <ItemGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|x64'">
    <Reference Include="ClassLibrary1">
      <HintPath>..\..\ClassLibrary1\ClassLibrary1\bin\x64\Release\netstandard2.0\ClassLibrary1.dll</HintPath>
    </Reference>
  </ItemGroup>

  <ItemGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86'">
    <Reference Include="ClassLibrary1">
      <HintPath>..\..\ClassLibrary1\ClassLibrary1\bin\x86\Debug\netstandard2.0\ClassLibrary1.dll</HintPath>
    </Reference>
  </ItemGroup>
  
  <ItemGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|x86'">
    <Reference Include="ClassLibrary1">
      <HintPath>..\..\ClassLibrary1\ClassLibrary1\bin\x86\Release\netstandard2.0\ClassLibrary1.dll</HintPath>
    </Reference>
  </ItemGroup>
</Project>
```

::: moniker range="vs-2017"
> [!NOTE]
> In Visual Studio 2017 è necessario scaricare il progetto prima di poter modificare il file di progetto. Per scaricare il progetto, fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Scarica progetto**. Al termine, salvare le modifiche e ricaricare il progetto facendo clic con il pulsante destro del mouse sul nodo del progetto e scegliendo **Ricarica progetto**.
::: moniker-end

Per altre informazioni sul file di progetto, vedere [Informazioni di riferimento sullo schema del file di progetto di MSBuild](../msbuild/msbuild-project-file-schema-reference.md).

## <a name="see-also"></a>Vedere anche

- [Informazioni sulle piattaforme di compilazione](../ide/understanding-build-platforms.md)
- [/platform (opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option)
- [Applicazioni a 64 bit](/dotnet/framework/64-bit-apps)
- [Supporto a 64 bit per l'IDE di Visual Studio](../ide/visual-studio-ide-64-bit-support.md)
- [Informazioni sul file di progetto](/aspnet/web-forms/overview/deployment/web-deployment-in-the-enterprise/understanding-the-project-file)
