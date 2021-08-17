---
title: 'Procedura dettagliata: Creazione di un SDK con C++ | Microsoft Docs'
description: Informazioni su come creare un SDK nativo della libreria matematica C++, creare un pacchetto dell'SDK come estensione Visual Studio e quindi usarlo per creare un'app usando questa procedura dettagliata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 82c875f115611c1e28af39874ca8f384b0afb067022f6539b0f2ff5d9855f77a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121375111"
---
# <a name="walkthrough-create-an-sdk-using-c"></a>Procedura dettagliata: Creare un SDK con C++
Questa procedura dettagliata illustra come creare un SDK nativo della libreria matematica C++, creare un pacchetto dell'SDK come estensione Visual Studio (VSIX) e quindi usarlo per creare un'app. La procedura dettagliata è suddivisa in questi passaggi:

- [Per creare le librerie native e Windows Runtime](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)

- [Per creare il progetto di estensione NativeMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)

- [Per creare un'app di esempio che usa la libreria di classi](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)

## <a name="prerequisites"></a>Prerequisiti
 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per altre informazioni, vedere [Visual Studio SDK.](../extensibility/visual-studio-sdk.md)

## <a name="to-create-the-native-and-windows-runtime-libraries"></a><a name="createClassLibrary"></a>Per creare le librerie native e Windows Runtime

1. Nella barra dei menu scegliere **File**  >  **nuovo**  >  **Project**.

2. Nell'elenco dei modelli espandere **Visual C++** Windows Universale e quindi selezionare il modello  >  DLL **(Windows app** universali). Nella casella **Nome** specificare `NativeMath` e quindi fare clic sul pulsante **OK.**

3. Aggiornare *NativeMath.h* in modo che corrisponda al codice seguente.

     :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.h" id="Snippet1":::

4. Aggiornare *NativeMath.cpp in modo* che corrisponda al codice seguente:

     :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.cpp" id="Snippet2":::

5. In **Esplora soluzioni** aprire il menu di scelta rapida per la soluzione  **'NativeMath'** e quindi scegliere  >  **Aggiungi nuovo** Project .

6. Nell'elenco dei modelli espandere **Visual C++** e quindi selezionare il modello Windows **Runtime Component** . Nella casella **Nome** specificare `NativeMathWRT` e quindi fare clic sul pulsante **OK.**

7. Aggiornare *Class1.h in* modo che corrisponda al codice seguente:

     :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.h" id="Snippet3":::

8. Aggiornare *Class1.cpp in modo* che corrisponda al codice seguente:

     :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.cpp" id="Snippet4":::

9. Sulla barra dei menu scegliere **Compila**  >  **soluzione**.

## <a name="to-create-the-nativemathvsix-extension-project"></a><a name="createVSIX"></a> Per creare il progetto di estensione NativeMathVSIX

1. In **Esplora soluzioni** aprire il menu di scelta rapida per la soluzione  **'NativeMath'** e quindi scegliere  >  **Aggiungi nuovo** Project .

2. Nell'elenco dei modelli espandere estendibilità di **Visual C#**  >  e quindi selezionare **VSIX Project**. Nella casella **Nome** specificare **NativeMathVSIX** e quindi scegliere **OK.**

3. In **Esplora soluzioni** aprire il menu di scelta rapida **per source.extension.vsixmanifest** e quindi scegliere **Visualizza codice**.

4. Usare il codice XML seguente per sostituire il codice XML esistente.

    ```xml
    <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
      <Metadata>
        <Identity Id="NativeMathVSIX..c6b3cae1-e7e2-4e71-90f6-21017ea0dff7" Version="1.0" Language="en-US" Publisher="MyName" />
        <DisplayName>Native Math SDK</DisplayName>
        <Description>Native Math Library w/ Windows Runtime Additions</Description>
      </Metadata>
      <Installation Scope="Global" AllUsers="true">
        <InstallationTarget Id="Microsoft.ExtensionSDK" TargetPlatformIdentifier="Windows" TargetPlatformVersion="v8.0" SdkName="NativeMathSDK" SdkVersion="1.0" />
      </Installation>
      <Dependencies>
      </Dependencies>
      <Assets>
        <Asset Type="Microsoft.ExtensionSDK" d:Source="File" Path="SDKManifest.xml" />
      </Assets>
    </PackageManifest>
    ```

5. In **Esplora soluzioni** aprire il menu di scelta rapida per il **progetto NativeMathVSIX** e quindi scegliere **Aggiungi**  >  **nuovo elemento**.

6. Nell'elenco di **elementi di Visual C#** espandere **Dati** e quindi selezionare **File XML**. Nella casella **Nome** specificare `SDKManifest.xml` e quindi fare clic sul pulsante **OK.**

7. Usare questo codice XML per sostituire il contenuto del file:

    :::code language="xml" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathvsix/sdkmanifest.xml" id="Snippet5":::

8. In **Esplora soluzioni**, nel **progetto NativeMathVSIX,** creare questa struttura di cartelle:

    ```xml
    \DesignTime
          \CommonConfiguration
                \Neutral
                      \Include
          \Debug
                \x86
    \Redist
          \Debug
                \x86
    \References
          \CommonConfiguration
                \Neutral
    ```

9. In **Esplora soluzioni** aprire il menu di scelta rapida per la soluzione **'NativeMath'** e quindi scegliere Apri cartella **in** Esplora file .

10. In **Esplora file** copiare *$SolutionRoot$\NativeMath\NativeMath.h* e quindi in **Esplora soluzioni**, nel **progetto NativeMathVSIX,** incollarlo nella cartella *\\ $SolutionRoot$\NativeMathVSIX\DesignTime\CommonConfiguration\Neutral\Include.*

     Copiare *$SolutionRoot$\Debug\NativeMath\NativeMath.lib* e incollarlo nella cartella *$SolutionRoot$\NativeMathVSIX\DesignTime\Debug\x86. \\*

     Copiare *$SolutionRoot$\Debug\NativeMath\NativeMath.dll* e incollarlo nella cartella *\\ $SolutionRoot$\NativeMathVSIX\Redist\Debug\x86.*

     Copiare *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.dll* e incollarlo nella cartella *$SolutionRoot$\NativeMathVSIX\Redist\Debug\x86.*
     Copiare *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.winmd* e incollarlo nella cartella *$SolutionRoot$\NativeMathVSIX\References\CommonConfiguration\Neutral.*

     Copiare *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.pri* e incollarlo nella cartella *$SolutionRoot$\NativeMathVSIX\References\CommonConfiguration\Neutral.*

11. Nella *cartella $SolutionRoot$\NativeMathVSIX\DesignTime\Debug\x86 \\* creare un file di testo denominato *NativeMathSDK.props* e incollarne il contenuto seguente:
   
    ```xml
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
      <PropertyGroup>
        <NativeMathSDKPath>$(FrameworkSDKRoot)\..\..\UAP\v0.8.0.0\ExtensionSDKs\NativeMathSDK\1.0\</NativeMathSDKPath>
        <IncludePath>$(NativeMathSDKPath)DesignTime\CommonConfiguration\Neutral\Include;$(IncludePath)</IncludePath>
        <LibraryPath>$(NativeMathSDKPath)DesignTime\Debug\x86;$(LibraryPath)</LibraryPath>
      </PropertyGroup>
      <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">
         <Link>
           <AdditionalDependencies>NativeMath.lib;%(AdditionalDependencies)</AdditionalDependencies>
         </Link>
      </ItemDefinitionGroup>
    </Project>
    ```

12. Sulla barra dei menu scegliere **Visualizza**  >  **altro Windows** proprietà  >  **(Tastiera:** scegliere il tasto **F4).**

13. In **Esplora soluzioni** selezionare il file **NativeMathWRT.winmd.** Nella finestra **Proprietà** modificare la proprietà **Azione di** compilazione in **Contenuto** e quindi impostare la proprietà Includi **in VSIX** su **True.**

     Ripetere questo processo per il file **NativeMath.h.**

     Ripetere questo processo per il file **NativeMathWRT.pri.**

     Ripetere questo processo per il file **NativeMath.Lib.**

     Ripetere questo processo per il file **NativeMathSDK.props.**

14. In **Esplora soluzioni** selezionare il file **NativeMath.h.** Nella finestra **Proprietà** impostare la **proprietà Includi in VSIX** su **True.**

     Ripetere questo processo per il **NativeMath.dll** file.

     Ripetere questo processo per il **NativeMathWRT.dll** file.

     Ripetere questo processo per il **SDKManifest.xml** file.

15. Sulla barra dei menu scegliere **Compila**  >  **soluzione**.

16. In **Esplora soluzioni** aprire il menu di scelta rapida per il **progetto NativeMathVSIX** e quindi scegliere **Apri cartella in** Esplora file .

17. In **Esplora file** passare alla *cartella $SolutionRoot$\NativeMathVSIX\bin\Debug* e quindi eseguire *NativeMathVSIX.vsix* per avviare l'installazione.

18. Scegliere il **pulsante Installa,** attendere il completamento dell'installazione e quindi aprire Visual Studio.

## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a> Per creare un'app di esempio che usa la libreria di classi

1. Nella barra dei menu scegliere **File**  >  **nuovo**  >  **Project**.

2. Nell'elenco dei modelli espandere **Visual C++**  >  **Windows Universale** e quindi selezionare **App vuota**. Nella casella **Nome** specificare **NativeMathSDKSample** e quindi scegliere **OK.**

3. In **Esplora soluzioni** aprire il menu di scelta rapida per il **progetto NativeMathSDKSample** e quindi scegliere **Aggiungi**  >  **riferimento**.

4. **Nell'elenco dei tipi** di riferimento della finestra di dialogo Aggiungi riferimento espandere Universal **Windows** e quindi **selezionare Estensioni**. Selezionare infine la **casella di controllo Native Math SDK** e quindi fare clic sul pulsante **OK.**

5. Visualizzare le proprietà del progetto per NativeMathSDKSample.

    Le proprietà definite in *NativeMathSDK.props* sono state applicate quando è stato aggiunto il riferimento. È possibile verificare che le proprietà siano state applicate esaminando **la VC++ directory** delle proprietà di configurazione del **progetto.**

6. In **Esplora soluzioni** aprire **MainPage.xaml** e quindi usare il codice XAML seguente per sostituirlo:

    :::code language="xml" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml" id="Snippet1":::

7. Aggiornare *Mainpage.xaml.h* in modo che corrisponda al codice seguente:

    :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.h" id="Snippet2":::

8. Aggiornare *MainPage.xaml.cpp in modo* che corrisponda al codice seguente:

    :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.cpp" id="Snippet3":::

9. Premere **F5 per** eseguire l'app.

10. Nell'app immettere due numeri, selezionare un'operazione e quindi scegliere il **=** pulsante .

     Viene visualizzato il risultato corretto.

    Questa procedura dettagliata ha illustrato come creare e usare un SDK di estensione per chiamare in una [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] libreria e in una libreria [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] non.

## <a name="next-steps"></a>Passaggi successivi

## <a name="see-also"></a>Vedere anche
- [Procedura dettagliata: Creare un SDK usando C# o Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [Creare un software development kit](../extensibility/creating-a-software-development-kit.md)
