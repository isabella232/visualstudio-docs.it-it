---
title: Controllare le proprietà XAML durante il debug | Microsoft Docs
ms.date: 03/06/2017
ms.topic: conceptual
ms.assetid: 390edde4-7b8d-4c89-8d69-55106b7e6b11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: fdb973718e56279e7bfb04c9d412bcd83410223d
ms.sourcegitcommit: 0e482cfc15f809b564c3de61646f29ecd7bfcba6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/14/2019
ms.locfileid: "70987745"
---
# <a name="inspect-xaml-properties-while-debugging"></a>Analizzare le proprietà XAML durante il debug
Gli strumenti **Struttura ad albero visuale attiva** ed **Esplora proprietà attive** offrono un punto di vista in tempo reale sul codice XAML. Questi strumenti offrono una visualizzazione albero degli elementi dell'interfaccia utente dell'applicazione XAML in esecuzione e mostrano le proprietà di runtime di qualsiasi elemento dell'interfaccia utente selezionato.

È possibile usare questi strumenti nelle configurazioni seguenti:

|Tipo di app|Sistema operativo e strumenti|
|-----------------|--------------------------------|
|Applicazioni Windows Presentation Foundation (4.0 e versioni successive)|Windows 7 e versioni successive|
|App di Windows universale|Windows 10 e versioni successive, con [Windows 10 SDK](https://dev.windows.com/en-us/downloads/windows-10-sdk)|

## <a name="looking-at-elements-in-the-live-visual-tree"></a>Visualizzazione degli elementi nella finestra Struttura ad albero visuale attiva
Per iniziare, verrà analizzata un'applicazione WPF molto semplice con una visualizzazione elenco e un pulsante. Ogni volta che si fa clic sul pulsante, viene aggiunto un altro elemento all'elenco. Gli elementi pari sono di colore grigio e quelli dispari sono gialli.

Creare una nuova applicazione WPF in C# (File > Nuovo > Progetto, quindi selezionare C# e cercare Applicazione WPF). Assegnare all'applicazione il nome **TestXAML**.

Modificare MainWindow.xaml come segue:

```xaml
<Window x:Class="TestXAML.MainWindow"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    xmlns:local="clr-namespace:TestXAML"
    mc:Ignorable="d"
    Title="MainWindow" Height="350" Width="525">
    <Grid>
        <Button x:Name="button" Background="LightBlue" Content="Add Item" HorizontalAlignment="Left" Margin="216,206,0,0" VerticalAlignment="Top" Width="75" Click="button_Click"/>
        <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="100" VerticalAlignment="Top" Width="100" Margin="205,80,0,0"/>
    </Grid>
</Window>
```

Aggiungere il gestore del comando seguente al file MainWindow.xaml.cs:

```csharp
int count;

private void button_Click(object sender, RoutedEventArgs e)
{
    ListBoxItem item = new ListBoxItem();
    item.Content = "Item" + ++count;
    if (count % 2 == 0)
    {
        item.Background = Brushes.LightGray;
    }
    else
    {
        item.Background = Brushes.LightYellow;
    }
    listBox.Items.Add(item);
}
```

Compilare il progetto e avviare il debug. La build deve essere configurata per il debug, non per il rilascio. Per altre informazioni sulle configurazioni della build, vedere [Informazioni sulle configurazioni della build](../ide/understanding-build-configurations.md).

Quando la finestra viene visualizzata, fare clic sul pulsante **Aggiungi elemento** un paio di volte. Viene visualizzato un output simile al seguente:

![Finestra principale dell'app](../debugger/media/livevisualtree-app.png "LiveVIsualTree-app")

Aprire quindi la finestra **Struttura ad albero visuale attiva** (**Debug > Finestre > Struttura ad albero visuale attiva** o cercarla sul lato sinistro dell'IDE). Rilasciare la finestra dalla posizione di ancoraggio in modo da poterla visualizzare affiancata alla finestra delle **proprietà attive**. Nella finestra **Struttura ad albero visuale attiva** espandere il nodo **ContentPresenter**. Tale nodo dovrebbe contenere i nodi per il pulsante e la casella di riepilogo. Espandere la casella di riepilogo, listBox, (e quindi **ScrollContentPresenter** e **ItemsPresenter**) per individuare i relativi elementi. La finestra dovrebbe essere simile alla seguente:

![ListBoxItem nell'albero elementi visivi attivi](../debugger/media/livevisualtree-listboxitems.png "LiveVisualTree-ListBoxItems")

Tornare alla finestra dell'applicazione e aggiungere altri elementi. Nella finestra **Albero elementi visivi attivi** dovrebbero venire visualizzati altri elementi casella di riepilogo.

Esaminare ora le proprietà di uno degli elementi casella di riepilogo. Selezionare il primo elemento casella di riepilogo nella finestra **Struttura ad albero visuale attiva** e fare clic sull'icona **Mostra proprietà** sulla barra degli strumenti. Dovrebbe venire visualizzata la finestra **Esplora proprietà attive**. Si noti che il campo **Contenuto** è "Item1" e il campo **Sfondo** è **#FFFFFFE0** (giallo chiaro). Tornare alla finestra **Struttura ad albero visuale attiva** e selezionare il secondo elemento casella di riepilogo. In **Esplora proprietà attive** il campo **Contenuto** dovrebbe essere "Item2" e il campo **Sfondo** **#FFD3D3D3** (grigio chiaro).

La struttura effettiva del codice XAML include numerosi elementi a cui probabilmente non si è direttamente interessati e se non si conosce bene il codice potrebbe risultare difficile esplorare l'albero per trovare ciò che si sta cercando. Lo strumento **Struttura ad albero visuale attiva** offre alcuni modi per usare l'interfaccia utente dell'applicazione per individuare l'elemento che si vuole esaminare.

**Abilita la selezione nell'applicazione in esecuzione**. È possibile abilitare questa modalità quando si seleziona il pulsante all'estrema sinistra sulla barra degli strumenti nella finestra **Struttura ad albero visuale attiva**. Quando questa modalità è attivata, è possibile selezionare un elemento dell'interfaccia utente nell'applicazione affinché lo strumento **Struttura ad albero visuale attiva** (e il **visualizzatore delle proprietà attive**) si aggiorni automaticamente per mostrare il nodo nell'albero corrispondente a tale elemento e le relative proprietà.

**Visualizza gli Adorner layout nell'applicazione in esecuzione**. È possibile abilitare questa modalità quando si seleziona il pulsante immediatamente a destra del pulsante di abilitazione della selezione. Quando l'opzione **Visualizza gli Adorner layout** è attivata, la finestra dell'applicazione mostra le linee orizzontali e verticali lungo i bordi dell'oggetto selezionato, per consentire di vederne l'allineamento, nonché rettangoli che mostrano i margini. Ad esempio, attivare entrambe le opzioni **Abilita selezione** e **Visualizza gli Adorner layout** e selezionare il blocco di testo **Aggiungi elemento** nell'applicazione. Dovrebbero venire visualizzati il nodo del blocco di testo in **Struttura ad albero visuale attiva** e le proprietà del blocco di testo nel **visualizzatore delle proprietà attive**, nonché le linee orizzontali e verticali lungo i bordi del blocco di testo.

![LivePropertyViewer in DisplayLayout](../debugger/media/livevisualtreelivepropertyviewer-displaylayout.png "LiveVisualTreeLivePropertyViewer-DisplayLayout")

**Anteprima selezione**. È possibile abilitare questa modalità selezionando il terzo pulsante da sinistra sulla barra degli strumenti nella finestra Albero elementi visivi attivi. Questa modalità mostra il codice XAML in cui è stato dichiarato l'elemento, se si ha accesso al codice sorgente dell'applicazione. Selezionare le opzioni **Abilita selezione** e **Anteprima selezione** e quindi selezionare il pulsante nell'applicazione di test. Il file MainWindow.xaml verrà aperto in Visual Studio e il cursore verrà posizionato sulla riga in cui è definito il pulsante.

## <a name="using-xaml-tools-with-running-applications"></a>Uso di strumenti XAML con applicazioni in esecuzione
È possibile usare questi strumenti XAML anche quando non si ha il codice sorgente. Quando si esegue l'associazione a un'applicazione XAML in esecuzione, è possibile usare lo strumento **Struttura ad albero visuale attiva** anche per gli elementi dell'interfaccia utente di tale applicazione. Di seguito è riportato un esempio che usa la stessa applicazione di test WPF usata in precedenza.

1. Avviare l'applicazione **TestXaml** nella configurazione di rilascio. Non è possibile eseguire l'associazione a un processo in esecuzione in una configurazione di tipo**Debug**.

2. Aprire una seconda istanza di Visual Studio e fare clic su **Debug > Associa a processo**. Trovare **TestXaml.exe** nell'elenco di processi disponibili e fare clic su **Associa**.

3. Viene avviata l'esecuzione dell'applicazione.

4. Nella seconda istanza di Visual Studio aprire la finestra **Struttura ad albero visuale attiva** (**Debug > Finestre > Struttura ad albero visuale attiva**). Dovrebbero venire visualizzati gli elementi dell'interfaccia utente di **TestXaml** e dovrebbe essere possibile modificarli nello stesso modo in cui sono stati modificati direttamente durante il debug dell'applicazione.

## <a name="see-also"></a>Vedere anche

[Scrivere ed eseguire il debug del codice XAML in esecuzione con il ricaricamento attivo XAML](xaml-hot-reload.md)
