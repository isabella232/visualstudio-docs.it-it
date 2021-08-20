---
title: Utilizzo GPU | Microsoft Docs
description: Informazioni su come usare lo strumento Utilizzo GPU nel Profiler prestazioni per comprendere meglio l'utilizzo hardware di alto livello dell'app Direct3D.
ms.date: 11/01/2018
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 567f23ea4997a9497b3ef2160f86b3a46beaf432
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122150391"
---
# <a name="gpu-usage"></a>Utilizzo GPU

Usare lo strumento Utilizzo GPU nel Profiler prestazioni per comprendere meglio l'utilizzo hardware di alto livello dell'app Direct3D. Consente di verificare se le prestazioni dell'app sono associate alla CPU o alla GPU e di ottenere informazioni dettagliate su come usare l'hardware della piattaforma in modo più efficace. Utilizzo GPU supporta le app che usano Direct3D 12, Direct3D 11 e Direct3D 10. Non supporta altre API grafiche, ad esempio Direct2D o OpenGL.

Di seguito è illustrato l'aspetto della finestra Report utilizzo **GPU:**

![Screenshot del report utilizzo GPU, con sequenze temporali CPU e GPU](media/gfx_diag_gpu_usage_report.png "gfx_diag_gpu_usage_report")

## <a name="requirements"></a>Requisiti

Oltre ai requisiti per la Diagnostica della grafica, per l'uso dello strumento Utilizzo GPU è necessario quanto segue:

- Una GPU e un driver che supportino la strumentazione di temporizzazione necessaria.

  > [!NOTE]
  > Per altre informazioni sull'hardware e i driver supportati, vedere [Hardware e driver supportati](#hwsupport) alla fine di questo documento.

Per altre informazioni sui Diagnostica della grafica, vedere [Introduzione.](../debugger/graphics/getting-started-with-visual-studio-graphics-diagnostics.md)

## <a name="use-the-gpu-usage-tool"></a>Usare lo strumento Utilizzo GPU

Quando si esegue l'app con lo strumento Utilizzo GPU, Visual Studio una sessione di diagnostica. Questa sessione mostra informazioni di alto livello sulle prestazioni di rendering dell'app e sull'utilizzo della GPU in tempo reale.

Per avviare lo strumento Utilizzo GPU:

1. Nel menu principale scegliere **Debug** prestazioni e diagnostica  >   oppure premere ALT+F2 sulla tastiera.

2. Nell'hub **Prestazioni e diagnostica** selezionare la casella accanto a Utilizzo **GPU**. Facoltativamente, selezionare le caselle accanto agli altri strumenti a cui si è interessati. È possibile eseguire contemporaneamente diversi strumenti di diagnostica e prestazioni per ottenere un quadro più completo delle prestazioni dell'app.

    ![Screenshot del Profiler prestazioni, con l'opzione Utilizzo GPU selezionata](media/gpuusageselected.png "Utilizzo GPU selezionato")

   > [!NOTE]
   > Non tutti gli strumenti di diagnostica e prestazioni possono essere usati contemporaneamente.

3. Nella parte inferiore dell'hub **Prestazioni e** diagnostica selezionare **Avvia** per eseguire l'app sotto gli strumenti selezionati.

Le informazioni di alto livello visualizzate in tempo reale includono intervallo di fotogrammi, frequenza dei fotogrammi e utilizzo della GPU. Ognuna di queste informazioni viene tracciata in modo indipendente, ma tutte usano una scala temporale comune in modo da poter comprendere facilmente le relazioni.

I grafici Frame **time (ms)** e **Frames per second (FPS)** hanno ognuno due linee orizzontali rosse che mostrano obiettivi di prestazioni di 60 e 30 fotogrammi al secondo. Nel grafico Durata frame l'app supera la destinazione di prestazioni se il grafico si trova sotto la linea e non raggiunge la destinazione se il grafico si trova sopra la linea. Per il grafico Frame al secondo, è l'opposto: l'app supera la destinazione delle prestazioni quando il grafo si trova sopra la linea e non raggiunge la destinazione quando il grafo si trova sotto la linea. Questi grafici vengono utilizzati principalmente per ottenere un'idea generale delle prestazioni dell'app e per identificare i rallentamenti che è possibile analizzare. Ad esempio, un'ulteriore analisi potrebbe essere giustificata se si verifica un improvviso calo della frequenza dei fotogrammi o un picco nell'utilizzo della GPU.

Mentre l'app viene eseguita con lo strumento Utilizzo GPU, la sessione di diagnostica raccoglie anche informazioni dettagliate sugli eventi grafici eseguiti nella GPU. Queste informazioni vengono usate per generare un report più dettagliato sul modo in cui l'app usa l'hardware. Poiché la generazione del report a partire dalle informazioni raccolte richiede del tempo, il report è disponibile solo al termine della raccolta delle informazioni nella sessione di diagnostica.

Quando si vuole esaminare più da vicino un problema di prestazioni o utilizzo, interrompere la raccolta di informazioni sulle prestazioni, in modo da poter generare il report.

Per generare e visualizzare il report utilizzo GPU:

1. Nella parte inferiore della finestra della  sessione di diagnostica scegliere il collegamento Arresta raccolta o selezionare **Arresta** nell'angolo superiore sinistro.

   ![Screenshot di una finestra di sessione di diagnostica nello strumento Utilizzo GPU, che mostra i frame al secondo, l'utilizzo della GPU, il pulsante Arresta e il collegamento Arresta raccolta.](media/gfx_diag_gpu_usage_collect.png "gfx_diag_gpu_usage_collect")

2. Nella parte superiore del report selezionare in uno dei grafici una sezione che mostra il problema da analizzare. La selezione può durare fino a 3 secondi. Le sezioni più lunghe vengono troncate verso l'inizio.

   ![Screenshot di una finestra di sessione di diagnostica nello strumento Utilizzo GPU con parte della sequenza temporale della sessione di diagnostica selezionata.](media/gfx_diag_gpu_usage_select1.png "gfx_diag_gpu_usage_select1")

3. Per visualizzare una sequenza temporale dettagliata della selezione, nella parte inferiore del report, in **... Fare clic qui per visualizzare i dettagli sull'utilizzo della GPU per il** messaggio dell'intervallo, selezionare **Visualizza dettagli**.

   ![Screenshot della finestra della sessione di diagnostica, con l'intervallo selezionato](media/gfx_diag_gpu_usage_select2.png "gfx_diag_gpu_usage_select2")

Si aprirà un nuovo documento a schede contenente il report. Il report Utilizzo GPU consente di vedere quando viene avviato un evento di grafica nella CPU, quando raggiunge la GPU e quanto tempo la GPU richiede per eseguirlo. Queste informazioni sono utili per identificare i colli di bottiglia e le opportunità di aumentare il parallelismo nel codice.

<!-- VERSIONLESS -->
## <a name="export-to-gpuview-or-windows-performance-analyzer"></a>Esportare in GPUView o Windows Performance Analyzer

A partire da Visual Studio 2017, è possibile aprire i dati con [GPUView](/windows-hardware/drivers/display/using-gpuview) e [Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer). È sufficiente selezionare **i collegamenti Apri in GpuView** o Apri in **WPA** nell'angolo inferiore destro della sessione di diagnostica.

![Screenshot della finestra della sessione di diagnostica, con i collegamenti evidenziati](media/gfx_diag_open_in.png)
<!-- /VERSIONLESS -->

## <a name="use-the-gpu-usage-report"></a>Usare il report utilizzo GPU

La parte superiore del report Utilizzo GPU mostra le sequenze temporali per l'attività di elaborazione della CPU, l'attività di rendering GPU e l'attività di copia GPU. Queste sequenze temporali sono divise da barre verticali grigio chiaro che indicano la sincronizzazione verticale dello schermo (vsync). La frequenza delle barre corrisponde alla frequenza di aggiornamento  di uno degli schermi (selezionati usando l'elenco a discesa Visualizza) da cui sono stati raccolti i dati di utilizzo della GPU.

Poiché lo schermo può avere una frequenza di aggiornamento superiore rispetto alla destinazione di prestazioni dell'app, potrebbe non esserci una relazione 1 a 1 tra vsync e frequenza dei frame che l'app deve ottenere. Per soddisfare la destinazione delle prestazioni, un'app deve completare tutte le operazioni di elaborazione, eseguire il rendering ed effettuare una `Present()` chiamata al framerate di destinazione. Il frame di cui è stato eseguito il rendering non verrà visualizzato fino al successivo vsync dopo `Present()` , tuttavia.

Nella parte inferiore del report Utilizzo GPU sono elencati gli eventi grafici che si sono verificati durante il periodo di tempo del report. Quando si seleziona un evento, viene visualizzato un marcatore in corrispondenza degli eventi corrispondenti nelle sequenze temporali pertinenti. In genere, un evento in un thread della CPU indica la chiamata API, mentre un altro evento in una delle sequenze temporali della GPU indica il momento in cui la GPU ha completato l'attività. Analogamente, quando si seleziona un evento in una sequenza temporale, il report evidenzia l'evento grafico corrispondente nella parte inferiore del report.

Quando si esegue lo zoom indietro delle sequenze temporali nella parte superiore del report, sono visibili solo gli eventi che richiedono più tempo. Per visualizzare gli eventi con una durata più breve, ingrandire le sequenze temporali usando CTRL+rotellina sul dispositivo di puntamento o il controllo di ridimensionamento nell'angolo inferiore sinistro del pannello superiore. È anche possibile trascinare il contenuto del pannello della sequenza temporale per spostarsi tra gli eventi registrati.

Per trovare ciò che si sta cercando, filtrare il report Utilizzo GPU in base ai nomi dei processi, agli ID thread e al nome dell'evento. È anche possibile scegliere la frequenza di aggiornamento dello schermo che determina le linee di vysnc. Se l'app usa l'interfaccia [ID3DUserDefinedAnnotation](/windows/desktop/api/d3d11_1/nn-d3d11_1-id3duserdefinedannotation) per raggruppare i comandi di rendering, è anche possibile ordinare gli eventi gerarchicamente.

 Di seguito sono riportate informazioni dettagliate:

|Controllo filtro|Descrizione|
|--------------------|-----------------|
|**Processo**|Nome del processo a cui si è interessati. Tutti i processi che hanno usato la GPU durante la sessione di diagnostica sono inclusi in questo elenco a discesa. Il colore associato al processo è il colore dell'attività del thread nelle sequenze temporali.|
|**Thread**|ID thread a cui si è interessati. In un'app multithread, queste informazioni consentono di isolare thread specifici che appartengono al processo a cui si è interessati. Gli eventi associati al thread selezionato sono evidenziati in ogni sequenza temporale.|
|**Schermo**|Numero della visualizzazione di cui viene visualizzata la frequenza di aggiornamento. Alcuni driver possono essere configurati in modo da presentare più schermi fisici come un unico schermo virtuale di grandi dimensioni. È possibile che nell'elenco sia presente un solo schermo, anche se al computer sono collegati più schermi.|
|**Filter**|Parole chiave a cui si è interessati. Gli eventi nella parte inferiore del report includeranno solo quelli che corrispondono a una parola chiave, interamente o parzialmente. È possibile specificare più parole chiave separandole con un punto e virgola (;).|
|**Hierarchy Sort** (Ordinamento gerarchia)|Casella di controllo che indica se le gerarchie di eventi, definite tramite marcatori utente, vengono mantenute o ignorate.|

L'elenco degli eventi nella parte inferiore del report Utilizzo GPU mostra i dettagli di ogni evento.

|Colonna|Descrizione|
|------------|-----------------|
|**Nome evento**|Nome dell'evento di grafica. Un evento in genere corrisponde a un evento nella sequenza temporale di un thread della CPU e a un evento in una sequenza temporale della GPU. I nomi degli eventi potrebbero *non essere attributi se* l'utilizzo della GPU non è in grado di determinare il nome di un evento. Per altre informazioni, vedere la nota seguente in questa tabella.|
|**Avvio CPU (ns)**|Momento di avvio dell'evento nella CPU a seguito della chiamata a un'API Direct3D. Il tempo viene misurato in nanosecondi in relazione al momento di avvio dell'app.|
|**Avvio GPU (ns)**|Momento di avvio dell'evento nella GPU. Il tempo viene misurato in nanosecondi in relazione al momento di avvio dell'app.|
|**Durata GPU (ns)**|Tempo, in nanosecondi, impiegato per completare l'evento nella GPU.|
|**Nome processo**|Nome dell'app da cui proviene l'evento.|
|**Thread ID**|ID del thread da cui proviene l'evento.|

> [!IMPORTANT]
> Se la GPU o il driver non supporta le funzionalità di strumentazione necessarie, tutti gli eventi verranno visualizzati *come senza attributi.* Se si verifica questo problema, aggiornare il driver GPU e riprovare. Per altre informazioni, vedere [Supporto di hardware e driver](#hwsupport) alla fine di questo documento.

## <a name="gpu-usage-settings"></a>Impostazioni di Utilizzo GPU

Si può configurare lo strumento Utilizzo GPU in modo da posticipare la raccolta di informazioni di profilatura, anziché iniziare a raccogliere le informazioni all'avvio dell'app. Le informazioni di profilatura possono essere di grandi dimensioni. È quindi consigliabile procedere con questa azione quando si è certi che i rallentamenti nelle prestazioni dell'app saranno visibili solo successivamente.

Per posticipare la profilatura rispetto all'avvio dell'app:

1. Nel menu principale scegliere **Debug** Performance and Diagnostics (Prestazioni e diagnostica di  >   debug) oppure premere ALT+F2 sulla tastiera.

2. Nell'hub **Prestazioni e diagnostica** selezionare il collegamento **Impostazioni** accanto a **Utilizzo GPU.**

3. In **Configurazione profilatura GPU** deselezionare la casella di controllo Inizia profilatura all'avvio dell'app nella pagina delle proprietà Generale per posticipare la profilatura.  

   ![Screenshot delle pagine delle proprietà degli oggetti, che mostra le opzioni di raccolta](media/gfx_diag_gpu_usage_config.png "gfx_diag_gpu_usage_config")

> [!IMPORTANT]
> Al momento non è possibile posticipare la profilatura per le app Direct3D 12.

Dopo aver eseguito l'app nello strumento Utilizzo GPU, nella parte inferiore della finestra dello strumento diventa disponibile un collegamento aggiuntivo. Per avviare la raccolta di informazioni di profilatura, scegliere il collegamento **Inizia** nel messaggio **Inizia a raccogliere altri dati dettagliati sull'utilizzo della GPU**.

## <a name="hardware-and-driver-support"></a><a name="hwsupport"></a> Hardware e driver supportati

Di seguito è riportato un elenco delle GPU e dei driver supportati:

|Vendor|Descrizione DELLA GPU|Versione del driver richiesta|
|------------|---------------------|-----------------------------|
|Intel®|Processori Intel® Core di quarta generazione (Haswell)<br /><br /> -   Intel® HD Graphics (GT1)<br />-   Intel® HD Graphics 4200 (GT2)<br />-   Intel® HD Graphics 4400 (GT2)<br />-   Intel® HD Graphics 4600 (GT2)<br />-   Intel® HD Graphics P4600 (GT2)<br />-   Intel® HD Graphics P4700 (GT2)<br />-   Intel® HD Graphics 5000 (GT3)<br />-   Intel® Iris™ Graphics 5100 (GT3)<br />-   Intel® Iris™ Pro Graphics 5200 (GT3e)|(usare i driver più recenti)|
|AMD®|La maggior parte a partire da AMD Radeon™ HD serie 7000 (esclude AMD Radeon™ HD 7350-7670)<br /><br /> Radeon AMD™ GPU, GPU AMD FirePro™ e acceleratori GPU AMD FirePro con architettura Graphics Core Next (GCN)<br /><br /> APU (Accelerated Processing Unit) AMD® E-Series e AMD A-series con architettura Graphics Core Next (GCN) (Kaveri, Kabini, Temash, Beema, Mullins)|14.7 RC3 o versione successiva|
|NVIDIA®|La maggior parte dai tempi di NVIDIA® GeForce® serie 400<br /><br /> GPU NVIDIA® GeForce®, NVIDIA Quadro® GPU e acceleratori GPU NVIDIA® Tesla™ con architettura Avana™, Kepler™ o Maxwell™|343.37 o versione successiva|

 Le configurazioni multi-GPU, ad esempio NVIDIA® SLI™ e AMD Crossfire™, non sono attualmente supportate. Sono supportate configurazioni di grafica ibride, ad esempio NVIDIA® Optimus™ e AMD Enduro™.
