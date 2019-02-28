---
title: 'Procedura dettagliata: Creazione di un SDK tramite C# o Visual Basic | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc41b980b012254ac263e027f1dd0361405c8366
ms.sourcegitcommit: cea6187005f8a0cdf44e866a1534a4cf5356208c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/27/2019
ms.locfileid: "56954008"
---
# <a name="walkthrough-create-an-sdk-using-c-or-visual-basic"></a>Procedura dettagliata: Creare un SDK tramite C# o Visual Basic
In questa procedura dettagliata si apprenderà come creare un SDK della libreria matematica semplice con Visual c# e quindi creare il pacchetto SDK come un Visual Studio Extension (VSIX). È possibile completare le procedure seguenti:

-   [Per creare il componente SimpleMath Windows Runtime](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)

-   [Per creare il progetto di estensione SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)
-   [Per creare un'app di esempio che usa la libreria di classi](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)

## <a name="prerequisites"></a>Prerequisiti
 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per altre informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

##  <a name="createClassLibrary"></a> Per creare il componente SimpleMath Windows Runtime

1. Nella barra dei menu, scegliere **File** > **New** > **nuovo progetto**.

2. Nell'elenco dei modelli, espandere **Visual c#** o **Visual Basic**, scegliere il **Windows Store** nodo, quindi scegliere il **componente di Runtime di Windows** modello.

3. Nel **nome** , specificare **SimpleMath**, quindi scegliere il **OK** pulsante.

4. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il **SimpleMath** nodo del progetto e quindi scegliere **proprietà**.

5. Rinominare **Class1.cs** al **Arithmetic.cs** e aggiornarlo in modo che corrisponda al codice seguente:

    [!code-csharp[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.cs)]
    [!code-vb[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.vb)]

6. Nella **Esplora soluzioni**, aprire il menu di scelta rapida per il **soluzione 'SimpleMath'** nodo, quindi scegliere **Configuration Manager**.

    Il **Configuration Manager** verrà visualizzata la finestra di dialogo.

7. Nel **configurazione soluzione attiva** casella di riepilogo **rilascio**.

8. Nel **Configuration** colonna, verificare che **SimpleMath** riga è impostata su **rilascio**e quindi scegliere il **Chiudi** pulsante per accettare il modificare.

   > [!IMPORTANT]
   >  il SDK per il componente SimpleMath include solo una configurazione. Questa configurazione deve essere la build di versione o le app che usano il componente non passare la certificazione il[!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)].

9. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il **SimpleMath** nodo del progetto e quindi scegliere **compilare**.

##  <a name="createVSIX"></a> Per creare il progetto di estensione SimpleMathVSIX

1.  Nel menu di scelta rapida per il **soluzione 'SimpleMath'** nodo, scegliere **Add** > **nuovo progetto**.

2.  Nell'elenco dei modelli, espandere **Visual c#** o **Visual Basic**, scegliere il **estendibilità** nodo, quindi scegliere il **progetto VSIX** modello.

3.  Nel **nome** , specificare **SimpleMathVSIX**, quindi scegliere il **OK** pulsante.

4.  Nelle **Esplora soluzioni**, scegliere il **vsixmanifest** elemento.

5.  Sulla barra dei menu scegliere **Visualizza** > **Codice**.

6.  Sostituire il codice XML esistente con il codice XML seguente:

     [!code-xml[CreatingAnSDKUsingWinRT#1](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]

7.  Nelle **Esplora soluzioni**, scegliere il **SimpleMathVSIX** progetto.

8.  Nella barra dei menu scegliere **Progetto** > **Aggiungi nuovo elemento**.

9. Nell'elenco degli **gli elementi comuni**, espandere **dati**, quindi scegliere **File XML**.

10. Nel **nome** , specificare `SDKManifest.xml`, quindi scegliere il **Aggiungi** pulsante.

11. In **Esplora soluzioni**, aprire il menu di scelta rapida `SDKManifest.xml`, scegliere **le proprietà**e quindi modificare il valore della **Includi in VSIX** proprietà per **True**.

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

13. Nel **Esplora soluzioni**, aprire il menu di scelta rapida per il **SimpleMathVSIX** del progetto, scegliere **Add**, quindi scegliere **nuova cartella**.

14. Rinominare la cartella per `references`.

15. Aprire il menu di scelta rapida per il **riferimenti** cartella, scegliere **Add**, quindi scegliere **nuova cartella**.

16. Rinominare la sottocartella `commonconfiguration`, creare una sottocartella all'interno di esso e assegnare un nome della sottocartella `neutral`.

17. Ripetere i quattro passaggi precedenti, questa volta rinominato la cartella prima di `redist`.

     Il progetto contiene ora la struttura di cartelle seguente:

    ```xml
    references\commonconfiguration\neutral
    redist\commonconfiguration\neutral
    ```

18. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il **SimpleMath** del progetto e quindi scegliere **Apri cartella in Esplora File**.

19. Nella **Esplora File**, passare alle *bin\Release* cartella, aprire il menu di scelta rapida per il **SimpleMath.winmd** file e quindi scegliere **copiare**.

20. In **Esplora soluzioni**, incollare i file nella *references\commonconfiguration\neutral* cartella la **SimpleMathVSIX** progetto.

21. Ripetere il passaggio precedente, incollare il **SimpleMath.pri** del file nel *redist\commonconfiguration\neutral* cartella nel **SimpleMathVSIX** progetto.

22. Nelle **Esplora soluzioni**, scegliere **SimpleMath.winmd**.

23. Nella barra dei menu, scegliere **View** > **proprietà** (tastiera: Scegliere il **F4** key).

24. Nel **delle proprietà** finestra Modifica il **azione di compilazione** proprietà **contenuto**e quindi modificare il **Includi in VSIX** proprietà  **True**.

25. Nelle **Esplora soluzioni**, ripetere questo processo per **SimpleMath.pri**.

26. Nelle **Esplora soluzioni**, scegliere il **SimpleMathVSIX** progetto.

27. Nella barra dei menu, scegliere **compilare** > **compilare SimpleMathVSIX**.

28. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il **SimpleMathVSIX** del progetto e quindi scegliere **Apri cartella in Esplora File**.

29. Nelle **Esplora File**, passare alla *\bin\Release* cartella e quindi eseguire *SimpleMathVSIX.vsix* per installarlo.

30. Scegliere il **installare** pulsante, attendere il completamento dell'installazione e quindi riavviare Visual Studio.

##  <a name="createSample"></a> Per creare un'app di esempio che usa la libreria di classi

1. Nella barra dei menu, scegliere **File** > **New** > **nuovo progetto**.

2. Nell'elenco dei modelli, espandere **Visual c#** oppure **Visual Basic**, quindi scegliere il **Windows Store** nodo.

3. Scegliere il **App vuota** modello, nome del progetto **ArithmeticUI**, quindi scegliere il **OK** pulsante.

4. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il **ArithmeticUI** del progetto e quindi scegliere **Add** > **riferimento**.

5. Nell'elenco dei tipi di riferimento, espandere **Windows**, quindi scegliere **estensioni**.

6. Nel riquadro dei dettagli, scegliere il **semplice Math SDK** estensione.

    Vengono visualizzate informazioni aggiuntive sul SDK. È possibile scegliere il **per altre informazioni** collegamento per aprire https://msdn.microsoft.com/, come specificato nel file Sdkmanifest più indietro in questa procedura dettagliata.

7. Nel **gestione riferimenti** finestra di dialogo, seleziona la **SDK matematiche semplici** casella di controllo e quindi scegliere il **OK** pulsante.

8. Nella barra dei menu, scegliere **View** > **Visualizzatore oggetti**.

9. Nel **esplorare** elenco, scegliere **semplice operazione matematica**.

     È ora possibile esplorare What ' s nel SDK.

10. Nelle **Esplora soluzioni**aprire **MainPage. XAML**e sostituirne il contenuto con il seguente XAML:

    **C#**
    ```xml
    <Page
        x:Class="WinRTMathTestCS.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:WinRTMathTestCS"
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
        x:Class="WinRTMathTest.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:WinRTMathTest"
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

11. Update **MainPage.xaml.cs** in modo che corrisponda il codice seguente:

     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.cs)]
     [!code-vb[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.vb)]

12. Scegliere il **F5** per eseguire l'app.

13. Nell'app, immettere tutti i due numeri, scegliere un'operazione e quindi scegliere il **=** pulsante.

     Viene visualizzato il risultato corretto.

    Avere creato e usato un SDK di estensione.

## <a name="see-also"></a>Vedere anche
- [Procedura dettagliata: Creare un SDK con C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [Procedura dettagliata: Creare un SDK con JavaScript](../extensibility/walkthrough-creating-an-sdk-using-javascript.md)
- [Creare un Software Development Kit](../extensibility/creating-a-software-development-kit.md)