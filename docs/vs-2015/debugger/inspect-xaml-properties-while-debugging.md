---
title: Controllare le proprietà XAML durante il debug | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 390edde4-7b8d-4c89-8d69-55106b7e6b11
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eb10290e14290f59950e6b291d479de2099ac7f9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47541068"
---
# <a name="inspect-xaml-properties-while-debugging"></a>Analizzare le proprietà XAML durante il debug
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [delle proprietà di ispezionare XAML durante il debug](https://docs.microsoft.com/visualstudio/debugger/inspect-xaml-properties-while-debugging).  
  
È possibile ottenere una visualizzazione in tempo reale del codice XAML in esecuzione con il **albero elementi visivi attivi** e il **Esplora proprietà attive**. Questi strumenti offrono una visualizzazione albero degli elementi dell'interfaccia utente dell'applicazione XAML in esecuzione e mostrano le proprietà di runtime di qualsiasi elemento dell'interfaccia utente selezionato.  
  
 È possibile usare questi strumenti nelle configurazioni seguenti:  
  
|Tipo di app|Sistema operativo e strumenti|  
|-----------------|--------------------------------|  
|Applicazioni Windows Presentation Foundation (4.0 e versioni successive)|Windows 7 e versioni successive|  
|App di Windows Store e Windows Phone 8.1|Windows 10 e versioni successive, con la [Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk)|  
|App di Windows universale|Windows 10 e versioni successive, con la [Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk)|  
  
## <a name="looking-at-elements-in-the-live-visual-tree"></a>Visualizzazione degli elementi nella finestra Struttura ad albero visuale attiva  
 Per iniziare, verrà analizzata un'applicazione WPF molto semplice con una visualizzazione elenco e un pulsante. Ogni volta che si fa clic sul pulsante, viene aggiunto un altro elemento all'elenco. Gli elementi pari sono di colore grigio e quelli dispari sono gialli.  
  
 Creare una nuova applicazione WPF in C# (File/Nuovo/Progetto, quindi selezionare C# e cercare Applicazione WPF). Denominarlo **TestXAML**.  
  
 Modificare MainWindow.xaml come segue:  
  
```xaml  
<Window x:Class="WpfApplication1.MainWindow"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
    xmlns:local="clr-namespace:WpfApplication1"  
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
  
 Compilare il progetto e avviare il debug. La build deve essere configurata per il debug, non per il rilascio. Per altre informazioni sulle configurazioni della build, vedere [informazioni sulle configurazioni della Build](../ide/understanding-build-configurations.md).)  
  
 Quando la finestra viene visualizzata, scegliere il **Aggiungi elemento** pulsante un paio di volte. Viene visualizzato un output simile al seguente:  
  
 ![Finestra principale dell'app](../debugger/media/livevisualtree-app.png "LiveVIsualTree-App")  
  
 A questo punto aprire il **albero elementi visivi attivi** finestra (**eseguire il Debug / Windows / albero elementi visivi attivi**, oppure individuarlo e selezionarlo lungo il lato sinistro dell'IDE). Trascinarlo dalla posizione di ancoraggio, è possibile analizzare in questa finestra e il **Live proprietà** finestra fianco a fianco. Nel **albero elementi visivi attivi** finestra, espandere il **ContentPresenter** nodo. Tale nodo dovrebbe contenere i nodi per il pulsante e la casella di riepilogo. Espandere la casella di riepilogo (e quindi il **ScrollContentPresenter** e il **ItemsPresenter**) per trovare l'elenco di elementi di finestra. La finestra dovrebbe essere simile alla seguente:  
  
 ![ListBoxItems nell'albero visuale in tempo reale](../debugger/media/livevisualtree-listboxitems.png "LiveVisualTree ListBoxItem")  
  
 Tornare alla finestra dell'applicazione e aggiungere altri elementi. Dovrebbe essere visualizzato più elementi di casella di riepilogo nel **albero elementi visivi attivi**.  
  
 Esaminare ora le proprietà di uno degli elementi casella di riepilogo. Selezionare il primo elemento di casella di riepilogo nel **albero elementi visivi attivi** e fare clic sui **Mostra proprietà** icona sulla barra degli strumenti. Il **Esplora proprietà attive** dovrebbe essere visualizzato. Si noti che il **contenuti** campo è "Item1" e il **sfondo** campo è **#ffffffe0** (giallo chiaro). Tornare al **albero elementi visivi attivi** e selezionare il secondo elemento casella di riepilogo. Il **Esplora proprietà attive** dovrebbe essere il **contenuto** campo è "Item2" e il **sfondo** campo è **#ffd3d3d3** (grigio chiaro ).  
  
 La struttura effettiva del codice XAML include numerosi elementi a cui probabilmente non si è direttamente interessati e se non si conosce bene il codice potrebbe risultare difficile esplorare l'albero per trovare ciò che si sta cercando. In modo che il **albero elementi visivi attivi** dispone di un paio di modi che consentono di utilizzare dell'interfaccia utente dell'applicazione che consentono di trovare l'elemento da esaminare.  
  
 **Abilita la selezione nell'applicazione in esecuzione**. È possibile abilitare questa modalità quando si seleziona il pulsante all'estrema sinistra nella **albero elementi visivi attivi** sulla barra degli strumenti. Con questa modalità è attivata, è possibile selezionare un elemento dell'interfaccia utente dell'applicazione e il **albero elementi visivi attivi** (e il **visualizzatore delle proprietà attive**) Aggiorna automaticamente per mostrare il nodo dell'albero corrisponde a tale elemento, e le relative proprietà.  
  
 **Visualizza gli Adorner layout nell'applicazione in esecuzione**. È possibile abilitare questa modalità quando si seleziona il pulsante immediatamente a destra del pulsante di abilitazione della selezione. Quando **Visualizza gli Adorner layout** è on, fa sì che la finestra dell'applicazione mostrare le linee orizzontali e verticali lungo i bordi dell'oggetto selezionato in modo da visualizzare vederne l'allineamento, nonché rettangoli che mostrano i margini. Ad esempio, attivare entrambe le opzioni **abilita la selezione** e **Visualizza gli Adorner layout** e selezionare il **Aggiungi elemento** blocco di testo nell'applicazione. Dovrebbe essere il nodo del blocco di testo nel **albero elementi visivi attivi** e proprietà del blocco di testo **visualizzatore delle proprietà attive**, nonché le linee orizzontali e verticali lungo i bordi del blocco di testo.  
  
 ![LivePropertyViewer in DisplayLayout](../debugger/media/livevisualtreelivepropertyviewer-displaylayout.png "LiveVisualTreeLivePropertyViewer DisplayLayout")  
  
 **Anteprima selezione**. È possibile abilitare questa modalità selezionando il terzo pulsante da sinistra sulla barra degli strumenti nella finestra Struttura ad albero visuale attiva. Questa modalità mostra il codice XAML in cui è stato dichiarato l'elemento, se si ha accesso al codice sorgente dell'applicazione. Selezionare **abilita la selezione** e **anteprima selezione**, e quindi selezionare il pulsante nell'applicazione di test. Il file MainWindow.xaml verrà aperto in Visual Studio e il cursore verrà posizionato sulla riga in cui è definito il pulsante.  
  
## <a name="using-xaml-tools-with-running-applications"></a>Uso di strumenti XAML con applicazioni in esecuzione  
 È possibile usare questi strumenti XAML anche quando non si ha il codice sorgente. Quando si collega a un'applicazione XAML in esecuzione, è possibile usare la **albero elementi visivi attivi** sugli elementi dell'interfaccia utente di tale applicazione troppo. Di seguito è riportato un esempio che usa la stessa applicazione di test WPF usata in precedenza.  
  
1.  Avviare il **TestXaml** applicazione nella configurazione di rilascio. Non è possibile collegare a un processo in esecuzione in un **Debug** configurazione.  
  
2.  Aprire una seconda istanza di Visual Studio e fare clic su **Debug / Connetti a processo**. Trovare **TestXaml.exe** nell'elenco dei processi disponibili, fare clic su **Attach**.  
  
3.  Viene avviata l'esecuzione dell'applicazione.  
  
4.  Nella seconda istanza di Visual Studio, aprire il **albero elementi visivi attivi** (**eseguire il Debug / Windows / albero elementi visivi attivi**). Dovrebbero vedere le **TestXaml** elementi dell'interfaccia utente e si dovrebbe essere possibile modificarli nello durante il debug dell'applicazione direttamente.



