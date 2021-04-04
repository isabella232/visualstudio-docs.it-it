---
title: 'Procedura dettagliata: creazione di un SDK con C++ | Microsoft Docs'
description: Informazioni su come creare un SDK Math Library per C++ nativo, assemblare l'SDK come estensione di Visual Studio e quindi usarlo per creare un'app usando questa procedura dettagliata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 743759896bf1de104825825d450be081ab2cc666
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217424"
---
# <a name="walkthrough-create-an-sdk-using-c"></a>Procedura dettagliata: creare un SDK con C++
In questa procedura dettagliata viene illustrato come creare un SDK di Math Library per C++ nativo, assemblare l'SDK come estensione di Visual Studio (VSIX) e quindi usarlo per creare un'app. La procedura dettagliata è divisa in questi passaggi:

- [Per creare le librerie native e Windows Runtime](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)

- [Per creare il progetto di estensione NativeMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)

- [Per creare un'app di esempio che usa la libreria di classi](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)

## <a name="prerequisites"></a>Prerequisiti
 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per ulteriori informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="to-create-the-native-and-windows-runtime-libraries"></a><a name="createClassLibrary"></a> Per creare le librerie native e Windows Runtime

1. Sulla barra dei menu scegliere **file**  >  **nuovo**  >  **progetto**.

2. Nell'elenco dei modelli espandere **Visual C++**  >  **universale di Windows** e quindi selezionare il modello **dll (app universali di Windows)** . Nella casella **nome** specificare `NativeMath` , quindi scegliere il pulsante **OK** .

3. Aggiornare *NativeMath. h* in modo che corrisponda al codice seguente.

     :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.h" id="Snippet1":::

4. Aggiornare *NativeMath. cpp* in modo che corrisponda al codice seguente:

     :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.cpp" id="Snippet2":::

5. In **Esplora soluzioni** aprire il menu di scelta rapida per la **soluzione ' NativeMath '**, quindi scegliere **Aggiungi**  >  **nuovo progetto**.

6. Nell'elenco dei modelli espandere **Visual C++**, quindi selezionare il modello di **componente Windows Runtime** . Nella casella **nome** specificare `NativeMathWRT` , quindi scegliere il pulsante **OK** .

7. Aggiornare *Class1. h* in modo che corrisponda al codice seguente:

     :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.h" id="Snippet3":::

8. Aggiornare *Class1. cpp* in modo che corrisponda al codice seguente:

     :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.cpp" id="Snippet4":::

9. Sulla barra dei menu scegliere **Compila**  >  **Compila soluzione**.

## <a name="to-create-the-nativemathvsix-extension-project"></a><a name="createVSIX"></a> Per creare il progetto di estensione NativeMathVSIX

1. In **Esplora soluzioni** aprire il menu di scelta rapida per la **soluzione ' NativeMath '**, quindi scegliere **Aggiungi**  >  **nuovo progetto**.

2. Nell'elenco dei modelli espandere Extensibility di **Visual C#**  >  e quindi selezionare **progetto VSIX**. Nella casella **nome** specificare **NativeMathVSIX**, quindi scegliere il pulsante **OK** .

3. In **Esplora soluzioni** aprire il menu di scelta rapida per **source. Extension. vsixmanifest**, quindi scegliere **Visualizza codice**.

4. Utilizzare il codice XML seguente per sostituire il codice XML esistente.

    :::code language="xml" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathvsix/source.extension.vsixmanifest" id="Snippet6":::


5. In **Esplora soluzioni** aprire il menu di scelta rapida per il progetto **NativeMathVSIX** , quindi scegliere **Aggiungi**  >  **nuovo elemento**.

6. Nell'elenco di **elementi di Visual C#** espandere **dati**, quindi selezionare **file XML**. Nella casella **nome** specificare `SDKManifest.xml` , quindi scegliere il pulsante **OK** .

7. Utilizzare questo codice XML per sostituire il contenuto del file:

    :::code language="xml" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathvsix/sdkmanifest.xml" id="Snippet5":::

8. In **Esplora soluzioni**, nel progetto **NativeMathVSIX** , creare questa struttura di cartelle:

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

9. In **Esplora soluzioni** aprire il menu di scelta rapida per la **soluzione ' NativeMath '** e quindi scegliere **Apri cartella in Esplora file**.

10. In **Esplora file** copiare *$SolutionRoot $ \NativeMath\NativeMath.h*, quindi in **Esplora soluzioni**, nel progetto **NativeMathVSIX** , incollarlo nella cartella *$SolutionRoot $ \NativeMathVSIX\DesignTime\CommonConfiguration\Neutral\Include \\* .

     Copiare *$SolutionRoot $ \Debug\NativeMath\NativeMath.lib*, quindi incollarlo nella cartella *$SolutionRoot $ \NativeMathVSIX\DesignTime\Debug\x86 \\* .

     Copiare *$SolutionRoot $\Debug\NativeMath\NativeMath.dll* e incollarlo nella cartella *$SolutionRoot $ \NativeMathVSIX\Redist\Debug\x86 \\* .

     Copiare *$SolutionRoot $\Debug\NativeMathWRT\NativeMathWRT.dll* e incollarlo nella cartella *$SolutionRoot $ \NativeMathVSIX\Redist\Debug\x86* .
     Copiare *$SolutionRoot $ \Debug\NativeMathWRT\NativeMathWRT.winmd* e incollarlo nella cartella *$SolutionRoot $ \NativeMathVSIX\References\CommonConfiguration\Neutral* .

     Copiare *$SolutionRoot $ \Debug\NativeMathWRT\NativeMathWRT.pri* e incollarlo nella cartella *$SolutionRoot $ \NativeMathVSIX\References\CommonConfiguration\Neutral* .

11. Nella cartella *$SolutionRoot $ \NativeMathVSIX\DesignTime\Debug\x86 \\* creare un file di testo denominato *NativeMathSDK. props*, quindi incollare il contenuto seguente:
   
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

12. Sulla barra dei menu scegliere **Visualizza**  >  **altre finestre**  >  **proprietà finestra** (tastiera: premere il tasto **f4** ).

13. In **Esplora soluzioni** selezionare il file **NativeMathWRT. winmd** . Nella finestra **Proprietà** impostare la proprietà **azione di compilazione** su **contenuto**, quindi impostare la proprietà **Includi in VSIX** su **true**.

     Ripetere questo processo per il file **NativeMath. h** .

     Ripetere questo processo per il file **NativeMathWRT. pri** .

     Ripetere questo processo per il file **NativeMath. lib** .

     Ripetere questo processo per il file **NativeMathSDK. props** .

14. In **Esplora soluzioni** selezionare il file **NativeMath. h** . Nella finestra **Proprietà** modificare la proprietà **Includi in VSIX** su **true**.

     Ripetere questo processo per il file di **NativeMath.dll** .

     Ripetere questo processo per il file di **NativeMathWRT.dll** .

     Ripetere questo processo per il file di **SDKManifest.xml** .

15. Sulla barra dei menu scegliere **Compila**  >  **Compila soluzione**.

16. In **Esplora soluzioni** aprire il menu di scelta rapida per il progetto **NativeMathVSIX** , quindi scegliere **Apri cartella in Esplora file**.

17. In **Esplora file** passare alla cartella *$SolutionRoot $ \NativeMathVSIX\bin\Debug* , quindi eseguire *NativeMathVSIX. vsix* per avviare l'installazione.

18. Scegliere il pulsante **Installa** , attendere il completamento dell'installazione, quindi aprire Visual Studio.

## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a> Per creare un'app di esempio che usa la libreria di classi

1. Sulla barra dei menu scegliere **file**  >  **nuovo**  >  **progetto**.

2. Nell'elenco dei modelli espandere **Visual C++**  >  **universale di Windows** e quindi selezionare **applicazione vuota**. Nella casella **nome** specificare **NativeMathSDKSample**, quindi scegliere il pulsante **OK** .

3. In **Esplora soluzioni** aprire il menu di scelta rapida per il progetto **NativeMathSDKSample** , quindi scegliere **Aggiungi**  >  **riferimento**.

4. Nell'elenco dei tipi di riferimento della finestra di dialogo **Aggiungi riferimento** espandere **Windows universale**, quindi selezionare **estensioni**. Infine, selezionare la casella di controllo **native Math SDK** , quindi scegliere il pulsante **OK** .

5. Visualizzare le proprietà del progetto per NativeMathSDKSample.

    Le proprietà definite in *NativeMathSDK. props* sono state applicate quando è stato aggiunto il riferimento. È possibile verificare che le proprietà siano state applicate esaminando la proprietà **directory di VC + +** delle **proprietà di configurazione** del progetto.

6. In **Esplora soluzioni** aprire **MainPage. XAML** e quindi usare il codice XAML seguente per sostituirne il contenuto:

    :::code language="xml" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml" id="Snippet1":::

7. Aggiornare *MainPage. XAML. h* in modo che corrisponda al codice seguente:

    :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.h" id="Snippet2":::

8. Aggiornare *MainPage. XAML. cpp* in modo che corrisponda al codice seguente:

    :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.cpp" id="Snippet3":::

9. Premere il tasto **F5** per eseguire l'app.

10. Nell'app immettere due numeri, selezionare un'operazione, quindi scegliere il **=** pulsante.

     Viene visualizzato il risultato corretto.

    In questa procedura dettagliata è stato illustrato come creare e usare un SDK di estensione per chiamare una [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] libreria e una libreria non [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] .

## <a name="next-steps"></a>Passaggi successivi

## <a name="see-also"></a>Vedere anche
- [Procedura dettagliata: creare un SDK usando C# o Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [Creare una Software Development Kit](../extensibility/creating-a-software-development-kit.md)
