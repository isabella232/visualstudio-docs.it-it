---
title: 'Procedura: configurare progetti per le piattaforme di destinazione'
description: Informazioni su Visual Studio consente di configurare le applicazioni per piattaforme diverse, incluse le piattaforme a 64 bit.
ms.custom: SEO-VS-2020
ms.date: 09/13/2021
ms.technology: vs-ide-compile
ms.topic: how-to
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b74eb7d0220867b80337b89ef70506bac31b7f6a
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2021
ms.locfileid: "128429017"
---
# <a name="how-to-configure-projects-to-target-platforms"></a>Procedura: configurare progetti per le piattaforme di destinazione

Visual Studio consente di configurare le compilazioni dell'applicazione per piattaforme diverse, incluse le piattaforme a 64 bit. Per altre informazioni sul supporto della piattaforma a 64 bit in Visual Studio, vedere [Applicazioni a 64 bit.](/dotnet/framework/64-bit-apps)

::: moniker range="vs-2022"
> [!NOTE]
> Visual Studio 2022 Preview viene eseguito come applicazione a 64 bit. Questo è completamente separato dalle piattaforme che è possibile usare come destinazione per i progetti in Visual Studio. È possibile usare qualsiasi versione di Visual Studio per le piattaforme a 32 bit e a 64 bit.
::: moniker-end
::: moniker range="<=vs-2019"
> [!NOTE]
> Visual Studio viene eseguito come applicazione a 32 bit. Questo è completamente separato dalle piattaforme che è possibile usare come destinazione per i progetti in Visual Studio. È possibile usare qualsiasi versione di Visual Studio per le piattaforme a 32 bit e a 64 bit.
::: moniker-end

## <a name="target-platforms-with-the-configuration-manager"></a>Individuazione delle piattaforme di destinazione con Gestione configurazione

La **Gestione configurazione** consente di aggiungere rapidamente una nuova piattaforma di destinazione al progetto. Se si seleziona una delle piattaforme incluse in Visual Studio, le proprietà del progetto vengono modificate per compilare il progetto per la piattaforma selezionata.

### <a name="to-configure-a-project-to-target-a-64-bit-platform"></a>Per configurare un progetto per una piattaforma a 64 bit

1. Sulla barra dei menu **scegliere** Compila Gestione configurazione  >  .

2. Nell'elenco **Piattaforma soluzione attiva** scegliere una piattaforma a 64 bit di destinazione per la soluzione e quindi scegliere il pulsante **Chiudi**.

    1. Se la piattaforma desiderata non viene visualizzata nell'elenco **Piattaforma soluzione** attiva, scegliere **Nuovo**.

         Verrà visualizzata la finestra di dialogo **Nuova piattaforma soluzione**.

    2. Nell'elenco **Digitare o selezionare la nuova piattaforma** scegliere **x64**.

        > [!NOTE]
        > Se si specifica un nuovo nome per la configurazione, potrebbe essere necessario modificare le impostazioni in **Creazione progetti** per la piattaforma corretta.

    3. Se si vuole copiare le impostazioni da una configurazione di piattaforma corrente, selezionarla e quindi fare clic sul pulsante **OK**.

Le proprietà per tutti i progetti nella soluzione che hanno come destinazione la piattaforma a 64 bit vengono aggiornate e la build successiva del progetto verrà ottimizzata per le piattaforme a 64 bit.

> [!NOTE]
> Il **nome della piattaforma Win32** viene usato per i progetti C++ e significa **x86**. Visual Studio considera sia le piattaforme a livello di progetto che le piattaforme a livello di soluzione e le piattaforme di progetto provengono dai sistemi di progetto specifici del linguaggio. I progetti C++ usano **Win32** **e x64,** ma le piattaforme della soluzione usano **x86** **e x64**. Quando si sceglie **x86** come configurazione della soluzione, Visual Studio la **piattaforma Win32** per i progetti C++. Per visualizzare le impostazioni della piattaforma a livello di progetto e della piattaforma a livello di soluzione, aprire Gestione configurazione **e** prendere nota delle due impostazioni della piattaforma. La piattaforma a livello di soluzione è visualizzata nell'elenco a discesa **Piattaforma soluzione** attiva e la tabella mostra la piattaforma a livello di progetto per ogni progetto.
> ![Screenshot che mostra la piattaforma della soluzione e la piattaforma del progetto](media/project-platform-win32.png)

## <a name="target-platforms-in-the-project-designer"></a>Individuazione delle piattaforme di destinazione in Progettazione progetti

Anche **Progettazione progetti** consente di creare diverse piattaforme di destinazione per il progetto. Se la selezione di una delle piattaforme incluse nell'elenco della finestra di dialogo **Nuova piattaforma soluzione** non è applicabile alla soluzione, è possibile creare un nome di configurazione personalizzato e modificare le impostazioni in **Creazione progetti** per la piattaforma di destinazione corretta.

L'esecuzione di questa attività varia in base al linguaggio di programmazione usato. Per altre informazioni, vedere i collegamenti seguenti:

- Per Visual Basic, vedere [/platform (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/platform).

- Per i progetti C#, vedere [pagina Compilazione, Project Designer (C#).](../ide/reference/build-page-project-designer-csharp.md)

- Per i progetti C++/CLI, vedere [/clr (compilazione Common Language Runtime).](/cpp/build/reference/clr-common-language-runtime-compilation)

## <a name="manually-editing-the-project-file"></a>Modifica manuale del file di progetto

In alcuni casi è necessario modificare manualmente il file di progetto per applicare una configurazione personalizzata. Un esempio è la presenza di condizioni che non possono essere specificate nell'IDE, ad esempio un riferimento diverso per due piattaforme differenti, come nell'esempio seguente.

### <a name="example-referencing-x86-and-x64-assemblies-and-dlls"></a>Esempio: riferimento ad assembly e DLL x86 e x64

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

## <a name="see-also"></a>Vedi anche

- [Informazioni sulle piattaforme di compilazione](../ide/understanding-build-platforms.md)
- [/platform (opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option)
- [Applicazioni a 64 bit](/dotnet/framework/64-bit-apps)
- [Supporto a 64 bit per l'IDE di Visual Studio](../ide/visual-studio-ide-64-bit-support.md)
- [Informazioni sul file di progetto](/aspnet/web-forms/overview/deployment/web-deployment-in-the-enterprise/understanding-the-project-file)
