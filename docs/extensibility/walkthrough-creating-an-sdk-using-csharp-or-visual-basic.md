---
title: 'Procedura dettagliata: creazione di un SDK utilizzando C . Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 16eb20452601a65c498ff112ea996f2d93559940
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697549"
---
# <a name="walkthrough-create-an-sdk-using-c-or-visual-basic"></a>Procedura dettagliata: Creazione di un SDK con C .NET o Visual BasicWalkthrough: Create an SDK using C 'amp-Visual Basic
In questa procedura dettagliata verrà illustrato come creare un SDK della libreria matematica semplice utilizzando Visual C, quindi creare un pacchetto dell'SDK come estensione di Visual Studio (VSIX). Verranno completate le procedure seguenti:

- [Per creare il componente DiVi Runtime SimpleMath](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)

- [Per creare il progetto di estensione SimpleMathVSIXTo create the SimpleMathVSIX extension project](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)
- [Per creare un'app di esempio che usa la libreria di classiTo create a sample app that uses the class library](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)

## <a name="prerequisites"></a>Prerequisiti
 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per ulteriori informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="to-create-the-simplemath-windows-runtime-component"></a><a name="createClassLibrary"></a>Per creare il componente DiVi Runtime SimpleMath

1. Nella barra dei menu scegliere **File** > **Nuovo** > **progetto**.

2. Nell'elenco dei modelli, espandere **Visual C,** o **Visual Basic**, scegliere il nodo **Windows Store** e quindi scegliere il modello Componente **Windows Runtime.**

3. Nella casella **Nome** specificare **SimpleMath**, quindi scegliere **OK** .

4. In **Esplora soluzioni**aprire il menu di scelta rapida per il nodo del progetto **SimpleMath,** quindi scegliere **Proprietà**.

5. Rinominare **Class1.cs** **in Arithmetic.cs** e aggiornarlo in modo che corrisponda al codice seguente:

    [!code-csharp[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.cs)]
    [!code-vb[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.vb)]

6. In **Esplora soluzioni**aprire il menu di scelta rapida per il nodo **Soluzione 'SimpleMath',** quindi scegliere **Configuration Manager**.

    Verrà visualizzata la finestra di dialogo **Gestione configurazione.**

7. Nell'elenco **Configurazione soluzione attiva** scegliere **Rilascio**.

8. Nella colonna **Configurazione** verificare che la riga **SimpleMath** sia impostata su **Release**, quindi scegliere il pulsante **Chiudi** per accettare la modifica.

   > [!IMPORTANT]
   > L'SDK per il componente SimpleMath include una sola configurazione. Questa configurazione deve essere la build di rilascio oppure le [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]app che utilizzano il componente non passeranno la certificazione per il file .

9. In **Esplora soluzioni**aprire il menu di scelta rapida per il nodo del progetto **SimpleMath,** quindi scegliere **Compila**.

## <a name="to-create-the-simplemathvsix-extension-project"></a><a name="createVSIX"></a>Per creare il progetto di estensione SimpleMathVSIXTo create the SimpleMathVSIX extension project

1. Scegliere **Aggiungi** > **nuovo progetto**dal menu di scelta rapida per il nodo Soluzione **'SimpleMath'.**

2. Nell'elenco dei modelli, espandere **Visual C,** o **Visual Basic**, scegliere il nodo **Extensibility** e quindi scegliere il modello di **progetto VSIX.**

3. Nella casella **Nome** specificare **SimpleMathVSIX**, quindi scegliere **OK** .

4. In **Esplora soluzioni**scegliere l'elemento **source.extension.vsixmanifest** .

5. Nella barra dei menu scegliere **Visualizza** > **codice**.

6. Sostituire il codice XML esistente con il codice XML seguente:

     [!code-xml[CreatingAnSDKUsingWinRT#1](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]

7. In **Esplora soluzioni**scegliere il progetto **SimpleMathVSIX.**

8. Nella barra dei menu scegliere **Aggiungi** > **nuovo elemento**.

9. Nell'elenco **Elementi comuni**espandere **Dati**, quindi scegliere **File XML**.

10. Nella casella **Nome** `SDKManifest.xml`specificare , quindi scegliere il pulsante **Aggiungi.**

11. In **Esplora soluzioni**aprire `SDKManifest.xml`il menu di scelta rapida per , scegliere **Proprietà**, quindi impostare il valore della proprietà **Includi in VSIX** su **True**.

12. Sostituisci il contenuto del file con il codice XML riportato di seguito:

    **C#**

    ```xml
    <FileList
      DisplayName="WinRT Math Library (CS)"
      MinVSVersion="11.0"
      TargetFramework=".NETCore,version=v4.5"
      AppliesTo="WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="https://msdn.microsoft.com/">
    </FileList>
    ```

    **Visual Basic**

    ```xml
    <FileList
      DisplayName="WinRT Math Library (VB)"
      MinVSVersion="11.0"
      TargetFramework=".NETCore,version=v4.5"
      AppliesTo="WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="https://msdn.microsoft.com/">
    </FileList>
    ```

13. In **Esplora soluzioni**aprire il menu di scelta rapida per il progetto **SimpleMathVSIX,** scegliere **Aggiungi**, quindi **Nuova cartella**.

14. Rinominare la `references`cartella in .

15. Aprire il menu di scelta rapida per la cartella **Riferimenti** , scegliere **Aggiungi**, quindi **Nuova cartella**.

16. Rinominare la `commonconfiguration`sottocartella in , creare una `neutral`sottocartella al suo interno e denominarla .

17. Ripetere i quattro passaggi precedenti, questa volta `redist`rinominando la prima cartella in .

     Il progetto contiene ora la seguente struttura di cartelle:

    ```xml
    references\commonconfiguration\neutral
    redist\commonconfiguration\neutral
    ```

18. In **Esplora soluzioni**aprire il menu di scelta rapida per il progetto **SimpleMath,** quindi scegliere **Apri cartella in Esplora file**.

19. In **Esplora file**, passare alla cartella *bin-Release* , aprire il menu di scelta rapida per il file **SimpleMath.winmd,** quindi scegliere **Copia**.

20. In **Esplora soluzioni**incollare il file nella cartella *references, commonconfiguration, neutral* del progetto **SimpleMathVSIX.**

21. Ripetere il passaggio precedente, incollando il file **SimpleMath.pri** nella cartella *redist-commonconfiguration-neutral* nel progetto **SimpleMathVSIX.**

22. In **Esplora soluzioni**scegliere **SimpleMath.winmd**.

23. Nella barra dei menu scegliere **Visualizza** > **proprietà** (tastiera: scegliere il tasto **F4).**

24. Nella finestra **Proprietà** modificare la proprietà Operazione di **compilazione** in **Contenuto**, quindi la proprietà **Includi in VSIX** in **True**.

25. In **Esplora soluzioni**ripetere questo processo per **SimpleMath.pri**.

26. In **Esplora soluzioni**scegliere il progetto **SimpleMathVSIX.**

27. Nella barra dei menu scegliere **Compila** > **SimpleMathVSIX**.

28. In **Esplora soluzioni**aprire il menu di scelta rapida per il progetto **SimpleMathVSIX,** quindi scegliere **Apri cartella in Esplora file**.

29. In **Esplora file**, passare alla cartella , quindi eseguire *\bin\Release* *SimpleMathVSIX.vsix* per installarlo.

30. Scegliere **il** installa pulsante, attendere il completamento dell'installazione e quindi riavviare Visual Studio.

## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a>Per creare un'app di esempio che usa la libreria di classiTo create a sample app that uses the class library

1. Nella barra dei menu scegliere **File** > **Nuovo** > **progetto**.

2. Nell'elenco dei modelli, espandere **Visual C,** Visual Basic o **Visual Basic**, quindi scegliere il nodo **Windows Store.**

3. Scegliere il modello **Applicazione vuota,** assegnare al progetto il nome **ArithmeticUI**, quindi scegliere **OK** .

4. In **Esplora soluzioni**aprire il menu di scelta rapida per il progetto **ArithmeticUI,** quindi scegliere **Aggiungi** > **riferimento**.

5. Nell'elenco dei tipi di riferimento espandere **Windows**, quindi scegliere **Estensioni**.

6. Nel riquadro dei dettagli scegliere l'estensione **WinRT Math Library.**

    Vengono visualizzate ulteriori informazioni sull'SDK. È possibile scegliere il collegamento https://msdn.microsoft.com/Ulteriori **informazioni** per aprire , come specificato nel file SDKManifest.xml specificato in precedenza in questa procedura dettagliata.

7. Nella finestra di dialogo **Gestione riferimenti** selezionare la casella di controllo Libreria **matematica WinRT,** quindi scegliere **OK.**

8. Nella barra dei menu scegliere **Visualizza** > **Visualizzatore oggetti**.

9. Nell'elenco **Sfoglia** scegliere **Matematica semplice**.

     È ora possibile esplorare il contenuto dell'SDK.

10. In **Esplora soluzioni**aprire **MainPage.xaml**e sostituiscene il contenuto con il codice XAML seguente:

    **C#**

    ```xml
    <Page
        x:Class="ArithmeticUI.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:SimpleMath"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
            <TextBox x:Name="_firstNumber" HorizontalAlignment="Left" Margin="414,370,0,0" TextWrapping="Wrap" Text="First Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <TextBox x:Name="_secondNumber" HorizontalAlignment="Left" Margin="613,370,0,0" TextWrapping="Wrap" Text="Second Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <Button Content="+" HorizontalAlignment="Left" Margin="557,301,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="-" HorizontalAlignment="Left" Margin="557,345,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="*" HorizontalAlignment="Left" Margin="557,389,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="/" HorizontalAlignment="Left" Margin="557,433,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="=" HorizontalAlignment="Left" Margin="755,367,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnResultsClick"/>
            <TextBox x:Name="_result" HorizontalAlignment="Left" Margin="809,370,0,0" TextWrapping="Wrap" Text="Result" VerticalAlignment="Top" Height="32" Width="163" TextAlignment="Center" IsReadOnly="True"/>
        </Grid>
    </Page>
    ```

    **Visual Basic**

    ```xml
    <Page
        x:Class="ArithmeticUI.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:SimpleMath"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
            <TextBox x:Name="_firstNumber" HorizontalAlignment="Left" Margin="414,370,0,0" TextWrapping="Wrap" Text="First Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <TextBox x:Name="_secondNumber" HorizontalAlignment="Left" Margin="613,370,0,0" TextWrapping="Wrap" Text="Second Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <Button Content="+" HorizontalAlignment="Left" Margin="557,301,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="-" HorizontalAlignment="Left" Margin="557,345,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="*" HorizontalAlignment="Left" Margin="557,389,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="/" HorizontalAlignment="Left" Margin="557,433,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="=" HorizontalAlignment="Left" Margin="755,367,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnResultsClick"/>
            <TextBox x:Name="_result" HorizontalAlignment="Left" Margin="809,370,0,0" TextWrapping="Wrap" Text="Result" VerticalAlignment="Top" Height="32" Width="163" TextAlignment="Center" IsReadOnly="True"/>
        </Grid>
    </Page>
    ```

11. Aggiornare MainPage.xaml.cs corrisponda al codice seguente:Update **MainPage.xaml.cs** to match the following code:

     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.cs)]
     [!code-vb[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.vb)]

12. Scegliere il **tasto F5** per eseguire l'app.

13. Nell'app immettere due numeri qualsiasi, scegliere un'operazione e quindi il **=** pulsante.

     Viene visualizzato il risultato corretto.

    La creazione e l'utilizzo di un SDK di estensione sono stati creati e utilizzati correttamente.

## <a name="see-also"></a>Vedere anche
- [Procedura dettagliata: Creazione di un SDK con C](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [Procedura dettagliata: Creare un SDK usando JavaScriptWalkthrough: Create an SDK using JavaScript](../extensibility/walkthrough-creating-an-sdk-using-javascript.md)
- [Creare un Software Development Kit](../extensibility/creating-a-software-development-kit.md)
