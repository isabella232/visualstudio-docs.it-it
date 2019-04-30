---
title: 'Procedura dettagliata: Il primo Applicazione2 di Desktop WPF | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 3c460fa9-2ea1-413f-ae54-54a1f2a499d1
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bee99bc546eca3787db1f9cd082359afb6881d10
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63421142"
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a>Procedura dettagliata: Prima applicazione Desktop WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

name = "Introduzione" ></a> questa procedura dettagliata fornisce un'introduzione allo sviluppo di Windows Presentation Foundation (WPF). Si creerà un'applicazione di base che include gli elementi che sono comuni alla maggior parte delle applicazioni desktop WPF: Markup XAML, code-behind, definizioni delle applicazioni, controlli, layout, associazione dati e stili.  
  
## <a name="Create_The_Application_Code_Files"></a> Creazione del progetto di applicazione  
 In questa sezione verrà creata l'infrastruttura dell'applicazione, che include il progetto e una finestra principale o un modulo.  
  
#### <a name="to-create-the-project"></a>Per creare il progetto  
  
1. Nella barra dei menu scegliere **File**, **Nuovo**, **Progetto**.  
  
2. Nella finestra di dialogo **Nuovo progetto** espandere il nodo **Visual C#** o **Visual Basic** e scegliere il nodo **Windows** , quindi espandere il nodo **Windows** e scegliere il nodo **Desktop classico** .  
  
3. Nell'elenco dei modelli scegliere il modello **Applicazione WPF** .  
  
4. Nella finestra di dialogo **Nome** immettere `ExpenseIt`, quindi scegliere il pulsante **OK** .  
  
     Il progetto viene creato, i file del progetto vengono aggiunti a **Esplora soluzioni**e viene visualizzata la finestra di progettazione per la finestra dell'applicazione predefinita denominata **MainWindow.xaml** .  
  
#### <a name="to-modify-the-main-window"></a>Per modificare la finestra principale  
  
1. Nella finestra di progettazione scegliere la scheda **MainWindow.xaml** se non è già la scheda della finestra di progettazione attiva.  
  
2. Se si usa C#, trovare la riga `<Window x:Class="ExpenseIt.MainWindow"` e sostituirla con `<NavigationWindow x:Class="ExpenseIt.MainWindow"`.  
  
     Se si usa Visual Basic, trovare la riga `<Window x:Class=" MainWindow"` e sostituirla con `<NavigationWindow x:Class="MainWindow"`.  
  
     Quando si modifica il tag `<Window` in `<NavigationWindow`, Intellisense modifica automaticamente anche il tag di chiusura in `</NavigationWindow>` .  
  
    > [!NOTE]
    > Dopo aver modificato il tag, potrebbero essere visualizzati diversi errori se è aperta la finestra **Elenco errori** . Le modifiche che verranno apportate nei passaggi successivi elimineranno gli errori visualizzati.  
  
3. Scegliere i tag `<Grid>` e `</Grid>` ed eliminarli.  
  
     **NavigationWindow** non può contenere altri elementi dell'interfaccia utente come **Grid**.  
  
4. Nella finestra di dialogo **Proprietà** espandere il nodo della categoria **Common** e scegliere la proprietà **Title** , quindi immettere `ExpenseIt` e premere **INVIO** .  
  
     L'elemento **Title** nella finestra XAML viene modificato per corrispondere al nuovo valore. È possibile modificare le proprietà XAML nella finestra XAML o **Proprietà** e le modifiche risulteranno sincronizzate.  
  
5. Nella finestra XAML impostare il valore dell'elemento **Height** su `375`e il valore della proprietà **Width** su `500`.  
  
     Questi elementi corrispondono alle proprietà **Height** e **Width** della categoria **Layout** nella finestra **Proprietà** .  
  
     Il file **MainWindow.xaml** dovrebbe essere simile a questo in C#:  
  
    ```xaml  
    <NavigationWindow x:Class="ExpenseIt.MainWindow"  
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
            xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
            xmlns:local="clr-namespace:ExpenseIt"  
            mc:Ignorable="d"  
            Title="ExpenseIt" Height="375" Width="500">  
  
    </NavigationWindow>  
    ```  
  
     O a questo in Visual Basic:  
  
    ```xaml  
    <NavigationWindow x:Class="MainWindow"  
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
            xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
            xmlns:local="clr-namespace:ExpenseIt"  
            mc:Ignorable="d"  
            Title="ExpenseIt" Height="375" Width="500">  
  
    </NavigationWindow>  
    ```  
  
#### <a name="to-modify-the-code-behind-file-c"></a>Per modificare il file code-behind (C#)  
  
1. In **Esplora soluzioni**espandere il nodo **MainWindow.xaml** e aprire il file **MainWindow.xaml.cs** .  
  
2. Trovare la riga `public partial class MainWindow : Window` e sostituirla con `public partial class MainWindow : NavigationWindow`.  
  
     La classe `MainWindow` che deve essere derivata da `NavigationWindow`viene modificata. In Visual Basic questa modifica viene eseguita automaticamente quando si modifica la finestra in XAML, quindi non sono necessarie modifiche al codice.  
  
## <a name="add_files_to_the_application"></a> Aggiunta di file all'applicazione  
 In questa sezione verranno aggiunte due pagine e un'immagine all'applicazione.  
  
#### <a name="to-add-a-home-screen"></a>Per aggiungere una schermata iniziale  
  
1. In **Esplora soluzioni**aprire il menu di scelta rapida per il nodo **ExpenseIt** e scegliere **Aggiungi**, **Pagina**.  
  
2. Nella finestra di dialogo **Aggiungi nuovo elemento** scegliere la casella di testo **Nome** e immettere `ExpenseItHome`, quindi scegliere il pulsante **Aggiungi** .  
  
     Questa pagina è la prima finestra visualizzata quando viene avviata l'applicazione.  
  
3. Nella finestra di progettazione scegliere la scheda **ExpenseItHome.xaml** se non è già la scheda della finestra di progettazione attiva.  
  
4. Scegliere l'elemento `<Title>` e modificare il titolo in **ExpenseIt – Home**.  
  
     Il file **ExpenseItHome.xaml** dovrebbe essere simile a questo in C#:  
  
    ```xaml  
    <Page x:Class="ExpenseIt.ExpenseItHome"  
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"   
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"   
          xmlns:local="clr-namespace:ExpenseIt"  
          mc:Ignorable="d"   
          d:DesignHeight="300" d:DesignWidth="300"  
          Title="ExpenseIt - Home">  
  
        <Grid>  
  
        </Grid>  
    </Page>  
    ```  
  
     O a questo in Visual Basic:  
  
    ```xaml  
    <Page x:Class="ExpenseItHome"  
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"   
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"   
          xmlns:local="clr-namespace:ExpenseIt"  
          mc:Ignorable="d"   
          d:DesignHeight="300" d:DesignWidth="300"  
          Title="ExpenseIt - Home">  
        <Grid>  
  
        </Grid>  
    </Page>  
    ```  
  
5. Nella finestra di progettazione scegliere la scheda **MainWindow.xaml** .  
  
6. Trovare l'elemento `Title="ExpenseIt" Height="375" Width="500">` della riga e aggiungere una proprietà `Source="ExpenseItHome.xaml"` .  
  
     **ExpenseItHome.xaml** viene impostata come la prima pagina aperta all'avvio dell'applicazione. Il file **MainWindow.xaml** dovrebbe essere simile a questo in C#:  
  
    ```xaml  
    <NavigationWindow x:Class="ExpenseIt.MainWindow"  
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
            xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
            xmlns:local="clr-namespace:ExpenseIt"  
            mc:Ignorable="d"  
            Title="ExpenseIt" Height="375" Width="500" Source="ExpenseItHome.xaml">  
  
    </NavigationWindow>  
    ```  
  
     O a questo in Visual Basic:  
  
    ```xaml  
    <NavigationWindow x:Class="MainWindow"  
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
            xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
            xmlns:local="clr-namespace:ExpenseIt"  
            mc:Ignorable="d"  
            Title="ExpenseIt" Height="375" Width="500" Source="ExpenseItHome.xaml">  
  
    </NavigationWindow>  
    ```  
  
     Come per le proprietà impostate precedentemente, la proprietà `Source` potrebbe essere stata impostata nella categoria **Varie** della finestra **Proprietà** .  
  
#### <a name="to-add-a-details-window"></a>Per aggiungere una finestra dei dettagli  
  
1. In **Esplora soluzioni**aprire il menu di scelta rapida per il nodo **ExpenseIt** e scegliere **Aggiungi**, **Pagina**.  
  
2. Nella finestra di dialogo **Aggiungi nuovo elemento** scegliere la casella di testo **Nome** e immettere `ExpenseReportPage`, quindi scegliere il pulsante **Aggiungi** .  
  
     Questa finestra visualizzerà una singola nota spese.  
  
3. Nella finestra di progettazione scegliere la scheda **ExpenseReportPage.xaml** se non è già la scheda della finestra di progettazione attiva.  
  
4. Scegliere l'elemento `<Title>` e modificare il titolo in **ExpenseIt – View Expense**.  
  
     Il file ExpenseReportPage.xaml dovrebbe essere simile a questo in C#:  
  
    ```xaml  
    <Page x:Class="ExpenseIt.ExpenseReportPage"  
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"   
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"   
          xmlns:local="clr-namespace:ExpenseIt"  
          mc:Ignorable="d"   
          d:DesignHeight="300" d:DesignWidth="300"  
          Title="ExpenseIt - View Expense">  
  
        <Grid>  
  
        </Grid>  
    </Page>  
    ```  
  
     O a questo in Visual Basic:  
  
    ```xaml  
    <Page x:Class="ExpenseReportPage"  
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"   
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"   
          xmlns:local="clr-namespace:ExpenseIt"  
          mc:Ignorable="d"   
          d:DesignHeight="300" d:DesignWidth="300"  
          Title="ExpenseIt - View Expense">  
        <Grid>  
  
        </Grid>  
    </Page>  
    ```  
  
5. Nella barra dei menu scegliere **Debug**, **Avvia debug** (o premere F5) per eseguire l'applicazione.  
  
     La figura seguente mostra l'applicazione con i pulsanti della finestra di navigazione.  
  
     ![Schermata dell'esempio ExpenseIt](../designers/media/gettingstartedfigure1.png "GettingStartedFigure1")  
  
6. Chiudere l'applicazione per tornare alla modalità di progettazione.  
  
## <a name="Add_Layout"></a> Creazione dell'interfaccia utente  
 Il layout consente di posizionare gli elementi in modo ordinato e di gestire le dimensioni e la posizione degli elementi quando un modulo viene ridimensionato. In questa sezione viene creata una griglia con una sola colonna e tre righe. Vengono aggiunti i controlli alle due pagine, viene aggiunto il codice e vengono definiti gli stili riutilizzabili per i controlli.  
  
#### <a name="to-create-the-layout"></a>Per creare il layout  
  
1. Aprire **ExpenseItHome.xaml** e scegliere l'elemento `<Grid>` .  
  
2. Nella finestra di dialogo **Proprietà** espandere il nodo della categoria **Layout** e impostare i valori **Margin** su `10`, `10`, `0`e `10`, che corrispondono ai margini sinistro, destro, superiore e inferiore.  
  
     L'elemento `Margin="10,0,10,10"` viene aggiunto all'elemento `<Grid>` in XAML. Anche in questo caso è possibile che i valori siano stati immessi direttamente nel codice XAML invece che nella finestra **Proprietà** con lo stesso risultato.  
  
3. Aggiungere il codice code XAML seguente all'elemento `Grid` per creare le definizioni di righe e colonne:  
  
    ```xaml  
    <Grid.ColumnDefinitions>  
        <ColumnDefinition />  
    </Grid.ColumnDefinitions>  
    <Grid.RowDefinitions>  
        <RowDefinition Height="Auto"/>  
        <RowDefinition />  
        <RowDefinition Height="Auto"/>  
    </Grid.RowDefinitions>  
    ```  
  
#### <a name="to-add-controls"></a>Per aggiungere controlli  
  
1. Aprire **ExpenseItHome.xaml**.  
  
2. Aggiungere il codice XAML seguente subito sopra il tag `</Grid>` per creare i controlli `Border`, `ListBox` e `Button` .  
  
    ```xaml  
    <!-- People list -->  
      <Border Grid.Column="0" Grid.Row="0" Height="35" Padding="5" Background="#4E87D4">  
          <Label VerticalAlignment="Center" Foreground="White">Names</Label>  
      </Border>  
      <ListBox Name="peopleListBox" Grid.Column="0" Grid.Row="1">  
          <ListBoxItem>Mike</ListBoxItem>  
          <ListBoxItem>Lisa</ListBoxItem>  
          <ListBoxItem>John</ListBoxItem>  
          <ListBoxItem>Mary</ListBoxItem>  
      </ListBox>  
  
      <!-- View report button -->  
      <Button Grid.Column="0" Grid.Row="2" Margin="0,10,0,0" Width="125"  
    Height="25" HorizontalAlignment="Right">View</Button>  
  
    ```  
  
     I controlli vengono visualizzati nella finestra di progettazione. I controlli possono essere stati creati anche usando il trascinamento dalla finestra **Casella degli strumenti** alla finestra di progettazione e impostando le proprietà nella finestra **Proprietà** .  
  
3. Compilare ed eseguire l'applicazione. La figura seguente mostra l'aspetto in fase di esecuzione dei controlli creati da XAML in questa procedura.  
  
     ![Schermata dell'esempio ExpenseIt](../designers/media/gettingstartedfigure2.png "GettingStartedFigure2")  
  
4. Chiudere l'applicazione per tornare alla modalità di progettazione.  
  
#### <a name="to-add-a-background-image"></a>Per aggiungere un'immagine di sfondo  
  
1. Scegliere l'immagine seguente e salvarla come `watermark.png`.  
  
     ![Immagine filigrana per la procedura dettagliata](../designers/media/wpf-watermark.png "WPF_watermark")  
  
    > [!NOTE]
    > In alternativa, è possibile creare una propria immagine e salvarla come `watermark.png`.  
  
2. In **Esplora soluzioni**aprire il menu di scelta rapida per il nodo **ExpenseIt** e scegliere **Aggiungi**, **Elemento esistente**.  
  
3. Nella finestra di dialogo **Aggiungi elemento esistente** trovare l'immagine **watermark.png** appena aggiunta, selezionarla e scegliere il pulsante **Aggiungi** .  
  
    > [!NOTE]
    > Potrebbe essere necessario espandere l'elenco **Tipi di file** e scegliere **File di immagine**.  
  
4. Aprire il file **ExpenseItHome.xaml** e aggiungere il codice XAML seguente subito sopra il tag `</Grid>` per creare un'immagine di sfondo:  
  
    ```xaml  
    <Grid.Background>  
        <ImageBrush ImageSource="watermark.png"/>  
    </Grid.Background>  
  
    ```  
  
#### <a name="to-add-a-title"></a>Per aggiungere un titolo  
  
1. Aprire **ExpenseItHome.xaml**.  
  
2. Trovare la riga `<Grid.ColumnDefinitions>` e aggiungere quanto segue sotto di essa:  
  
    ```xaml  
    <ColumnDefinition Width="230" />  
  
    ```  
  
     Viene creata una colonna aggiuntiva a sinistra delle altre colonne, con una larghezza fissa di 230 pixel.  
  
3. Trovare la riga `<Grid.RowDefinitions>` e aggiungere quanto segue sotto di essa:  
  
    ```xaml  
    <RowDefinition />  
  
    ```  
  
     Viene aggiunta una riga nella parte superiore della griglia.  
  
4. Spostare i controlli nella seconda colonna impostando il valore `Grid.Column` su 1. Spostare ogni controllo verso il basso di una riga, aumentando ogni valore `Grid.Row` di 1.  
  
    1. Trovare la riga `<Border Grid.Column="0" Grid.Row="0" Height="35" Padding="5" Background="#4E87D4">`. Modificare `Grid.Column="0"` in `Grid.Column="1"` e `Grid.Row="0"` in `Grid.Row="1"`.  
  
    2. Trovare la riga `<ListBox Name="peopleListBox" Grid.Column="0" Grid.Row="1"`. Modificare `Grid.Column="0"` in `Grid.Column="1"` e `Grid.Row="1"` in `Grid.Row="2"`.  
  
    3. Trovare la riga `<Button Grid.Column="0" Grid.Row="2" Margin="0,10,0,0" Width="125"`. Modificare `Grid.Column="0"` in `Grid.Column="1"` e `Grid.Row="2"` in `Grid.Row="3"`.  
  
5. Subito prima dell'elemento `<Border` , aggiungere il codice XAML seguente per visualizzare il titolo:  
  
    ```xaml  
    <Label Grid.Column="1" VerticalAlignment="Center" FontFamily="Trebuchet MS"   
            FontWeight="Bold" FontSize="18" Foreground="#0066cc">  
        View Expense Report  
    </Label>  
  
    ```  
  
     Il contenuto di **ExpenseItHome.xaml** dovrebbe essere simile a questo in C#:  
  
    ```xaml  
    <Page x:Class="ExpenseIt.ExpenseItHome"  
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"   
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"   
          xmlns:local="clr-namespace:ExpenseIt"  
          mc:Ignorable="d"   
          d:DesignHeight="300" d:DesignWidth="300"  
          Title="ExpenseIt - Home">  
        <Grid Margin="10,0,10,10">  
            <Grid.ColumnDefinitions>  
                <ColumnDefinition Width="230" />  
                <ColumnDefinition />  
            </Grid.ColumnDefinitions>  
            <Grid.RowDefinitions>  
                <RowDefinition />  
                <RowDefinition Height="Auto"/>  
                <RowDefinition />  
                <RowDefinition Height="Auto"/>  
            </Grid.RowDefinitions>  
            <Border Grid.Column="1" Grid.Row="1" Height="35" Padding="5" Background="#4E87D4">  
                <Label VerticalAlignment="Center" Foreground="White">Names</Label>  
            </Border>  
            <!-- People list -->  
            <Label Grid.Column="1" VerticalAlignment="Center" FontFamily="Trebuchet MS"   
            FontWeight="Bold" FontSize="18" Foreground="#0066cc">  
                View Expense Report  
            </Label>  
            <ListBox Name="peopleListBox" Grid.Column="1" Grid.Row="2">  
                <ListBoxItem>Mike</ListBoxItem>  
                <ListBoxItem>Lisa</ListBoxItem>  
                <ListBoxItem>John</ListBoxItem>  
                <ListBoxItem>Mary</ListBoxItem>  
            </ListBox>  
  
            <!-- View report button -->  
            <Button Grid.Column="1" Grid.Row="3" Margin="0,10,0,0" Width="125"  
    Height="25" HorizontalAlignment="Right">View</Button>  
            <Grid.Background>  
                <ImageBrush ImageSource="watermark.png"/>  
            </Grid.Background>  
        </Grid>  
    </Page>  
    ```  
  
     O a questo in Visual Basic:  
  
    ```xaml  
    <Page x:Class="ExpenseItHome"  
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"   
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"   
          xmlns:local="clr-namespace:ExpenseIt"  
          mc:Ignorable="d"   
          d:DesignHeight="300" d:DesignWidth="300"  
          Title="ExpenseIt - Home" >  
        <Grid Margin="10,0,10,10">  
            <Grid.ColumnDefinitions>  
                <ColumnDefinition Width="230" />  
                <ColumnDefinition />  
            </Grid.ColumnDefinitions>  
            <Grid.RowDefinitions>  
                <RowDefinition />  
                <RowDefinition Height="Auto"/>  
                <RowDefinition />  
                <RowDefinition Height="Auto"/>  
            </Grid.RowDefinitions>  
            <Border Grid.Column="1" Grid.Row="1" Height="35" Padding="5" Background="#4E87D4">  
                <Label VerticalAlignment="Center" Foreground="White">Names</Label>  
            </Border>  
            <!-- People list -->  
            <Label Grid.Column="1" VerticalAlignment="Center" FontFamily="Trebuchet MS"   
            FontWeight="Bold" FontSize="18" Foreground="#0066cc">  
                View Expense Report  
            </Label>  
            <ListBox Name="peopleListBox" Grid.Column="1" Grid.Row="2">  
                <ListBoxItem>Mike</ListBoxItem>  
                <ListBoxItem>Lisa</ListBoxItem>  
                <ListBoxItem>John</ListBoxItem>  
                <ListBoxItem>Mary</ListBoxItem>  
            </ListBox>  
  
            <!-- View report button -->  
            <Button Grid.Column="1" Grid.Row="3" Margin="0,10,0,0" Width="125"  
    Height="25" HorizontalAlignment="Right">View</Button>  
            <Grid.Background>  
                <ImageBrush ImageSource="watermark.png"/>  
            </Grid.Background>  
        </Grid>  
    </Page>  
    ```  
  
6. Se a questo punto si compila e si esegue l'applicazione, dovrebbe risultare simile alla figura seguente:  
  
     ![Schermata dell'esempio ExpenseIt](../designers/media/gettingstartedfigure3.png "GettingStartedFigure3")  
  
#### <a name="to-add-code-to-the-button"></a>Per aggiungere il codice al pulsante  
  
1. Aprire **ExpenseItHome.xaml**.  
  
2. Scegliere l'elemento `<Button` e aggiungere il codice XAML seguente subito dopo l'elemento **HorizontalAlignment="Right"** : `Click="Button_Click"`.  
  
     Viene aggiunto un gestore eventi per l'evento `Click` di Button. Il codice dell'elemento **<Button** dovrebbe essere simile al seguente:  
  
    ```  
    <!-- View report button -->  
      <Button Grid.Column="1" Grid.Row="3" Margin="0,10,0,0" Width="125"  
    Height="25" HorizontalAlignment="Right" Click="Button_Click">View</Button>  
    ```  
  
3. Aprire il file **ExpenseItHome.xaml.cs** o **ExpenseItHome.xaml.vb** .  
  
4. Aggiungere il codice seguente alla classe `ExpenseItHome` :  
  
    ```csharp  
    private void Button_Click(object sender, RoutedEventArgs e)  
    {  
        // View Expense Report  
        ExpenseReportPage expenseReportPage = new ExpenseReportPage();  
        this.NavigationService.Navigate(expenseReportPage);  
  
    }  
    ```  
  
    ```vb  
    Private Sub Button_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)  
        ' View Expense Report  
        Dim expenseReportPage As New ExpenseReportPage()  
    Me.NavigationService.Navigate(expenseReportPage)  
    End Sub  
    ```  
  
     Questo gestore eventi apre la pagina della nota spese quando viene premuto il pulsante.  
  
#### <a name="to-create-the-ui-for-the-report-page"></a>Per creare l'interfaccia utente per la pagina del report  
  
1. Aprire **ExpenseReportPage.xaml**.  
  
     Questa pagina visualizzerà la nota spese per la persona selezionata nella home page.  
  
2. Aggiungere il codice code XAML seguente tra i tag `<Grid>` e `</Grid>` :  
  
    ```xaml  
    <Grid.Background>  
        <ImageBrush ImageSource="watermark.png" />  
    </Grid.Background>  
    <Grid.ColumnDefinitions>  
        <ColumnDefinition Width="230" />  
        <ColumnDefinition />  
    </Grid.ColumnDefinitions>  
    <Grid.RowDefinitions>  
        <RowDefinition Height="Auto" />  
        <RowDefinition />  
    </Grid.RowDefinitions>  
  
    <Label Grid.Column="1" VerticalAlignment="Center" FontFamily="Trebuchet MS"   
    FontWeight="Bold" FontSize="18" Foreground="#0066cc">  
        Expense Report For:  
    </Label>  
    <Grid Margin="10" Grid.Column="1" Grid.Row="1">  
  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition />  
            <ColumnDefinition />  
        </Grid.ColumnDefinitions>  
        <Grid.RowDefinitions>  
            <RowDefinition Height="Auto" />  
            <RowDefinition Height="Auto" />  
            <RowDefinition />  
        </Grid.RowDefinitions>  
  
        <!-- Name -->  
        <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="0" Orientation="Horizontal">  
            <Label Margin="0,0,0,5" FontWeight="Bold">Name:</Label>  
            <Label Margin="0,0,0,5" FontWeight="Bold"></Label>  
        </StackPanel>  
  
        <!-- Department -->  
        <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="1" Orientation="Horizontal">  
            <Label Margin="0,0,0,5" FontWeight="Bold">Department:</Label>  
            <Label Margin="0,0,0,5" FontWeight="Bold"></Label>  
        </StackPanel>  
  
        <Grid Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="2" VerticalAlignment="Top"   
              HorizontalAlignment="Left">  
            <!-- Expense type and Amount table -->  
            <DataGrid  AutoGenerateColumns="False" RowHeaderWidth="0" >  
                <DataGrid.ColumnHeaderStyle>  
                    <Style TargetType="{x:Type DataGridColumnHeader}">  
                        <Setter Property="Height" Value="35" />  
                        <Setter Property="Padding" Value="5" />  
                        <Setter Property="Background" Value="#4E87D4" />  
                        <Setter Property="Foreground" Value="White" />  
                    </Style>  
                </DataGrid.ColumnHeaderStyle>  
                <DataGrid.Columns>  
                    <DataGridTextColumn Header="ExpenseType" />  
                    <DataGridTextColumn Header="Amount"  />  
                </DataGrid.Columns>  
            </DataGrid>  
        </Grid>  
    </Grid>  
    ```  
  
     Questa interfaccia utente è simile a quella creata per la home page, ma i dati del report vengono visualizzati in un controllo **DataGrid** .  
  
3. Compilare ed eseguire l'applicazione.  
  
4. Scegliere il pulsante **Visualizza** .  
  
     Viene visualizzata la pagina della nota spese.  
  
     La figura seguente mostra la pagina della nota spese. Notare che il pulsante di navigazione all'indietro è abilitato.  
  
     ![Schermata dell'esempio ExpenseIt](../designers/media/gettingstartedfigure4.png "GettingStartedFigure4")  
  
#### <a name="to-style-controls"></a>Controlli di stile  
  
1. Aprire il file **App.xaml** (C#) o **Application.xaml** (Visual Basic).  
  
2. Aggiungere il codice XAML seguente tra i tag `<Application.Resources>` e `</Application.Resources>` :  
  
    ```xaml  
    <!-- Header text style -->  
    <Style x:Key="headerTextStyle">  
        <Setter Property="Label.VerticalAlignment" Value="Center"></Setter>  
        <Setter Property="Label.FontFamily" Value="Trebuchet MS"></Setter>  
        <Setter Property="Label.FontWeight" Value="Bold"></Setter>  
        <Setter Property="Label.FontSize" Value="18"></Setter>  
        <Setter Property="Label.Foreground" Value="#0066cc"></Setter>  
    </Style>  
  
    <!-- Label style -->  
    <Style x:Key="labelStyle" TargetType="{x:Type Label}">  
        <Setter Property="VerticalAlignment" Value="Top" />  
        <Setter Property="HorizontalAlignment" Value="Left" />  
        <Setter Property="FontWeight" Value="Bold" />  
        <Setter Property="Margin" Value="0,0,0,5" />  
    </Style>  
  
    <!-- DataGrid header style -->  
    <Style x:Key="columnHeaderStyle" TargetType="{x:Type DataGridColumnHeader}">  
        <Setter Property="Height" Value="35" />  
        <Setter Property="Padding" Value="5" />  
        <Setter Property="Background" Value="#4E87D4" />  
        <Setter Property="Foreground" Value="White" />  
    </Style>  
  
    <!-- List header style -->  
    <Style x:Key="listHeaderStyle" TargetType="{x:Type Border}">  
        <Setter Property="Height" Value="35" />  
        <Setter Property="Padding" Value="5" />  
        <Setter Property="Background" Value="#4E87D4" />  
    </Style>  
  
    <!-- List header text style -->  
    <Style x:Key="listHeaderTextStyle" TargetType="{x:Type Label}">  
        <Setter Property="Foreground" Value="White" />  
        <Setter Property="VerticalAlignment" Value="Center" />  
        <Setter Property="HorizontalAlignment" Value="Left" />  
    </Style>  
  
    <!-- Button style -->  
    <Style x:Key="buttonStyle" TargetType="{x:Type Button}">  
        <Setter Property="Width" Value="125" />  
        <Setter Property="Height" Value="25" />  
        <Setter Property="Margin" Value="0,10,0,0" />  
        <Setter Property="HorizontalAlignment" Value="Right" />  
    </Style>  
    ```  
  
     Questo codice XAML aggiunge gli stili seguenti:  
  
    - `headerTextStyle`: Per formattare il titolo della pagina `Label`.  
  
    - `labelStyle`: Per formattare il `Label` controlli.  
  
    - `columnHeaderStyle`: Per formattare il `DataGridColumnHeader`.  
  
    - `listHeaderStyle`: Per formattare l'intestazione dell'elenco `Border` controlli.  
  
    - `listHeaderTextStyle`: Per formattare l'intestazione dell'elenco **etichetta**.  
  
    - `buttonStyle`: Per formattare il `Button` nella **ExpenseItHome. XAML** ExpenseItHome.  
  
3. Aprire **ExpenseItHome.xaml** e sostituire tutto il contenuto tra gli elementi `<Grid>` e `</Grid>` con il codice XAML seguente  
  
    ```xaml  
    <Grid.ColumnDefinitions>  
                <ColumnDefinition Width="230" />  
                <ColumnDefinition />  
            </Grid.ColumnDefinitions>  
  
            <Grid.RowDefinitions>  
                <RowDefinition/>  
                <RowDefinition Height="Auto"/>  
                <RowDefinition />  
                <RowDefinition Height="Auto"/>  
            </Grid.RowDefinitions>  
            <Label Grid.Column="1" Style="{StaticResource headerTextStyle}" >  
                View Expense Report  
            </Label>  
            <!-- People list -->  
                  <Border Grid.Column="1" Grid.Row="1" Style="{StaticResource listHeaderStyle}">  
                <Label Style="{StaticResource listHeaderTextStyle}">Names</Label>  
            </Border>  
            <ListBox Name="peopleListBox" Grid.Column="1" Grid.Row="2">  
                <ListBoxItem>Mike</ListBoxItem>  
                <ListBoxItem>Lisa</ListBoxItem>  
                <ListBoxItem>John</ListBoxItem>  
                <ListBoxItem>Mary</ListBoxItem>  
            </ListBox>  
  
            <!-- View report button -->  
            <Button Grid.Column="1" Grid.Row="3" Click="Button_Click" Style="{StaticResource buttonStyle}">View</Button>  
            <Grid.Background>  
                <ImageBrush ImageSource="watermark.png"  />  
            </Grid.Background>  
    ```  
  
     Le proprietà come `VerticalAlignment` e `FontFamily` che definiscono l'aspetto di ciascun controllo vengono rimosse e sostituite mediante l'applicazione degli stili.  
  
4. Aprire **ExpenseReportPage.xaml** e sostituire tutto il contenuto tra gli elementi `<Grid>` e gli elementi finali `</Grid>` con il codice XAML seguente  
  
    ```xaml  
    <Grid.Background>  
        <ImageBrush ImageSource="watermark.png" />  
    </Grid.Background>  
    <Grid.ColumnDefinitions>  
        <ColumnDefinition Width="230" />  
        <ColumnDefinition />  
    </Grid.ColumnDefinitions>  
    <Grid.RowDefinitions>  
        <RowDefinition Height="Auto" />  
        <RowDefinition />  
    </Grid.RowDefinitions>  
    <Label Grid.Column="1" Style="{StaticResource headerTextStyle}">  
        Expense Report For:  
    </Label>  
    <Grid Margin="10" Grid.Column="1" Grid.Row="1">  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition />  
            <ColumnDefinition />  
        </Grid.ColumnDefinitions>  
        <Grid.RowDefinitions>  
            <RowDefinition Height="Auto" />  
            <RowDefinition Height="Auto" />  
            <RowDefinition />  
        </Grid.RowDefinitions>  
  
        <!-- Name -->  
        <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="0" Orientation="Horizontal">  
            <Label Style="{StaticResource labelStyle}">Name:</Label>  
            <Label Style="{StaticResource labelStyle}"></Label>  
        </StackPanel>  
  
        <!-- Department -->  
        <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="1"   
    Orientation="Horizontal">  
            <Label Style="{StaticResource labelStyle}">Department:</Label>  
            <Label Style="{StaticResource labelStyle}"></Label>  
        </StackPanel>  
  
        <Grid Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="2" VerticalAlignment="Top"   
              HorizontalAlignment="Left">  
            <!-- Expense type and Amount table -->  
            <DataGrid ColumnHeaderStyle="{StaticResource columnHeaderStyle}"   
                      AutoGenerateColumns="False" RowHeaderWidth="0" >  
                <DataGrid.Columns>  
                    <DataGridTextColumn Header="ExpenseType" />  
                    <DataGridTextColumn Header="Amount"  />  
                </DataGrid.Columns>  
            </DataGrid>  
        </Grid>  
    </Grid>  
  
    ```  
  
     Vengono aggiunti gli stili agli elementi `<Label>` e `<Border>` .  
  
## <a name="connecting-to-data"></a>Connessione ai dati  
 In questa sezione verrà creato un provider di dati e un modello di dati e verranno connessi i controlli per visualizzare i dati.  
  
#### <a name="to-bind-data-to-a-control"></a>Per associare i dati a un controllo  
  
1. Aprire **ExpenseItHome.xaml** e scegliere l'elemento `<Grid>` .  
  
2. Aggiungere il codice code XAML seguente:  
  
    ```xaml  
  
    <Grid.Resources>  
    <!-- Expense Report Data -->  
    <XmlDataProvider x:Key="ExpenseDataSource" XPath="Expenses">  
        <x:XData>  
            <Expenses xmlns="">  
                <Person Name="Mike" Department="Legal">  
                    <Expense ExpenseType="Lunch" ExpenseAmount="50" />  
                    <Expense ExpenseType="Transportation" ExpenseAmount="50" />  
                </Person>  
                <Person Name="Lisa" Department="Marketing">  
                    <Expense ExpenseType="Document printing"  
          ExpenseAmount="50"/>  
                    <Expense ExpenseType="Gift" ExpenseAmount="125" />  
                </Person>  
                <Person Name="John" Department="Engineering">  
                    <Expense ExpenseType="Magazine subscription"   
         ExpenseAmount="50"/>  
                    <Expense ExpenseType="New machine" ExpenseAmount="600" />  
                    <Expense ExpenseType="Software" ExpenseAmount="500" />  
                </Person>  
                <Person Name="Mary" Department="Finance">  
                    <Expense ExpenseType="Dinner" ExpenseAmount="100" />  
                </Person>  
            </Expenses>  
        </x:XData>  
    </XmlDataProvider>  
    </Grid.Resources>  
    ```  
  
     Questo codice crea una classe `XmlDataProvider` che contiene i dati per ogni persona. In genere questi dati vengono caricati sotto forma di file, ma in questo caso, per semplicità, verranno aggiunti inline.  
  
3. Nell'elemento `<Grid.Resources>` aggiungere il codice XAML seguente:  
  
    ```xaml  
    <!-- Name item template -->  
    <DataTemplate x:Key="nameItemTemplate">  
        <Label Content="{Binding XPath=@Name}"/>  
    </DataTemplate>  
    ```  
  
     Viene aggiunto un `Data Template` che definisce come visualizzare i dati in **ListBox**.  
  
4. Sostituire l'elemento `<ListBox>` esistente con il codice XAML seguente.  
  
    ```xaml  
    <ListBox Name="peopleListBox" Grid.Column="1" Grid.Row="2"   
             ItemsSource="{Binding Source={StaticResource ExpenseDataSource}, XPath=Person}"  
             ItemTemplate="{StaticResource nameItemTemplate}">  
    </ListBox>  
    ```  
  
     Questo codice associa la proprietà `ItemsSource` di `ListBox` all'origine dati e applica il modello di dati come `ItemTemplate`.  
  
#### <a name="to-connect-data-to-controls"></a>Per connettere i dati ai controlli  
  
1. Aprire **ExpenseReportPage.xaml.vb** o **ExpenseReportPage.xaml.cs**.  
  
2. In C# aggiungere il costruttore seguente alla classe **ExpenseReportPage** oppure sostituire la classe esistente in Visual Basic con quanto segue:  
  
    ```csharp  
    // Custom constructor to pass expense report data  
        public ExpenseReportPage(object data):this()  
        {  
            // Bind to expense report data.  
            this.DataContext = data;  
        }  
    ```  
  
    ```vb  
    Partial Public Class ExpenseReportPage  
    Inherits Page  
    Public Sub New()  
    InitializeComponent()  
    End Sub  
  
    ' Custom constructor to pass expense report data  
    Public Sub New(ByVal data As Object)  
    Me.New()  
    ' Bind to expense report data.  
    Me.DataContext = data  
    End Sub  
  
    End Class  
    ```  
  
     Questo costruttore accetta un oggetto dati come parametro. In questo caso l'oggetto dati conterrà il nome della persona selezionata.  
  
3. Aprire **ExpenseItHome.xaml.vb** o **ExpenseItHome.xaml.cs**.  
  
4. Sostituire il codice `Click` del gestore eventi con quanto segue:  
  
    ```csharp  
    private void Button_Click(object sender, RoutedEventArgs e)  
    {  
        // View Expense Report  
        ExpenseReportPage expenseReportPage = new ExpenseReportPage(this.peopleListBox.SelectedItem);  
        this.NavigationService.Navigate(expenseReportPage);  
  
    }  
    ```  
  
    ```vb  
    Private Sub Button_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)  
        ' View Expense Report  
        Dim expenseReportPage As New ExpenseReportPage(Me.peopleListBox.SelectedItem)  
        Me.NavigationService.Navigate(expenseReportPage)  
    End Sub  
    ```  
  
     Questo codice chiama il nuovo costruttore.  
  
#### <a name="to-update-the-ui-with-data-templates"></a>Per aggiornare l'interfaccia utente con i modelli di dati  
  
1. Aprire **ExpenseReportPage.xaml**.  
  
2. Sostituire il codice XAML per gli elementi **Nome** e **Department**`<StackPanel` con quanto segue:  
  
    ```xaml  
    <!-- Name -->  
    <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="0" Orientation="Horizontal">  
        <Label Style="{StaticResource labelStyle}">Name:</Label>  
        <Label Style="{StaticResource labelStyle}" Content="{Binding XPath=@Name}"></Label>  
    </StackPanel>  
  
    <!-- Department -->  
    <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="1" Orientation="Horizontal">  
        <Label Style="{StaticResource labelStyle}">Department:</Label>  
        <Label Style="{StaticResource labelStyle}" Content="{Binding XPath=@Department}"></Label>  
    </StackPanel>  
  
    ```  
  
     Associa i controlli **Label** alle proprietà dell'origine dati appropriate.  
  
3. Aggiungere il codice code XAML seguente nell'elemento `<Grid>` :  
  
    ```xaml  
    <!--Templates to display expense report data-->  
    <Grid.Resources>  
        <!-- Reason item template -->  
        <DataTemplate x:Key="typeItemTemplate">  
            <Label Content="{Binding XPath=@ExpenseType}"/>  
        </DataTemplate>  
        <!-- Amount item template -->  
        <DataTemplate x:Key="amountItemTemplate">  
            <Label Content="{Binding XPath=@ExpenseAmount}"/>  
        </DataTemplate>  
    </Grid.Resources>  
  
    ```  
  
     Definisce come visualizzare i dati della nota spese.  
  
4. Sostituire l'elemento `<DataGrid>` con quanto segue:  
  
    ```xaml  
    <!-- Expense type and Amount table -->  
    <DataGrid ItemsSource="{Binding XPath=Expense}" ColumnHeaderStyle="{StaticResource columnHeaderStyle}" AutoGenerateColumns="False" RowHeaderWidth="0" >  
  
        <DataGrid.Columns>  
            <DataGridTextColumn Header="ExpenseType" Binding="{Binding XPath=@ExpenseType}"  />  
            <DataGridTextColumn Header="Amount" Binding="{Binding XPath=@ExpenseAmount}" />  
        </DataGrid.Columns>  
  
    </DataGrid>  
    ```  
  
     Viene aggiunto **ItemSource** e vengono definite le associazioni per gli elementi di spesa.  
  
5. Compilare ed eseguire l'applicazione.  
  
6. Scegliere una persona, quindi fare clic sul pulsante **Visualizza** .  
  
     La figura seguente mostra le due pagine dell'applicazione ExpenseIt con i controlli, il layout, gli stili, il data binding e i modelli di dati applicati.  
  
     ![Schermate dell'esempio ExpenseIt](../designers/media/gettingstartedfigure5.png "GettingStartedFigure5")  
  
## <a name="Best_Practices"></a> Procedure consigliate  
 Questo esempio illustra le nozioni di base di WPF e, di conseguenza, non segue le procedure consigliate per lo sviluppo di applicazioni. Per una descrizione completa delle procedure guidate di sviluppo di applicazioni di WPF e .NET Framework, vedere gli argomenti seguenti:  
  
- Accessibilità: [Procedure consigliate per l'accesso facilitato](https://msdn.microsoft.com/library/aa350483\(v=vs.100\).aspx)  
  
- Sicurezza: [Sicurezza di Windows Presentation Foundation](https://msdn.microsoft.com/library/aa970906\(v=vs.100\).aspx)  
  
- Localizzazione: [Panoramica della globalizzazione e localizzazione WPF](https://msdn.microsoft.com/library/ms788718\(v=vs.100\).aspx)  
  
- Prestazioni: [Ottimizzazione delle prestazioni di applicazioni WPF](https://msdn.microsoft.com/library/aa970683\(v=vs.100\).aspx)  
  
## <a name="Whats_Next"></a> Argomenti successivi  
 A questo punto si hanno diverse tecniche a disposizione per creare un'applicazione desktop con WPF. Dovrebbe essere stata acquisita una conoscenza di base dei componenti fondamentali di un'applicazione WPF con associazione ai dati. Questo argomento non è esaustivo, ma intende fornire all'utente le informazioni e gli strumenti per approfondire autonomamente le numerose opzioni di cui dispone, che vanno oltre le tecniche descritte nell'argomento.  
  
 Per altre informazioni sull'architettura WPF e i modelli di programmazione, vedere gli argomenti seguenti:  
  
- [Architettura WPF](https://msdn.microsoft.com/library/ms750441\(v=vs.100\).aspx)  
  
- [Panoramica di XAML](https://msdn.microsoft.com/library/ms752059\(v=vs.100\).aspx)  
  
- [Panoramica sulle proprietà di dipendenza](https://msdn.microsoft.com/library/ms752914\(v=vs.100\).aspx)  
  
- [Sistema di layout](https://msdn.microsoft.com/library/ms745058\(v=vs.100\).aspx)  
  
- [Stili e modelli](https://msdn.microsoft.com/library/bb613570\(v=vs.100\).aspx)  
  
  Per altre informazioni sulla creazione di applicazioni, vedere gli argomenti seguenti:  
  
- [Panoramica sullo sviluppo di applicazioni](https://msdn.microsoft.com/library/bb613549\(v=vs.100\).aspx)  
  
- [Panoramica sui controlli](https://msdn.microsoft.com/library/bb613551\(v=vs.100\).aspx)  
  
- [Panoramica sul data binding](https://msdn.microsoft.com/library/ms752347\(v=vs.100\).aspx)  
  
- [Panoramica sui grafici, l'animazione e gli elementi multimediali di WPF](https://msdn.microsoft.com/library/ms742562\(v=vs.100\).aspx)  
  
- [Documenti in WPF](https://msdn.microsoft.com/library/ms748388\(v=vs.100\).aspx)  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Creare un'applicazione Desktop WPF connessa a un servizio Mobile di Azure](../designers/walkthrough-create-a-wpf-desktop-application-connected-to-an-azure-mobile-service.md)   
 [Create Modern Desktop Applications with Windows Presentation Foundation](../designers/create-modern-desktop-applications-with-windows-presentation-foundation.md) (Creare moderne applicazioni desktop con Windows Presentation Foundation)
