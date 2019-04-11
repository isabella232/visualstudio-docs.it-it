---
title: Supporto per il riconoscimento di Monitor per estensioni di Visual Studio
titleSuffix: ''
description: Scopri il nuovo supporto di extender per ogni monitoraggio-riconoscimento disponibile in Visual Studio 2019.
ms.date: 04/09/2019
helpviewer_keywords:
- Visual Studio, PMA, per-monitor-awareness, extenders, Windows Forms
- Per-Monitor Awareness support for extenders
ms.assetid: ''
author: rub8n
ms.author: rurios
manager: anthc
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: reference
ms.workload:
- multiple
ms.openlocfilehash: 42de73a29e053066c0fbeca72ca3511b58b2fa7e
ms.sourcegitcommit: 0a2fdc23faee77187e10a1c19665ba5a1ac68e72
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/10/2019
ms.locfileid: "59477695"
---
# <a name="per-monitor-awareness-support-for-visual-studio-extenders"></a>Supporto per il riconoscimento di Monitor per estensioni di Visual Studio

Versioni precedenti a Visual Studio 2019 era relativo contesto di riconoscimento DPI impostato su compatibile con system, anziché a una compatibile con monitor DPI (PMA). In esecuzione nel sistema di riconoscimento ha generato in un'esperienza visiva con funzionalità ridotta (tipi di carattere, ad esempio sfocati o le icone) ogni volta che Visual Studio era necessario eseguire il rendering su monitor con fattori di scala diversa o accedere in remoto dei computer con configurazioni di visualizzazione diverse (ad esempio diverse Windows scalabilità).

Il contesto di riconoscimento DPI di Visual Studio 2019 è set come compatibile con, consentendo di Visual Studio per eseguire il rendering in base alla configurazione dello schermo in cui è ospitato monitor piuttosto che una configurazione generica definito dal sistema. In definitiva, traducendo in un'interfaccia utente precisi per superfici che implementano il supporto PMA.

Vedere la [sviluppo di applicazioni Desktop DPI elevato in Windows](https://docs.microsoft.com/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) per altre informazioni sulle condizioni e lo scenario lo trattate in questo documento.

## <a name="quickstart"></a>Guida rapida
- Verificare che Visual Studio è in esecuzione in modalità PMA (vedere **abilitazione PMA**)

- Convalidare il funzionamento di estensione correttamente in un set di scenari comuni (vedere **test di estensioni per i problemi PMA**)

- Se si rilevano problemi, si sarà necessario aggiungere il nuovo pacchetto nugget PMA, diagnosticare e risolvere i problemi usando le strategie e consigli descritti in questo documento

## <a name="enabling-pma"></a>Abilitazione PMA
Per abilitare PMA in Visual Studio, è necessario soddisfare i requisiti seguenti:
1)  Windows 10 April 2018 Update (v1803, RS4) o versione successiva
2)  Versione RTM di .NET framework 4.8 o versione successiva (attualmente è disponibile come anteprima autonomo o bundle con recenti Windows build Insider)
3)  Visual Studio 2019 con il ["Ottimizzare il rendering per le schermate con densità di pixel diversa"](https://docs.microsoft.com/visualstudio/ide/reference/general-environment-options-dialog-box?view=vs-2019) opzione abilitata

Una volta soddisfatti questi requisiti, Visual Studio verrà abilitata automaticamente PMA nell'intero processo.

## <a name="testing-your-extensions-for-pma-issues"></a>Le estensioni per i problemi PMA di test

Visual Studio supporta ufficialmente di framework WPF, Windows Forms, Win32 e dell'interfaccia utente HTML/JS. Se Visual Studio viene inserita la modalità PMA, si comportano in modo diverso gli stack di interfaccia utente diversi. Pertanto, indipendentemente dal framework dell'interfaccia utente, è consigliabile che passi del test viene eseguita per garantire che sia conforme a PMA tutti dell'interfaccia utente.

Indipendentemente dal framework dell'interfaccia utente supportate dall'estensione, è consigliabile convalidare gli scenari comuni seguenti:

1. Modifica il fattore di scala di un ambiente solo monitor, mentre l'applicazione è in esecuzione *
    - Questo scenario consente di verificare che risponda dell'interfaccia utente per la modifica del valore DPI Windows dinamica

2. Docking/il disinserimento un computer portatile in cui un monitoraggio collegato è impostato per il database primario e il monitoraggio collegato è un fattore di scala diversa rispetto al database primario mentre è in esecuzione l'applicazione.
    - Questo scenario consente di verificare che risponda dell'interfaccia utente alla visualizzazione della modifica del valore DPI, nonché la gestione consente di visualizzare in modo dinamico l'aggiunta o la rimozione

3. La presenza di più monitor grazie a fattori di scala diversa e lo spostamento dell'applicazione tra di essi.
    - Questo scenario consente di verificare che risponda alla modifica del valore DPI di visualizzazione dell'interfaccia utente
    
4. .NET Remoting in un computer quando il computer locale e remoto dispone di fattori di scala diversa per il monitoraggio principale.
    - Questo scenario consente di verificare che risponda dell'interfaccia utente per la modifica del valore DPI Windows dinamica

Un buon test preliminare per se dell'interfaccia utente potrebbe avere problemi è o meno il codice usa uno di *Microsoft.VisualStudio.Utilities.Dpi.DpiHelper* o *Microsoft.VisualStudio.PlatformUI.DpiHelper* classi. Queste classi DpiHelper precedenti supportano solo ai valori DPI del sistema e non sempre funziona correttamente quando il processo è PMA.

Uso tipico di questi DpiHelpers avrà un aspetto simile:

```cs
Point screenTopRight = logicalBounds.TopRight.LogicalToDeviceUnits();

POINT screenIntTopRight = new POINT
{
    x = (int)screenTopRIght.X,
    y = (int)screenTopRIght.Y
}

IntPtr monitor = NativeMethods.MonitorFromPoint(screenIntTopRight, NativeMethods.Monitor_DEFAULTTONEARST);
```

Nell'esempio precedente, un rettangolo che rappresenta i limiti logici di una finestra viene convertito in unità di dispositivo in modo che può essere passato al metodo nativo MonitorFromPoint che si aspetta di coordinate del dispositivo per poter restituendo un puntatore di monitoraggio accurate.

### <a name="classes-of-issues"></a>Classi di problemi

Quando PMA è abilitata per Visual Studio, l'interfaccia utente è stato possibile replicare i problemi in vari modi più comuni. La maggior parte, se non tutti, questi problemi possono verificarsi in uno dei framework dell'interfaccia utente supportate di Visual Studio. Inoltre, questi problemi possono verificarsi anche quando una parte dell'interfaccia utente è ospitata in modalità mista DPI scenari di ridimensionamento (il Windows si intende [documentazione](https://docs.microsoft.com/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) per altre informazioni). 

#### <a name="win32-window-creation"></a>Creazione della finestra Win32
Durante la creazione di windows con CreateWindow() o CreateWindowEx(), un modello comune è creare la finestra in corrispondenza delle coordinate 0,0 (l'angolo superiore sinistro dello schermo principale), quindi spostarlo sulla propria posizione finale. Tuttavia, tale operazione può causare la finestra attivare un valore DPI modificato messaggio o un evento, che quindi possibile riattivare altri eventi o messaggi dell'interfaccia utente e alla fine causare comportamenti indesiderati o per il rendering.

#### <a name="wpf-element-placement"></a>Posizionamento degli elementi WPF
Quando lo spostamento di elementi WPF utilizzando il vecchio Microsoft.VisualStudio.Utilities.Dpi.DpiHelper, angolo superiore sinistro le coordinate potrebbero non essere calcolate correttamente ogni volta che gli elementi sono presenti il caso di valori DPI non primario.

#### <a name="serialization-of-ui-element-sizes-or-positions"></a>Serializzazione delle dimensioni degli elementi dell'interfaccia utente o le posizioni
Ogni volta che le dimensioni dell'interfaccia utente o la posizione viene ripristinato in un contesto DPI diverso rispetto a ciò che si trovava al, verrà posizionato e ridimensionato in modo non corretto. Ciò accade perché i limiti logici di una finestra vengono convertiti in unità di dispositivo in modo che può essere passato al metodo Win32 MonitorFromPoint che si aspetta di coordinate del dispositivo per poter restituendo un puntatore di monitoraggio accurate.

#### <a name="incorrect-scaling"></a>Ridimensionamento non corretto
Elementi dell'interfaccia utente creati nel valore DPI primario verranno ridimensionati in modo corretto, tuttavia quando si sposta in una visualizzazione con un valore DPI diverso, non modificare la scala e il relativo contenuto in questo modo, finisce per essere troppo grande o troppo piccolo.

#### <a name="incorrect-bounding"></a>Rettangolo di selezione non corretto
Analogamente, il problema della scalabilità, elementi dell'interfaccia utente consente di calcolare i limiti in modo corretto sul quel contesto DPI primario, tuttavia quando spostato in un valore DPI non primari, essi non calcolare i nuovi limiti correttamente. Di conseguenza, la finestra del contenuto finisce per avere sia troppo piccolo o troppo grande rispetto all'interfaccia utente di hosting, con conseguente ritaglio o uno spazio vuoto.

#### <a name="drag--drop"></a>Trascinamento della selezione
Ogni volta che all'interno di scenari DPI in modalità mista (ad esempio, diversi elementi dell'interfaccia utente per il rendering nel contesto DPI primario e non primari), trascinare e rilasciare le coordinate potrebbero modo errate, causando la destinazione finale posizione finisce non corretto.

#### <a name="out-of-process-ui"></a>Interfaccia utente di out-of-process
Parte dell'interfaccia utente viene creato out-of-process e se il processo esterno creazione in una modalità di compatibilità DPI diversi rispetto a Visual Studio, questo può causare i problemi di rendering precedente.

#### <a name="windows-forms-controls-images-or-windows-not-displaying"></a>Windows non vengono visualizzati, immagini o controlli Windows Form
Una delle cause principali per risolvere questo problema è il tentativo di assegnare un nuovo elemento di un controllo o finestra con una DpiAwarenessContext a un'altra finestra DpiAwarenessContext gli sviluppatori. 

Le figure seguenti illustrano le restrizioni di sistema operativo di Windows corrente nel padre di windows, a meno che non viene modificata in modo esplicito i thread che ospita il comportamento:

![Screenshot del comportamento corretto genitorialità](../../extensibility/ux-guidelines/media/PMA-parenting-behavior.PNG)

Di conseguenza, se si imposta la relazione padre-figlio tra le modalità non supportate, viene restituito un errore e il controllo o la finestra non vengono visualizzata come previsto.

### <a name="diagnosing-issues"></a>Diagnosi dei problemi
Esistono molti fattori da considerare quando si identificano i problemi di PMA: 

1. L'interfaccia utente o di API previsto logico o valori di dispositivo.
    - UI di WPF e le API in genere usano valori logici (ma non sempre)
    - Interfaccia utente di Win32 e le API in genere utilizzano i valori di dispositivo

2. I valori di provenienza?
    - Se riceve i valori da altre API o l'interfaccia utente, è il passaggio di dispositivo o valori logici.
    - Se la ricezione di valori da più origini, tutti usare/prevede gli stessi tipi di valori o le conversioni necessarie essere combinati e associati?

3. Sono costanti dell'interfaccia utente in uso e il formato si trovano?

4. È il thread nel contesto di DPI corretto per i valori vengono ricevuti?
    - Le modifiche per abilitare CLMM in genere opportuno inserire i percorsi del codice nel contesto corretto, tuttavia, lavorare all'esterno del flusso di messaggi principale ciclo o l'evento potrebbe eseguire nel contesto errato DPI.

5. I valori superano i limiti del contesto DPI?
    - Operazione di trascinamento è una situazione comune in cui coordinate possono superare i contesti DPI. Finestra tenta di fare la cosa giusta, ma in alcuni casi, l'host dell'interfaccia utente potrebbe essere necessario eseguire operazioni di conversione per assicurarsi che i limiti del contesto corrispondente.

### <a name="pma-nugget-package"></a>Pacchetto NuGet PMA
Le nuove librerie DpiAwarness sono reperibile nel pacchetto Microsoft.VisualStudio.DpiAwareness NuGet.

### <a name="recommended-tools"></a>Strumenti consigliati
Gli strumenti seguenti consentono di eseguire il debug di problemi correlati alla PMA in alcuni degli stack dei diversi dell'interfaccia utente supportato da Visual Studio.

#### <a name="snoop"></a>Fare ricerche
Fare ricerche è uno strumento di debug di XAML con alcune funzionalità aggiuntive che non ha gli strumenti XAML di Visual Studio integrati. Inoltre, fare ricerche non deve eseguire attivamente il debug di Visual Studio per essere in grado di visualizzare e modificare la UI WPF. I due modi principali fare ricerche può risultare utile per la diagnosi dei problemi PMA è per la convalida delle coordinate di posizionamento logico o limiti di dimensioni e per la convalida dell'interfaccia utente ha il valore DPI a destra.
 
#### <a name="visual-studio-xaml-tools"></a>Strumenti di Visual Studio XAML
Come fare ricerche, gli strumenti XAML in Visual Studio consente di diagnosticare problemi PMA. Dopo aver trovato una probabile causa del problema, è possibile impostare punti di interruzione e usare la finestra struttura ad albero visuale in tempo reale, nonché le finestre di debug, per controllare i limiti dell'interfaccia utente e DPI corrente.

## <a name="strategies-for-fixing-pma-issues"></a>Strategie per la risoluzione dei problemi di PMA

### <a name="replacing-dpihelper-calls"></a>La sostituzione di chiamate DpiHelper
Nella maggior parte dei casi, risoluzione dei problemi dell'interfaccia utente in PMA riduce alla sostituzione di chiamate nel codice gestito al precedente: *Microsoft.VisualStudio.Utilities.Dpi.DpiHelper* e *Microsoft.VisualStudio.PlatformUI.DpiHelper* classi, con le chiamate al nuovo *Microsoft.VisualStudio.Utilities.DpiAwareness* classe helper. 

Per il codice nativo, esso comporterà sostituendo le chiamate per il vecchio *VsUI::CDpiHelper* con le chiamate alla nuova classe *VsUI::CDpiAwareness* classe. Le nuove classi DpiAwareness e CDpiAwareness offrono gli helper di conversione stessa come le classi DpiHelper ma che non richiedono un parametro di input aggiuntivo: l'elemento dell'interfaccia utente da utilizzare come riferimento per l'operazione di conversione. 

La classe DpiAwareness gestita offre gli helper per gli oggetti visivi WPF, controlli Windows Form e Win32 HWND e HMONITORs (entrambi in formato IntPtrs), mentre il CDpiAwareness classe offerte HWND e HMONITOR helper nativi.

### <a name="windows-forms-dialogs-windows-or-controls-displayed-in-the-wrong-dpiawarenesscontext"></a>Finestre di dialogo Windows Form, windows o i controlli visualizzati nella finestra di DpiAwarenessContext errato
Anche dopo un elemento padre ha esito positivo di windows con diversi DpiAwarenessContext (a causa di comportamento predefinito di windows), gli utenti possono comunque visualizzare ridimensionamento problemi come finestre diverse DpiAwarenessContext ridimensionare in modo diverso. Di conseguenza, gli utenti possono vedere sfocati/allineamento testo o immagine problemi nell'interfaccia utente.

La soluzione consiste nell'impostare l'ambito DpiAwarenessContext corretto per tutte le finestre e i controlli nell'applicazione.

### <a name="tlmm-dialogs"></a>Finestre di dialogo TLMM
Durante la creazione di finestre di primo livello, ad esempio le finestre di dialogo modale, è importante per assicurarsi che il thread è nello stato appropriato prima di HWND da creare. I thread possono essere inserite nella consapevolezza di sistema da utilizzando l'helper CDpiScope nativo o gestito l'helper DpiAwareness.EnterDpiScope in. (TLMM deve in genere usato in finestre di dialogo non WPF e windows.)

### <a name="child-level-mixed-mode-clmm"></a>Livello figlio in modalità mista (CLMM)

Per impostazione predefinita, le finestre figlio ricevono la stessa modalità di compatibilità con DPI di padri. Tuttavia, è possibile usare SetThreadDpiHostingBehavior per eseguirne l'override e hanno finestre figlio eseguito in modalità di scalabilità diversi rispetto a loro padre o host.


#### <a name="clmm-issues"></a>Problemi CLMM
Maggior parte delle operazioni di calcolo dell'interfaccia utente che viene eseguita come parte della messaggistica principale catena di ciclo o un evento deve essere già in esecuzione nel giusto contesto DPI. Tuttavia, se coordinate o dimensioni calcoli vengono eseguiti all'esterno di questi flussi di lavoro principale (ad esempio durante un'attività di tempo di inattività o disattivare il thread dell'interfaccia utente, il contesto corrente DPI potrebbe essere errato causando misplacement dell'interfaccia utente o di ridimensionamento erroneamente problemi. Inserire il thread in stato corretto per l'interfaccia utente di lavoro a livello generale corregge il problema.
 
#### <a name="opting-out-of-clmm"></a>Rifiuto esplicito CLMM
Se viene eseguita la migrazione di una finestra degli strumenti non WPF per supportare pienamente PMA, è necessario rifiutare esplicitamente CLMM. A tale scopo, deve essere implementata una nuova interfaccia: IVsDpiAware.

C#:
```cs
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown)]
public interface IVsDpiAeware
{
    [ComAliasName("Microsoft.VisualStudio.Shell.Interop.VSDPIMode")]
    uint Mode {get;}
}
```
 
C++:
```cplusplus
IVsDpiAware : public IUnknown
{
    public:
        HRRESULT STDMETHODCALLTYPE get_Mode(__RCP__out VSDPIMODE *dwMode);
};
```
 

Per i linguaggi gestiti, il modo migliore per implementare questa interfaccia è nella stessa classe che deriva da *Microsoft.VisualStudio.Shell.ToolWindowPane*. Per C++, il modo migliore per implementare questa interfaccia è nella stessa classe che implementa *IVsWindowPane* da vsshell.h.

Il valore restituito dalla proprietà modalità sull'interfaccia è un __VSDPIMODE (e cast a un uint in gestito):

```cs
enum __VSDPIMODE
    {
        VSDM_Unaware    = 0x01,
        VSDM_System     = 0x02,
        VSDM_PerMonitor = 0x03,
    }
```

- Significa che la finestra degli strumenti deve gestire 96 DPI, gestirà Windows ridimensionarlo per tutte le altre DPI. Risultante sul contenuto viene leggermente sfocato.
- Indica di sistema che della finestra degli strumenti deve gestire il valore DPI per il database primario la visualizzazione di valori DPI. Qualsiasi visualizzazione con un valore DPI corrisponda avrà un aspetto precisi, ma se il valore DPI diverso o cambiano durante la sessione, Windows consente di gestire il ridimensionamento e sarà leggermente sfocato.
- PerMonitor significa che la finestra degli strumenti deve gestire tutti i DPI su tutti gli schermi e ogni volta che viene modificato il valore DPI.

**NOTA**: Visual Studio supporta solo PerMonitorV2 consapevolezza, in modo che il valore di enumerazione PerMonitor converte il valore di Windows di DPI_AWARENESS_CONTEXT_PER_MONITOR_AWARE_V2.

## <a name="known-issues"></a>Problemi noti

### <a name="windows-forms"></a>Windows Form

Per ottimizzare i nuovi scenari in modalità mista, Windows Form modificato come la creazione di controlli e windows ogni volta che l'elemento padre non è stato impostato in modo esplicito. In precedenza, i controlli senza un/padre espliciti usati un interno "parcheggio finestra" come elemento padre temporaneo per il controllo o la finestra viene creato. 

La "finestra di parcheggio" Ottiene relativo DpiAwarenessContext dal processo che in cui viene eseguita l'applicazione. Il controllo eredita le stesse DpiAwarenessContext come finestra di parcheggio e sarebbe quindi possibile associare di nuovo all'elemento padre originale/previsto dallo sviluppatore dell'applicazione.  Questo non funziona quando il padre desiderato per il controllo non è il DpiAwarenessContext stesso come il controllo da creare.

A partire da .NET 4.8, se l'elemento padre non è impostata in modo esplicito nel controllo o finestra Windows Form verrà eseguire una query per una finestra di parcheggio corrispondente DpiAwarenessContext del thread in cui viene richiesta la creazione di controllo o finestra e utilizzarlo come un elemento padre temporaneo. In altre parole, al momento della creazione il controllo viene ora creato con il DpiAwarenessContext desiderata. Il controllo o finestra verrà quindi ricollegata al padre previsto dallo sviluppatore dell'applicazione.
