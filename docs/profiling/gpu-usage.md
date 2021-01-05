---
title: Utilizzo GPU | Microsoft Docs
description: Informazioni su come usare lo strumento utilizzo GPU nel profiler delle prestazioni per comprendere meglio l'utilizzo dell'hardware di alto livello dell'app Direct3D.
ms.date: 11/01/2018
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a6b143cc0b3001f0a182de43f1b6eea554025eda
ms.sourcegitcommit: 105e7b5a486262bc92939980383ceee068098a11
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/30/2020
ms.locfileid: "97815652"
---
# <a name="gpu-usage"></a>Utilizzo GPU

Usare lo strumento utilizzo GPU nel profiler delle prestazioni per comprendere meglio l'utilizzo dell'hardware di alto livello dell'app Direct3D. Consente di verificare se le prestazioni dell'app sono basate sulla CPU o con associazione GPU e di ottenere informazioni su come usare l'hardware della piattaforma in modo più efficace. L'utilizzo della GPU supporta le app che usano Direct3D 12, Direct3D 11 e Direct3D 10. Non supporta altre API grafiche, ad esempio Direct2D o OpenGL.

Ecco come appare la finestra **report utilizzo GPU** :

![Screenshot del report sull'utilizzo della GPU, con sequenze temporali CPU e GPU](media/gfx_diag_gpu_usage_report.png "gfx_diag_gpu_usage_report")

## <a name="requirements"></a>Requisiti

Oltre ai requisiti per Diagnostica della grafica, per l'utilizzo dello strumento utilizzo GPU sono necessari gli elementi seguenti:

- Una GPU e un driver che supportino la strumentazione di temporizzazione necessaria.

  > [!NOTE]
  > Per altre informazioni sull'hardware e i driver supportati, vedere [Hardware e driver supportati](#hwsupport) alla fine di questo documento.

Per ulteriori informazioni sui requisiti di Diagnostica della grafica, vedere [Getting Started](../debugger/graphics/getting-started-with-visual-studio-graphics-diagnostics.md).

## <a name="use-the-gpu-usage-tool"></a>Usare lo strumento utilizzo GPU

Quando si esegue l'app nello strumento utilizzo GPU, Visual Studio crea una sessione di diagnostica. Questa sessione illustra in tempo reale le informazioni generali sulle prestazioni di rendering dell'app e sull'utilizzo della GPU.

Per avviare lo strumento Utilizzo GPU:

1. Nel menu principale scegliere **debug**  >  **prestazioni e diagnostica** (oppure, sulla tastiera, premere ALT + F2).

2. Nell'hub **prestazioni e diagnostica** selezionare la casella accanto a **utilizzo GPU**. Facoltativamente, selezionare le caselle accanto agli altri strumenti a cui si è interessati. È possibile eseguire contemporaneamente diversi strumenti di diagnostica e prestazioni per ottenere un quadro più completo delle prestazioni dell'app.

    ![Screenshot del Profiler prestazioni con utilizzo GPU selezionato](media/gpuusageselected.png "Utilizzo GPU selezionato")

   > [!NOTE]
   > Non tutti gli strumenti per le prestazioni e la diagnostica possono essere utilizzati contemporaneamente.

3. Nella parte inferiore dell'hub **prestazioni e diagnostica** selezionare **Avvia** per eseguire l'app negli strumenti selezionati.

Le informazioni di alto livello visualizzate in tempo reale includono intervallo di frame, frequenza dei frame e utilizzo della GPU. Ognuna di queste informazioni viene rappresentata in un grafico in modo indipendente, ma tutti utilizzano una scala temporale comune per poter comprendere facilmente le relazioni.

I grafici **tempo di frame (MS)** e **frame al secondo (fps)** presentano due linee rosse e orizzontali che mostrano gli obiettivi di prestazioni di 60 e 30 fotogrammi al secondo. Nel grafico Durata frame l'app supera la destinazione di prestazioni se il grafico si trova sotto la linea e non raggiunge la destinazione se il grafico si trova sopra la linea. Per il grafico frame al secondo, è il contrario: l'app supera la destinazione di prestazioni quando il grafico si trova sopra la linea e manca la destinazione quando il grafico si trova sotto la linea. Questi grafici vengono usati principalmente per ottenere un'idea generale delle prestazioni dell'app e per identificare i rallentamenti che è opportuno esaminare. Ad esempio, è possibile che venga garantita un'ulteriore analisi se viene visualizzato un calo improvviso della frequenza dei frame o un picco nell'utilizzo della GPU.

Mentre l'app viene eseguita con lo strumento utilizzo GPU, la sessione di diagnostica raccoglie anche informazioni dettagliate sugli eventi di grafica eseguiti nella GPU. Queste informazioni vengono usate per generare un report più granulare sul modo in cui l'app utilizza l'hardware. Poiché la generazione del report a partire dalle informazioni raccolte richiede del tempo, il report è disponibile solo al termine della raccolta delle informazioni nella sessione di diagnostica.

Quando si desidera esaminare più accuratamente un problema relativo a prestazioni o utilizzo, interrompere la raccolta di informazioni sulle prestazioni in modo che sia possibile generare il report.

Per generare e visualizzare il report sull'utilizzo della GPU:

1. Nella parte inferiore della finestra della sessione di diagnostica scegliere il collegamento **Interrompi raccolta** oppure selezionare **Arresta** nell'angolo superiore sinistro.

   ![Screenshot di una finestra della sessione di diagnostica nello strumento utilizzo GPU, che mostra i frame al secondo, l'utilizzo della GPU, il pulsante Interrompi e il collegamento Interrompi raccolta.](media/gfx_diag_gpu_usage_collect.png "gfx_diag_gpu_usage_collect")

2. Nella parte superiore del report selezionare in uno dei grafici una sezione che mostra il problema da analizzare. La selezione può avere una lunghezza di 3 secondi. Le sezioni più lunghe vengono troncate verso l'inizio.

   ![Screenshot di una finestra della sessione di diagnostica nello strumento utilizzo GPU con una parte della sequenza temporale della sessione di diagnostica selezionata.](media/gfx_diag_gpu_usage_select1.png "gfx_diag_gpu_usage_select1")

3. Per visualizzare una sequenza temporale dettagliata della selezione, nella parte inferiore del report, in **... fare clic qui per visualizzare i dettagli dell'utilizzo della GPU per il** messaggio di intervallo, selezionare **Visualizza dettagli**.

   ![Screenshot della finestra della sessione di diagnostica con intervallo selezionato](media/gfx_diag_gpu_usage_select2.png "gfx_diag_gpu_usage_select2")

Si aprirà un nuovo documento a schede contenente il report. Il report utilizzo GPU consente di vedere quando viene avviato un evento di grafica sulla CPU, quando raggiunge la GPU e il tempo impiegato dalla GPU per eseguirlo. Queste informazioni sono utili per identificare i colli di bottiglia e le opportunità di aumentare il parallelismo nel codice.

<!-- VERSIONLESS -->
## <a name="export-to-gpuview-or-windows-performance-analyzer"></a>Esportare in GPUView o Windows Performance Analyzer

A partire da Visual Studio 2017, è possibile aprire i dati con [GPUView](/windows-hardware/drivers/display/using-gpuview) e [Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer). È sufficiente selezionare i collegamenti **Apri in GpuView** o **Apri in WPA** situati nell'angolo inferiore destro della sessione di diagnostica.

![Screenshot della finestra della sessione di diagnostica con i collegamenti evidenziati](media/gfx_diag_open_in.png)
<!-- /VERSIONLESS -->

## <a name="use-the-gpu-usage-report"></a>Usare il report utilizzo GPU

La parte superiore del report sull'utilizzo della GPU Mostra le sequenze temporali per l'attività di elaborazione della CPU, l'attività di rendering della GPU e l'attività di copia della GPU. Queste sequenze temporali sono divise da barre verticali grigio chiaro che indicano la sincronizzazione verticale della visualizzazione (vsync). La frequenza delle barre corrisponde alla frequenza di aggiornamento di uno degli schermi (selezionato usando l'elenco a discesa **Visualizza** ) in cui sono stati raccolti i dati di utilizzo della GPU.

Poiché lo schermo può avere una frequenza di aggiornamento superiore rispetto alla destinazione di prestazioni dell'app, potrebbe non esserci una relazione 1 a 1 tra vsync e frequenza dei frame che l'app deve ottenere. Per soddisfare la destinazione di prestazioni, un'app deve completare l'elaborazione, eseguire il rendering ed effettuare una `Present()` chiamata al framerate di destinazione. Il frame sottoposto a rendering non verrà visualizzato fino al vsync successivo `Present()` , tuttavia.

La parte inferiore del report sull'utilizzo della GPU elenca gli eventi di grafica che si sono verificati durante il periodo di tempo del report. Quando si seleziona un evento, viene visualizzato un marcatore in corrispondenza degli eventi corrispondenti nelle sequenze temporali pertinenti. In genere, un evento in un thread della CPU indica la chiamata API, mentre un altro evento in una delle sequenze temporali della GPU indica il momento in cui la GPU ha completato l'attività. Analogamente, quando si seleziona un evento in una sequenza temporale, il report evidenzia l'evento di grafica corrispondente nella parte inferiore del report.

Quando si esegue lo zoom indietro delle sequenze temporali nella parte superiore del report, sono visibili solo gli eventi che richiedono più tempo. Per visualizzare gli eventi che hanno una durata più breve, ingrandire le sequenze temporali usando Ctrl + rotellina sul dispositivo di puntamento oppure il controllo di ridimensionamento nell'angolo inferiore sinistro del pannello superiore. È anche possibile trascinare il contenuto del pannello della sequenza temporale per spostarsi tra gli eventi registrati.

Per trovare ciò che si sta cercando, filtrare il report sull'utilizzo della GPU in base ai nomi dei processi, agli ID dei thread e al nome dell'evento. È anche possibile scegliere la frequenza di aggiornamento dello schermo che determina le linee di vysnc. Se l'app usa l'interfaccia [ID3DUserDefinedAnnotation](/windows/desktop/api/d3d11_1/nn-d3d11_1-id3duserdefinedannotation) per raggruppare i comandi di rendering, è anche possibile ordinare gli eventi gerarchicamente.

 Di seguito sono riportate informazioni dettagliate:

|Controllo filtro|Descrizione|
|--------------------|-----------------|
|**Processo**|Nome del processo a cui si è interessati. Tutti i processi che hanno utilizzato la GPU durante la sessione di diagnostica sono inclusi in questo elenco a discesa. Il colore associato al processo è il colore dell'attività del thread nelle sequenze temporali.|
|**Thread**|ID del thread a cui si è interessati. In un'app multithread, queste informazioni consentono di isolare thread specifici che appartengono al processo a cui si è interessati. Gli eventi associati al thread selezionato sono evidenziati in ogni sequenza temporale.|
|**Schermo**|Il numero dello schermo di cui viene visualizzata la frequenza di aggiornamento. Alcuni driver possono essere configurati in modo da presentare più schermi fisici come un unico schermo virtuale di grandi dimensioni. È possibile che nell'elenco sia presente un solo schermo, anche se al computer sono collegati più schermi.|
|**Filter**|Parole chiave a cui si è interessati. Gli eventi nella parte inferiore del report includeranno solo quelli che corrispondono a una parola chiave, interamente o parzialmente. È possibile specificare più parole chiave separandole con un punto e virgola (;).|
|**Hierarchy Sort** (Ordinamento gerarchia)|Casella di controllo che indica se le gerarchie degli eventi, definite mediante marcatori utente, vengono mantenute o ignorate.|

L'elenco di eventi nella parte inferiore del report sull'utilizzo della GPU Mostra i dettagli di ogni evento.

|Colonna|Descrizione|
|------------|-----------------|
|**Nome evento**|Nome dell'evento di grafica. Un evento in genere corrisponde a un evento nella sequenza temporale di un thread della CPU e a un evento in una sequenza temporale della GPU. Se l'utilizzo della GPU non è in grado di determinare il nome di un evento, i nomi degli eventi potrebbero non essere *attribuiti* . Per ulteriori informazioni, vedere la nota che segue questa tabella.|
|**Avvio CPU (ns)**|Momento di avvio dell'evento nella CPU a seguito della chiamata a un'API Direct3D. Il tempo viene misurato in nanosecondi in relazione al momento di avvio dell'app.|
|**Avvio GPU (ns)**|Momento di avvio dell'evento nella GPU. Il tempo viene misurato in nanosecondi in relazione al momento di avvio dell'app.|
|**Durata GPU (ns)**|Tempo, in nanosecondi, impiegato per il completamento dell'evento nella GPU.|
|**Nome processo**|Nome dell'app da cui proviene l'evento.|
|**ID thread**|ID del thread da cui proviene l'evento.|

> [!IMPORTANT]
> Se la GPU o il driver non supporta le funzionalità di strumentazione necessarie, tutti gli eventi vengono visualizzati come non *attribuiti*. Se si verifica questo problema, aggiornare il driver della GPU e riprovare. Per ulteriori informazioni, vedere [supporto hardware e driver](#hwsupport) alla fine di questo documento.

## <a name="gpu-usage-settings"></a>Impostazioni di Utilizzo GPU

Si può configurare lo strumento Utilizzo GPU in modo da posticipare la raccolta di informazioni di profilatura, anziché iniziare a raccogliere le informazioni all'avvio dell'app. Le informazioni di profilatura possono essere di grandi dimensioni. È quindi consigliabile procedere con questa azione quando si è certi che i rallentamenti nelle prestazioni dell'app saranno visibili solo successivamente.

Per posticipare la profilatura rispetto all'avvio dell'app:

1. Nel menu principale scegliere **debug**  >  **prestazioni e diagnostica** (oppure, sulla tastiera, premere ALT + F2).

2. Nell'hub **prestazioni e diagnostica** selezionare il collegamento **Impostazioni** accanto a **utilizzo GPU**.

3. Nella pagina delle proprietà **generale** della **configurazione della profilatura GPU** deselezionare la casella di controllo **inizia profilatura all'avvio dell'app** per posticipare la profilatura.

   ![Screenshot delle pagine delle proprietà dell'oggetto, che mostra le opzioni di raccolta](media/gfx_diag_gpu_usage_config.png "gfx_diag_gpu_usage_config")

> [!IMPORTANT]
> Al momento non è possibile posticipare la profilatura per le app Direct3D 12.

Dopo aver eseguito l'app nello strumento Utilizzo GPU, nella parte inferiore della finestra dello strumento diventa disponibile un collegamento aggiuntivo. Per avviare la raccolta di informazioni di profilatura, scegliere il collegamento **Inizia** nel messaggio **Inizia a raccogliere altri dati dettagliati sull'utilizzo della GPU**.

## <a name="hardware-and-driver-support"></a><a name="hwsupport"></a> Hardware e driver supportati

Di seguito è riportato un elenco delle GPU e dei driver supportati:

|Vendor|Descrizione GPU|Versione driver obbligatoria|
|------------|---------------------|-----------------------------|
|Intel®|Processori Intel® Core di quarta generazione (Haswell)<br /><br /> -   Intel® HD Graphics (GT1)<br />-   Intel® HD Graphics 4200 (GT2)<br />-   Intel® HD Graphics 4400 (GT2)<br />-   Intel® HD Graphics 4600 (GT2)<br />-   Intel® HD Graphics P4600 (GT2)<br />-   Intel® HD Graphics P4700 (GT2)<br />-   Intel® HD Graphics 5000 (GT3)<br />-   Intel® Iris™ Graphics 5100 (GT3)<br />-   Intel® Iris™ Pro Graphics 5200 (GT3e)|(usare i driver più recenti)|
|AMD®|La maggior parte dalla serie AMD Radeon™ HD 7000 (esclude AMD Radeon™ HD 7350-7670)<br /><br /> AMD Radeon™ GPU, processori AMD FirePro™ GPU e acceleratori GPU AMD FirePro con architettura GCN (Graphics Core Next)<br /><br /> APU (Accelerated Processing Unit) AMD® E-Series e AMD A-series con architettura Graphics Core Next (GCN) (Kaveri, Kabini, Temash, Beema, Mullins)|14,7 RC3 o versione successiva|
|NVIDIA®|La maggior parte da NVIDIA® GeForce® serie 400<br /><br /> NVIDIA® GeForce® GPU, NVIDIA Quadro® GPU e NVIDIA® Tesla™ acceleratori GPU con l'architettura di fermi™, Keplero™ o Maxwell™|343,37 o versione successiva|

 Al momento non sono supportate le configurazioni con più GPU, ad esempio NVIDIA® SLI™ e AMD CrossFire™. Sono supportate le configurazioni grafiche ibride, ad esempio NVIDIA® Optimus™ e AMD Enduro™.
