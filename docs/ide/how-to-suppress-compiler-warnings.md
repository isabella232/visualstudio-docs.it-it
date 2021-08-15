---
title: Eliminare gli avvisi per progetti e NuGet pacchetti
description: Informazioni su come usare Visual Studio per eliminare un log di compilazione filtrando uno o più tipi di avvisi del compilatore.
ms.custom: SEO-VS-2020
ms.date: 01/24/2018
ms.technology: vs-ide-compile
ms.topic: how-to
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 55c3a0b0d5d7bd41b564467936252f3c0a3cafc3c40e2549b673c4f8046136fc
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121272252"
---
# <a name="how-to-suppress-compiler-warnings"></a>Procedura: Non visualizzare gli avvisi del compilatore

È possibile snellire un log di compilazione escludendo uno o più tipi di avvisi del compilatore. Ad esempio, potrebbe essere necessario esaminare solo parte dell'output generato quando si imposta il livello di dettaglio del log di compilazione su **Normale,** Dettagliato o **Diagnostica.** Per altre informazioni sul livello di dettaglio, vedere [Procedura: Visualizzare, salvare e configurare file di log di compilazione](../ide/how-to-view-save-and-configure-build-log-files.md).

## <a name="suppress-specific-warnings-for-visual-c-or-f"></a>Non visualizzare avvisi specifici per Visual C# o F\#

Usare la pagina delle proprietà **Compila** per escludere avvisi specifici per i progetti C# e F#.

1. In **Esplora soluzioni** scegliere il progetto in cui non devono essere visualizzati gli avvisi.

1. Sulla barra dei menu scegliere **Visualizza pagine**  >  **delle proprietà**.

1. Scegliere la scheda **Compila**.

1. Nella casella **Non visualizzare avvisi** specificare i codici di errore degli avvisi che non devono essere visualizzati, separati da punti e virgola.

1. Ricompilare la soluzione.

## <a name="suppress-specific-warnings-for-c"></a>Eliminare avvisi specifici per C++

Usare la pagina delle proprietà **Proprietà di configurazione** per escludere avvisi specifici per i progetti C++.

1. In **Esplora soluzioni** scegliere il progetto o il file di origine in cui non devono essere visualizzati gli avvisi.

1. Sulla barra dei menu scegliere **Visualizza pagine**  >  **delle proprietà**.

1. Scegliere la categoria **Proprietà di configurazione**, selezionare la categoria **C/C++** e scegliere la pagina **Avanzate**.

1. Effettuare uno dei passaggi indicati di seguito.

    - Nella casella **Disabilita avvisi specifici** specificare i codici di errore degli avvisi che non devono essere visualizzati, separati da punto e virgola.

    - Nella casella **Disabilita avvisi specifici** scegliere **Modifica** per visualizzare altre opzioni.

1. Fare clic sul pulsante **OK** e ricompilare la soluzione.

## <a name="suppress-warnings-for-visual-basic"></a>Non visualizzare avvisi per Visual Basic

È possibile nascondere gli avvisi del compilatore specifici per Visual Basic modificando il file con estensione *vbproj* per il progetto. Per escludere gli avvisi in base alla *categoria*, è possibile usare la [pagina delle proprietà Compilazione](../ide/reference/compile-page-project-designer-visual-basic.md). Per altre informazioni, vedere [Configurare gli avvisi in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).

### <a name="to-suppress-specific-warnings-for-visual-basic"></a>Per non visualizzare avvisi specifici per Visual Basic

Questo esempio mostra come modificare il file *vbproj* per escludere avvisi specifici del compilatore.

1. In **Esplora soluzioni** scegliere il progetto in cui non devono essere visualizzati gli avvisi.

1. Sulla barra dei menu **scegliere** Project Scarica  >  **Project**.

1. In **Esplora soluzioni** aprire il menu di scelta rapida per il progetto e quindi scegliere **Modifica\<ProjectName>vbproj**.

    Il file di progetto XML verrà aperto nell'editor del codice.

1. Individuare l'elemento `<NoWarn>` per la configurazione della build usata per la compilazione e aggiungere uno o più numeri di avviso come valore dell'elemento `<NoWarn>`. Se si specificano più numeri di avviso, separarli con una virgola.

     Nell'esempio seguente viene indicato l'elemento `<NoWarn>` per la configurazione della build *Debug* in una piattaforma x86 con due avvisi del compilatore esclusi:

    ```xml
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86' ">
        <PlatformTarget>x86</PlatformTarget>
        <DebugSymbols>true</DebugSymbols>
        <DebugType>full</DebugType>
        <Optimize>false</Optimize>
        <OutputPath>bin\Debug\</OutputPath>
        <DefineDebug>true</DefineDebug>
        <DefineTrace>true</DefineTrace>
        <ErrorReport>prompt</ErrorReport>
        <NoWarn>40059,42024</NoWarn>
        <WarningLevel>1</WarningLevel>
      </PropertyGroup>
    ```

   > [!NOTE]
   > I progetti .NET Core non contengono gruppi di proprietà di configurazione della build per impostazione predefinita. Per escludere avvisi in un progetto .NET Core, aggiungere la sezione della configurazione della build manualmente al file. Esempio:
   >
   > ```xml
   > <Project Sdk="Microsoft.NET.Sdk">
   >   <PropertyGroup>
   >     <OutputType>Exe</OutputType>
   >     <TargetFramework>netcoreapp2.0</TargetFramework>
   >     <RootNamespace>VBDotNetCore_1</RootNamespace>
   >   </PropertyGroup>
   >   <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
   >     <NoWarn>42016,41999,42017</NoWarn>
   >   </PropertyGroup>
   > </Project>
   > ```

1. Salvare le modifiche apportate al file con estensione *vbproj*.

1. Sulla barra dei menu **scegliere** Project Ricarica  >  **Project**.

1. Sulla barra dei menu scegliere **Compila**  >  **ricompila soluzione**.

    Nella finestra **Output** gli avvisi specificati non saranno più visualizzati.

Per altre informazioni, vedere l'[opzione del compilatore /nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) per il compilatore della riga di comando di Visual Basic.

## <a name="suppress-warnings-for-nuget-packages"></a>Non visualizzare avvisi per i pacchetti NuGet

In alcuni casi, può essere necessario escludere gli avvisi del compilatore NuGet per un singolo pacchetto NuGet, anziché per un intero progetto. L'avviso ha uno scopo, quindi si vuole evitare di escluderlo a livello di progetto. Ad esempio, uno degli avvisi NuGet indica che il pacchetto potrebbe non essere completamente compatibile con il progetto. Se si esclude questo avviso a livello di progetto e in seguito si aggiunge un ulteriore pacchetto NuGet, non si saprà mai se questo pacchetto è la causa di un avviso di compatibilità.

### <a name="to-suppress-a-specific-warning-for-a-single-nuget-package"></a>Per escludere un avviso specifico per un singolo pacchetto NuGet

1. In **Esplora soluzioni** selezionare il pacchetto NuGet per il quale si vogliono escludere avvisi del compilatore.

   ![Pacchetto NuGet in Esplora soluzioni](media/nuget-package-with-warning.png)

1. Scegliere **Proprietà** dal menu di scelta rapida.

1. Nella casella **NoWarn** delle proprietà del pacchetto immettere il numero di avviso che si vuole escludere per il pacchetto. Per escludere più di un avviso, usare la virgola per separare i numeri di avviso.

   ![Proprietà del pacchetto NuGet](media/nuget-properties-nowarn.png)

   L'avviso scompare da **Esplora soluzioni** e dall'**Elenco errori**.

## <a name="see-also"></a>Vedi anche

- [Procedura dettagliata: Creare un'applicazione](../ide/walkthrough-building-an-application.md)
- [Procedura: Visualizzare, salvare e configurare file di log di compilazione](../ide/how-to-view-save-and-configure-build-log-files.md)
- [Compilare](../ide/compiling-and-building-in-visual-studio.md)
