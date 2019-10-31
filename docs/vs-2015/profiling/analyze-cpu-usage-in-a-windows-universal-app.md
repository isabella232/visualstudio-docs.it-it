---
title: Analizzare l'utilizzo della CPU in un'app universale di Windows | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c122b08e-e3bf-43e6-bd6c-e776e178fd9a
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: 8d296c8803127cdbc2e6c72f86dcfba968e2b940
ms.sourcegitcommit: bdccab4c2dbd50ea8adaaf88c69c9ca32db88099
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73144793"
---
# <a name="analyze-cpu-usage-in-a-windows-universal-app"></a>Analizzare l'utilizzo della CPU in un'app universale di Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si applica a Windows e Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Quando è necessario analizzare i problemi relativi alle prestazioni dell'app, è consigliabile partire dall'analisi dell'utilizzo della CPU. Lo strumento **Utilizzo CPU** indica i punti in cui la CPU impiega più tempo per l'esecuzione di codice. Per concentrarsi su scenari specifici, l'utilizzo della CPU può essere eseguito con lo strumento velocità di [risposta interfaccia utente XAML](https://msdn.microsoft.com/library/4ff84cd1-4e63-4fda-b34f-3ef862a6e480) , lo strumento [utilizzo CPU](../profiling/cpu-usage.md) o entrambi gli strumenti in un'unica sessione di diagnostica.  
  
> [!NOTE]
> Lo strumento **Utilizzo CPU** non può essere usato con le app Silverlight per Windows Phone 8.1.  
  
 Questa procedura dettagliata illustra il processo di raccolta e analisi dei dati di utilizzo della CPU per una semplice app XAML universale di Windows.  
  
## <a name="BKMK_Create_the_CpuUseDemo_project"></a> Creare il progetto CpuUseDemo  
 **CpuUseDemo** è un'app creata per illustrare come raccogliere e analizzare i dati di utilizzo della CPU. I pulsanti generano un numero chiamando un metodo che seleziona il valore massimo da più chiamate a una funzione. La funzione chiamata crea un numero molto elevato di valori casuali e restituisce l'ultimo. I dati sono visualizzati in una casella di testo.  
  
1. Creare un nuovo progetto di app universale di Windows C# denominato **CpuUseDemo** usando il modello **BlankApp**.  
  
     ![Creare il CpuUseDemoProject](../profiling/media/cpu-use-newproject.png "CPU_USE_NewProject")  
  
2. Sostituire MainPage.xaml con [questo codice](#BKMK_MainPage_xaml).  
  
3. Sostituire MainPage.xaml.cs con [questo codice](#BKMK_MainPage_xaml_cs).  
  
4. Compilare l'app e provarla. L'app è abbastanza semplice per illustrare alcuni casi comuni di analisi dei dati di utilizzo della CPU.  
  
## <a name="BKMK_Collect_CPU_usage_data"></a> Raccogliere i dati di utilizzo della CPU  
 ![Eseguire una build di rilascio dell'app nel simulatore](../profiling/media/cpu-use-wt-setsimulatorandretail.png "CPU_USE_WT_SetSimulatorAndRetail")  
  
1. In Visual Studio impostare la destinazione della distribuzione su **Simulatore** e la configurazione della soluzione su **Release**.  
  
   - L'esecuzione dell'app nel simulatore ti consente di passare in modo semplice tra l'app e l'IDE di Visual Studio.  
  
   - L'esecuzione dell'app in modalità **Release** offre un punto di vista migliore sulle prestazioni effettive dell'app.  
  
2. Scegliere **Profiler prestazioni** dal menu **Debug**.  
  
3. Nell'hub Prestazioni e diagnostica scegliere **Utilizzo CPU** e quindi **Avvio**.  
  
    ![Avviare la sessione di diagnostica CpuUsage](../profiling/media/cpu-use-wt-perfdiaghub.png "CPU_USE_WT_PerfDiagHub")  
  
4. All'avvio dell'app fare clic su **Get Max Number**. Attendere circa un secondo dopo la visualizzazione dell'app, quindi scegliere **Get Max Number Async**. L'attesa tra i clic sui pulsanti consente di isolare in modo più semplice le routine relative ai clic nel report di diagnostica.  
  
5. Dopo la visualizzazione della seconda riga di output, scegli **Arresta raccolta** nell'hub Prestazioni e diagnostica.  
  
   ![Interrompi raccolta dati CpuUsage](../profiling/media/cpu-use-wt-stopcollection.png "CPU_USE_WT_StopCollection")  
  
   Lo strumento Utilizzo CPU analizza i dati e visualizza il report.  
  
   ![Report CpuUsage](../profiling/media/cpu-use-wt-report.png "CPU_USE_WT_Report")  
  
## <a name="BKMK_Analyze_the_CPU_Usage_report"></a> Analizzare il report di Utilizzo CPU  
  
### <a name="BKMK_CPU_utilization_timeline_graph"></a> Grafico della sequenza temporale dell'utilizzo della CPU  
 ![Grafico &#40;della&#41; sequenza temporale CpuUtilization%](../profiling/media/cpu-use-wt-timelinegraph.png "CPU_USE_WT_TimelineGraph")  
  
 Il grafico dell'utilizzo della CPU mostra l'attività della CPU dell'app sotto forma di percentuale di tutto il tempo CPU per tutti i core del processore nel dispositivo. I dati di questo report sono stati raccolti in una macchina dual core. I due grossi picchi rappresentano l'attività della CPU per i due clic sui pulsanti. `GetMaxNumberButton_Click` viene eseguito in modo sincrono in un singolo core, pertanto è logico che l'altezza del grafico del metodo non superi mai il 50%. `GetMaxNumberAsycButton_Click` viene eseguito in modo asincrono in entrambi i core, pertanto anche in questo caso è logico che il picco relativo si avvicini all'utilizzo di tutte le risorse della CPU in entrambi i core.  
  
#### <a name="BKMK_Select_timeline_segments_to_view_details"></a> Selezionare i segmenti della sequenza temporale per visualizzare i dettagli  
 Usare le barre di selezione nella sequenza temporale **Sessione di diagnostica** per analizzare i dati di GetMaxNumberButton_Click:  
  
 ![GetMaxNumberButton&#95;fare clic su selezionato](../profiling/media/cpu-use-wt-getmaxnumberreport.png "CPU_USE_WT_GetMaxNumberReport")  
  
 La sequenza temporale **Sessione di diagnostica** mostra ora il tempo trascorso nel segmento selezionato (poco più di due secondi in questo report) e filtra l'albero delle chiamate per mostrare solo i metodi eseguiti nella selezione.  
  
 Seleziona ora il segmento `GetMaxNumberAsyncButton_Click`.  
  
 ![GetMaxNumberAsyncButton&#95;fare clic su selezione report](../profiling/media/cpu-use-wt-getmaxnumberasync-selected.png "CPU_USE_WT_GetMaxNumberAsync_Selected")  
  
 Questo metodo viene completato in circa un secondo in meno rispetto a `GetMaxNumberButton_Click`, ma il significato delle voci dell'albero delle chiamate è meno ovvio.  
  
### <a name="BKMK_The_CPU_Usage_call_tree"></a> Albero delle chiamate di Utilizzo CPU  
 Per iniziare a comprendere le informazioni dell'albero delle chiamate, selezionare di nuovo il segmento `GetMaxNumberButton_Click` e analizzare i dettagli dell'albero.  
  
#### <a name="BKMK_Call_tree_structure"></a> Struttura dell'albero delle chiamate  
 ![GetMaxNumberButton&#95;fare clic su albero delle chiamate](../profiling/media/cpu-use-wt-getmaxnumbercalltree-annotated.png "CPU_USE_WT_GetMaxNumberCallTree_annotated")  
  
|||  
|-|-|  
|![Passaggio 1](../profiling/media/procguid-1.png "ProcGuid_1")|Il nodo di livello principale nell'albero delle chiamate di Utilizzo CPU è uno pseudo-nodo|  
|![Passaggio 2](../profiling/media/procguid-2.png "ProcGuid_2")|Nella maggior parte delle app, quando l'opzione **Mostra codice esterno** è disabilitata, il nodo di secondo livello è un nodo **[Codice esterno]** contenente il codice di sistema e di framework che avvia e arresta l'app, disegna l'interfaccia utente, controlla la pianificazione dei thread e fornisce altri servizi di basso livello all'app.|  
|![Passaggio 3](../profiling/media/procguid-3.png "ProcGuid_3")|Gli elementi figlio del nodo di secondo livello sono i metodi del codice utente e le routine asincrone che vengono chiamati o creati dal codice di sistema o di framework di secondo livello.|  
|![Passaggio 4](../profiling/media/procguid-4.png "ProcGuid_4")|I nodi figlio di un metodo contengono i dati solo per le chiamate del metodo padre. Quando l'opzione **Mostra codice esterno** è disabilitata, i metodi dell'app possono contenere anche un nodo **[Codice esterno]** .|  
  
#### <a name="BKMK_External_Code"></a> Codice esterno  
 Il codice esterno è costituito da funzioni nei componenti del sistema e del framework che vengono eseguite dal codice scritto. Include funzioni che avviano e arrestano l'app, disegnano l'interfaccia utente, controllano il threading e forniscono altri servizi di basso livello all'app. Nella maggior parte dei casi il codice esterno è poco interessante, per questo motivo l'albero delle chiamate di Utilizzo CPU raccoglie le funzioni esterne di un metodo utente in un unico nodo **[Codice esterno]** .  
  
 Se vuoi visualizzare i percorsi delle chiamate del codice esterno, scegli **Mostra codice esterno** nell'elenco **Visualizzazione filtro** e quindi scegli **Applica**.  
  
 ![Scegliere Visualizzazione filtro, quindi Mostra codice esterno](../profiling/media/cpu-use-wt-filterview.png "CPU_USE_WT_FilterView")  
  
 Tieni presente che numerose catene di chiamate del codice esterno sono molto annidate, pertanto la larghezza della colonna Nome funzione può superare la larghezza di visualizzazione in quasi tutti i monitor, ad eccezione di quelli più grandi. Quando ciò si verifica, i nomi delle funzioni sono visualizzati come **[…]** :  
  
 ![Codice esterno annidato nell'albero delle chiamate](../profiling/media/cpu-use-wt-showexternalcodetoowide.png "CPU_USE_WT_ShowExternalCodeTooWide")  
  
 Usa la casella di ricerca per trovare il nodo che stai cercando, quindi usa la barra di scorrimento orizzontale per visualizzare i dati:  
  
 ![Cerca codice esterno annidato](../profiling/media/cpu-use-wt-showexternalcodetoowide-found.png "CPU_USE_WT_ShowExternalCodeTooWide_Found")  
  
### <a name="BKMK_Call_tree_data_columns"></a> Colonne di dati dell'albero delle chiamate  
  
|||  
|-|-|  
|**CPU totale (%)**|![Equazione % dati totali](../profiling/media/cpu-use-wt-totalpercentequation.png "CPU_USE_WT_TotalPercentEquation")<br /><br /> Percentuale dell'attività CPU dell'app nell'intervallo di tempo selezionato usata dalle chiamate alla funzione e dalle funzioni chiamate dalla funzione. Osservare che si tratta di un valore diverso da quello del grafico della sequenza temporale di **Utilizzo CPU** , che mette a confronto l'attività totale dell'app in un intervallo di tempo con la capacità CPU disponibile totale.|  
|**CPU auto (%)**|![Equazione % auto](../profiling/media/cpu-use-wt-selflpercentequation.png "CPU_USE_WT_SelflPercentEquation")<br /><br /> Percentuale dell'attività CPU dell'app nell'intervallo di tempo selezionato usata dalle chiamate alla funzione, esclusa l'attività delle funzioni chiamate dalla funzione.|  
|**CPU totale (ms)**|Numero di millisecondi usati nelle chiamate alla funzione nell'intervallo di tempo selezionato e per le funzioni chiamate dalla funzione.|  
|**CPU auto (ms)**|Numero di millisecondi usati nelle chiamate alla funzione nell'intervallo di tempo selezionato e per le funzioni chiamate dalla funzione.|  
|**Modulo**|Nome del modulo contenente la funzione o numero dei moduli contenenti le funzioni in un nodo [Codice esterno].|  
  
### <a name="BKMK_Asynchronous_functions_in_the_CPU_Usage_call_tree"></a> Funzioni asincrone nell'albero delle chiamate di Utilizzo CPU  
 Quando il compilatore rileva un metodo asincrono, crea una classe nascosta per controllare l'esecuzione del metodo. Concettualmente, la classe è una macchina a stati che include un elenco di funzioni generate dal compilatore che chiamano le operazioni del metodo originale in modo asincrono, nonché i callback, l'utilità di pianificazione e gli iteratori necessari. Quando il metodo originale viene chiamato da un metodo padre, il runtime rimuove il metodo dal contesto di esecuzione del padre ed esegue i metodi della classe nascosta nel contesto del codice di sistema e di framework che controllano l'esecuzione dell'app. Spesso, ma non sempre, i metodi asincroni vengono eseguiti in uno o più thread diversi. Il codice è illustrato nell'albero delle chiamate di Utilizzo CPU come figlio del nodo **[Codice esterno]** immediatamente sotto il nodo principale dell'albero.  
  
 Per vedere questo aspetto nel nostro esempio, seleziona di nuovo il segmento `GetMaxNumberAsyncButton_Click` nella sequenza temporale.  
  
 ![GetMaxNumberAsyncButton&#95;fare clic su selezione report](../profiling/media/cpu-use-wt-getmaxnumberasync-selected.png "CPU_USE_WT_GetMaxNumberAsync_Selected")  
  
 I primi due nodi sotto **[Codice esterno]** sono i metodi generati dal compilatore della classe macchina a stati. Il terzo è la chiamata al metodo originale. Espandendo i metodi generati puoi vedere ciò che succede.  
  
 ![Espanso GetMaxNumberAsyncButton&#95;clic su albero delle chiamate](../profiling/media/cpu-use-wt-getmaxnumberasync-expandedcalltree.png "CPU_USE_WT_GetMaxNumberAsync_ExpandedCallTree")  
  
- `MainPage::GetMaxNumberAsyncButton_Click` fa molto poco: gestisce un elenco dei valori delle attività, calcola il massimo dei risultati e mostra l'output.  
  
- `MainPage+<GetMaxNumberAsyncButton_Click>d__3::MoveNext` mostra l'attività necessaria per pianificare e avviare le 48 attività che eseguono il wrapping della chiamata a `GetNumberAsync`.  
  
- `MainPage::<GetNumberAsync>b__b` mostra le operazioni eseguite dalle attività che chiamano `GetNumber`.  
  
## <a name="BKMK_Next_steps"></a> Passaggi successivi  
 L'app CpuUseDemo non è la più brillante delle app, ma puoi estenderne l'utilità usandola per provare l'operazione asincrona e altri strumenti nell'hub Prestazioni e diagnostica.  
  
- Osserva che `MainPage::<GetNumberAsync>b__b` usa più tempo in [Codice esterno] rispetto a quello usato per l'esecuzione del metodo GetNumber. Gran parte di questo tempo è correlato al sovraccarico delle operazioni asincrone. Prova ad aumentare il numero di attività (impostato nella costante `NUM_TASKS` di MainPage.xaml.cs) e a ridurre il numero di iterazioni in `GetNumber` (modifica il valore di `MIN_ITERATIONS`). Esegui lo scenario di raccolta e confronta l'attività della CPU di `MainPage::<GetNumberAsync>b__b` con quella della sessione di diagnostica originale di Utilizzo CPU. Prova a ridurre le attività e ad aumentare le iterazioni.  
  
- Gli utenti spesso non danno importanza alle reali prestazioni della tua app, bensì alle prestazioni percepite e alla velocità di risposta dell'app. Lo strumento Velocità di risposta interfaccia utente XAML mostra i dettagli dell'attività nel thread UI che influiscono sulla velocità di risposta percepita.  
  
     Crea una nuova sessione nell'hub Prestazioni e diagnostica e aggiungi sia lo strumento Velocità di risposta interfaccia utente XAML sia lo strumento Utilizzo CPU. Esegui lo scenario di raccolta. Probabilmente il report non conterrà informazioni non note, ma sarà possibile osservare le notevoli differenze nel grafico della sequenza temporale di **Utilizzo thread UI** per i due metodi. Con le app complesse reali, la combinazione di strumenti può essere molto utile.  
  
## <a name="BKMK_MainPage_xaml"></a> MainPage.xaml  
  
```csharp  
<Page  
    x:Class="CpuUseDemo.MainPage"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:local="using:CpuUseDemo"  
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
    mc:Ignorable="d">  
  
    <Page.Resources>  
        <Style TargetType="TextBox">  
            <Setter Property="FontFamily"  Value="Lucida Console" />  
        </Style>  
    </Page.Resources>  
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">  
        <Grid.RowDefinitions>  
            <RowDefinition Height="Auto" />  
            <RowDefinition Height="*" />  
        </Grid.RowDefinitions>  
        <StackPanel Grid.Row="0" Orientation="Horizontal"  Margin="0,40,0,0">  
            <Button Name="GetMaxNumberButton" Click="GetMaxNumberButton_Click"  Content="Get Max Number" />  
            <Button Name="GetMaxNumberAsyncButton" Click="GetMaxNumberAsyncButton_Click"  Content="Get Max Number Async" />  
        </StackPanel>  
        <StackPanel Grid.Row="1">  
            <TextBox Name="TextBox1" AcceptsReturn="True" />  
        </StackPanel>  
    </Grid>  
  
</Page>  
  
```  
  
## <a name="BKMK_MainPage_xaml_cs"></a> MainPage.xaml.cs  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.IO;  
using System.Linq;  
using System.Runtime.InteropServices.WindowsRuntime;  
using Windows.Foundation;  
using Windows.Foundation.Collections;  
using Windows.UI.Xaml;  
using Windows.UI.Xaml.Controls;  
using Windows.UI.Xaml.Controls.Primitives;  
using Windows.UI.Xaml.Data;  
using Windows.UI.Xaml.Input;  
using Windows.UI.Xaml.Media;  
using Windows.UI.Xaml.Navigation;  
using Windows.Foundation.Diagnostics;  
using System.Threading;  
using System.Threading.Tasks;  
using System.Collections.Concurrent;  
  
// The Blank Page item template is documented at http://go.microsoft.com/fwlink/?LinkId=234238  
  
namespace CpuUseDemo  
{  
    /// <summary>  
    /// An empty page that can be used on its own or navigated to within a Frame.  
    /// </summary>  
    public sealed partial class MainPage : Page  
    {  
        public MainPage()  
        {  
            this.InitializeComponent();  
        }  
  
        const int NUM_TASKS = 48;  
        const int MIN_ITERATIONS = int.MaxValue / 1000;  
        const int MAX_ITERATIONS = MIN_ITERATIONS + 10000;  
  
        long m_totalIterations = 0;  
        readonly object m_totalItersLock = new object();  
  
        private void GetMaxNumberButton_Click(object sender, RoutedEventArgs e)  
        {  
            GetMaxNumberAsyncButton.IsEnabled = false;  
            lock (m_totalItersLock)  
            {  
                m_totalIterations = 0;  
            }  
            List<int> tasks = new List<int>();  
            for (var i = 0; i < NUM_TASKS; i++)  
            {  
                var result = 0;  
                result = GetNumber();  
                tasks.Add(result);  
            }  
            var max = tasks.Max();  
            var s = GetOutputString("GetMaxNumberButton_Click", NUM_TASKS, max, m_totalIterations);  
            TextBox1.Text += s;  
            GetMaxNumberAsyncButton.IsEnabled = true;  
        }  
  
        private async void GetMaxNumberAsyncButton_Click(object sender, RoutedEventArgs e)  
        {  
            GetMaxNumberButton.IsEnabled = false;  
            GetMaxNumberAsyncButton.IsEnabled = false;  
            lock (m_totalItersLock)  
            {  
                m_totalIterations = 0;  
            }  
            var tasks = new ConcurrentBag<Task<int>>();  
            for (var i = 0; i < NUM_TASKS; i++)  
            {  
                tasks.Add(GetNumberAsync());  
            }  
            await Task.WhenAll(tasks.ToArray());  
            var max = 0;  
            foreach (var task in tasks)  
            {  
                max = Math.Max(max, task.Result);  
            }  
            var func = "GetMaxNumberAsyncButton_Click";  
            var outputText = GetOutputString(func, NUM_TASKS, max, m_totalIterations);  
            TextBox1.Text += outputText;  
            this.GetMaxNumberButton.IsEnabled = true;  
            GetMaxNumberAsyncButton.IsEnabled = true;  
        }  
  
        private int GetNumber()  
        {  
            var rand = new Random();  
            var iters = rand.Next(MIN_ITERATIONS, MAX_ITERATIONS);  
            var result = 0;  
            lock (m_totalItersLock)  
            {  
                m_totalIterations += iters;  
            }  
            // we're just spinning here  
            // and using Random to frustrate compiler optimizations  
            for (var i = 0; i < iters; i++)  
            {  
                result = rand.Next();  
            }  
            return result;  
        }  
  
        private Task<int> GetNumberAsync()  
        {  
            return Task<int>.Run(() =>  
            {  
                return GetNumber();  
            });  
        }  
  
        string GetOutputString(string func, int cycles, int max, long totalIters)  
        {  
            var fmt = "{0,-35}Tasks:{1,3}    Maximum:{2, 12}    Iterations:{3,12}\n";  
            return String.Format(fmt, func, cycles, max, totalIters);  
        }  
  
    }  
}  
  
```
