---
title: 'Procedura dettagliata: Creazione di un SDK con C# o Visual Basic | Microsoft Docs'
description: Informazioni su come creare un SDK della libreria matematica semplice usando Visual C# e quindi creare un pacchetto dell'SDK come estensione Visual Studio usando questa procedura dettagliata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
dev_langs:
- CSharp
- VB
ms.openlocfilehash: ea974e4ff65ccf027a28db9ceb35664a6d62a64559789c0bf3d865986d0831fb
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121320206"
---
# <a name="walkthrough-create-an-sdk-using-c-or-visual-basic"></a>Procedura dettagliata: Creare un SDK usando C# o Visual Basic
In questa procedura dettagliata si apprenderà come creare un SDK libreria matematica semplice usando Visual C# e quindi creare un pacchetto dell'SDK come estensione Visual Studio (VSIX). Verranno completate le procedure seguenti:

- [Per creare il componente SimpleMath Windows Runtime](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)

- [Per creare il progetto di estensione SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)
- [Per creare un'app di esempio che usa la libreria di classi](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)

## <a name="prerequisites"></a>Prerequisiti
 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per altre informazioni, vedere [Visual Studio SDK.](../extensibility/visual-studio-sdk.md)

## <a name="to-create-the-simplemath-windows-runtime-component"></a><a name="createClassLibrary"></a>Per creare il componente SimpleMath Windows Runtime

1. Sulla barra dei menu scegliere **File**  >  **nuovo**  >  **Project**.

2. Nell'elenco dei modelli espandere **Visual C#** o **Visual Basic**, scegliere il nodo **Windows Store** e quindi scegliere il modello Windows Runtime **Component** .

3. Nella casella **Nome** specificare **SimpleMath** e quindi fare clic sul **pulsante OK.**

4. In **Esplora soluzioni** aprire il menu di scelta rapida per il **nodo di progetto SimpleMath** e quindi scegliere **Proprietà**.

5. Rinominare **Class1.cs** in **Arithmetic.cs** e aggiornarlo in modo che corrisponda al codice seguente:

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrt/cs/winrtmath/arithmetic.cs" id="Snippet3":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrt/vb/winrtmath/arithmetic.vb" id="Snippet3":::

6. In **Esplora soluzioni** aprire il menu di scelta rapida per il nodo **"SimpleMath"** della soluzione e quindi **scegliere** Gestione configurazione .

    Verrà **Gestione configurazione** finestra di dialogo.

7. **Nell'elenco Configurazione soluzione attiva** scegliere **Rilascia**.

8. Nella colonna **Configurazione** verificare che la **riga SimpleMath** sia impostata su **Release** e quindi scegliere il **pulsante** Chiudi per accettare la modifica.

   > [!IMPORTANT]
   > L'SDK per il componente SimpleMath include una sola configurazione. Questa configurazione deve essere la build di rilascio oppure le app che usano il componente non supereranno la certificazione per [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)] .

9. In **Esplora soluzioni** aprire il menu di scelta rapida per il **nodo di progetto SimpleMath** e quindi scegliere **Compila**.

## <a name="to-create-the-simplemathvsix-extension-project"></a><a name="createVSIX"></a> Per creare il progetto di estensione SimpleMathVSIX

1. Nel menu di scelta rapida per il **nodo "SimpleMath" della** soluzione scegliere **Aggiungi**  >  **nuovo Project**.

2. Nell'elenco dei modelli espandere **Visual C#** o **Visual Basic**, scegliere il nodo **Extensibility** e quindi scegliere il **modello vsix Project.**

3. Nella casella **Nome** specificare **SimpleMathVSIX** e quindi scegliere **OK.**

4. In **Esplora soluzioni** scegliere l'elemento **source.extension.vsixmanifest.**

5. Sulla barra dei menu scegliere **Visualizza**  >  **codice**.

6. Sostituire il codice XML esistente con il codice XML seguente:

   ```xml
   <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
     <Metadata>
       <Identity Id="SimpleMath" Version="1.0" Language="en-US" Publisher="[YourName]" />
       <DisplayName>SimpleMath Library</DisplayName>
       <Description xml:space="preserve">Basic arithmetic operations in a WinRT-compatible library. Implemented in C#.</Description>
     </Metadata>
     <Installation Scope="Global" AllUsers="true">
       <InstallationTarget Id="Microsoft.ExtensionSDK" TargetPlatformIdentifier="Windows" TargetPlatformVersion="v8.0" SdkName="SimpleMath" SdkVersion="1.0" />
     </Installation>
     <Prerequisites>
       <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[14.0,16.0]" />
     </Prerequisites>
     <Dependencies>
       <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" d:Source="Manual" Version="4.5" />
     </Dependencies>
     <Assets>
       <Asset Type="Microsoft.ExtensionSDK" d:Source="File" Path="SDKManifest.xml" />
     </Assets>
   </PackageManifest>
   ```

7. In **Esplora soluzioni** scegliere il **progetto SimpleMathVSIX.**

8. Sulla barra dei menu **scegliere** Project Aggiungi nuovo  >  **elemento**.

9. Nell'elenco elementi **comuni** espandere **Dati** e quindi scegliere **File XML**.

10. Nella casella **Nome** specificare `SDKManifest.xml` e quindi scegliere il **pulsante** Aggiungi.

11. In **Esplora soluzioni** aprire il menu di scelta rapida per , scegliere Proprietà e quindi impostare il valore della proprietà Includi `SDKManifest.xml` in **VSIX** su **True**. 

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

13. In **Esplora soluzioni** aprire il menu di scelta rapida per il **progetto SimpleMathVSIX,** scegliere Aggiungi **e** quindi **Nuova cartella.**

14. Rinominare la cartella in `references` .

15. Aprire il menu di scelta rapida per la **cartella Riferimenti,** scegliere **Aggiungi** e quindi **Nuova cartella.**

16. Rinominare la sottocartella in , creare una sottocartella al suo `commonconfiguration` interno e denominarla `neutral` .

17. Ripetere i quattro passaggi precedenti, questa volta rinominando la prima cartella in `redist` .

     Il progetto contiene ora la struttura di cartelle seguente:

    ```xml
    references\commonconfiguration\neutral
    redist\commonconfiguration\neutral
    ```

18. In **Esplora soluzioni** aprire il menu di scelta rapida per il **progetto SimpleMath** e quindi scegliere Apri cartella **in** Esplora file .

19. In **Esplora file** passare alla cartella *bin\Release,* aprire il menu di scelta rapida per il file **SimpleMath.winmd** e quindi scegliere **Copia**.

20. In **Esplora soluzioni** incollare il file nella cartella *references\commonconfiguration\neutral* nel **progetto SimpleMathVSIX.**

21. Ripetere il passaggio precedente incollando il file **SimpleMath.pri** nella cartella *redist\commonconfiguration\neutral* nel **progetto SimpleMathVSIX.**

22. In **Esplora soluzioni** scegliere **SimpleMath.winmd**.

23. Sulla barra dei menu scegliere **Visualizza**  >  **proprietà** (tastiera: scegliere **il tasto F4).**

24. Nella finestra **Proprietà** modificare la proprietà **Azione di** compilazione in **Contenuto** e quindi impostare la proprietà Includi **in VSIX** su **True.**

25. In **Esplora soluzioni** ripetere questo processo per **SimpleMath.pri**.

26. In **Esplora soluzioni** scegliere il **progetto SimpleMathVSIX.**

27. Sulla barra dei menu scegliere **Compila**  >  **Compilazione SimpleMathVSIX**.

28. In **Esplora soluzioni** aprire il menu di scelta rapida per il **progetto SimpleMathVSIX** e quindi scegliere Apri cartella **in** Esplora file .

29. In **Esplora file** passare alla *cartella \bin\Release* e quindi eseguire *SimpleMathVSIX.vsix* per installarlo.

30. Scegliere il **pulsante Installa,** attendere il completamento dell'installazione e quindi riavviare Visual Studio.

## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a> Per creare un'app di esempio che usa la libreria di classi

1. Sulla barra dei menu scegliere **File**  >  **nuovo**  >  **Project**.

2. Nell'elenco dei modelli espandere **Visual C#** o **Visual Basic** e quindi scegliere il Windows **Store.**

3. Scegliere il **modello App** vuota, assegnare al progetto il nome **ArithmeticUI** e quindi scegliere **OK.**

4. In **Esplora soluzioni** aprire il menu di scelta rapida per il **progetto ArithmeticUI** e quindi scegliere **Aggiungi**  >  **riferimento**.

5. Nell'elenco dei tipi riferimento espandere **Windows** e quindi scegliere **Estensioni**.

6. Nel riquadro dei dettagli scegliere **l'estensione Libreria matematica WinRT.**

    Vengono visualizzate altre informazioni sull'SDK. È possibile scegliere il **collegamento Altre** informazioni per aprire , come specificato nel file SDKManifest.xml https://msdn.microsoft.com/ in precedenza in questa procedura dettagliata.

7. Nella finestra **di dialogo Gestione** riferimenti selezionare la casella di controllo Libreria matematica **WinRT** e quindi scegliere **OK.**

8. Sulla barra dei menu scegliere **Visualizza**  >  **Visualizzatore oggetti**.

9. **Nell'elenco Sfoglia** scegliere **Simple Math**.

     È ora possibile esplorare gli elementi dell'SDK.

10. In **Esplora soluzioni** aprire **MainPage.xaml** e sostituirlo con il codice XAML seguente:

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

11. Aggiornare **MainPage.xaml.cs in modo** che corrisponda al codice seguente:

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using Windows.Foundation;
using Windows.Foundation.Collections;
using Windows.UI.Xaml;
using Windows.UI.Xaml.Controls;
using Windows.UI.Xaml.Controls.Primitives;
using Windows.UI.Xaml.Data;
using Windows.UI.Xaml.Input;
using Windows.UI.Xaml.Media;
using Windows.UI.Xaml.Navigation;

// The Blank Page item template is documented at http://go.microsoft.com/fwlink/?LinkId=234238

namespace ArithmeticUI
{
    /// <summary>
    /// An empty page that can be used on its own or navigated to within a Frame.
    /// </summary>
    public sealed partial class MainPage : Page
    {
        public static string operation = null;

        public MainPage()
        {
            this.InitializeComponent();
        }

        /// <summary>
        /// Invoked when this page is about to be displayed in a Frame.
        /// </summary>
        /// <param name="e">Event data that describes how this page was reached.  The Parameter
        /// property is typically used to configure the page.</param>
        protected override void OnNavigatedTo(NavigationEventArgs e)
        {
        }

        /// <summary>
        /// Sets the operator chosen by the user
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void OnOperatorClick(object sender, RoutedEventArgs e)
        {
            operation = (sender as Button).Content.ToString();
        }

        /// <summary>
        /// Calls the SimpleMath SDK to do simple arithmetic
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void OnResultsClick(object sender, RoutedEventArgs e)
        {
            try
            {
                float firstNumber = float.Parse(this._firstNumber.Text);
                float secondNumber = float.Parse(this._secondNumber.Text);

                SimpleMath.Arithmetic math = new SimpleMath.Arithmetic();

                switch (operation)
                {
                    case "+":
                        this._result.Text = (math.add(firstNumber, secondNumber)).ToString();
                        break;
                    case "-":
                        this._result.Text = (math.subtract(firstNumber, secondNumber)).ToString();
                        break;
                    case "*":
                        this._result.Text = (math.multiply(firstNumber, secondNumber)).ToString();
                        break;
                    case "/":
                        this._result.Text = (math.divide(firstNumber, secondNumber)).ToString();
                        break;
                    default:
                        this._result.Text = "Choose operator";
                        break;
                }
            }
            catch
            {
                this._result.Text = "Enter valid #";
            }
        }
    }
}
```

```vb
' The Blank Page item template is documented at http://go.microsoft.com/fwlink/?LinkId=234238

''' <summary>
''' An empty page that can be used on its own or navigated to within a Frame.
''' </summary>
Public NotInheritable Class MainPage
    Inherits Page

    ''' <summary>
    ''' Invoked when this page is about to be displayed in a Frame.
    ''' </summary>
    ''' <param name="e">Event data that describes how this page was reached.  The Parameter
    ''' property is typically used to configure the page.</param>
    Protected Overrides Sub OnNavigatedTo(e As Navigation.NavigationEventArgs)
    
    End Sub

    Public Shared operation As String = Nothing

    ''' <summary>
    ''' Sets the operator chosen by the user
    ''' </summary>
    ''' <param name="sender"></param>
    ''' <param name="e"></param>
    Private Sub OnOperatorClick(ByVal sender As Object, ByVal e As RoutedEventArgs)
        operation = If(TypeOf sender Is Button, CType(sender, Button), Nothing).Content.ToString()
    End Sub


    ''' <summary>
    ''' Calls the SimpleMath SDK to do simple arithmetic
    ''' </summary>
    ''' <param name="sender"></param>
    ''' <param name="e"></param>
    Private Sub OnResultsClick(ByVal sender As Object, ByVal e As RoutedEventArgs)

        Try

            Dim firstNumber As Single = Single.Parse(Me._firstNumber.Text)
            Dim secondNumber As Single = Single.Parse(Me._secondNumber.Text)

            Dim math As New SimpleMath.Arithmetic()

            Select Case (operation)

                Case "+"
                    Me._result.Text = (math.Add(firstNumber, secondNumber)).ToString()

                Case "-"
                    Me._result.Text = (math.Subtract(firstNumber, secondNumber)).ToString()
                Case "*"
                    Me._result.Text = (math.Multiply(firstNumber, secondNumber)).ToString()
                Case "/"
                    Me._result.Text = (math.Divide(firstNumber, secondNumber)).ToString()
                Case Else
                    Me._result.Text = "Choose operator"

            End Select

        Catch
            Me._result.Text = "Enter valid #"
        End Try
    End Sub
End Class
```

12. Premere **F5 per** eseguire l'app.

13. Nell'app immettere due numeri, scegliere un'operazione e quindi scegliere il **=** pulsante .

     Viene visualizzato il risultato corretto.

    È stato creato e usato correttamente un SDK di estensione.

## <a name="see-also"></a>Vedi anche
- [Procedura dettagliata: Creare un SDK con C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [Procedura dettagliata: Creare un SDK usando JavaScript](../extensibility/walkthrough-creating-an-sdk-using-javascript.md)
- [Creare un Software Development Kit](../extensibility/creating-a-software-development-kit.md)
