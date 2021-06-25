---
title: Per-Monitor di consapevolezza per Visual Studio estenditori
titleSuffix: ''
description: Informazioni sul nuovo supporto dell'estensione per la sensibilità per monitor disponibile in Visual Studio 2019.
ms.date: 04/10/2019
helpviewer_keywords:
- Visual Studio, PMA, per-monitor-awareness, extenders, Windows Forms
- Per-Monitor Awareness support for extenders
author: rub8n
ms.author: rurios
manager: anthc
monikerRange: vs-2019
ms.topic: reference
dev_langs:
- CSharp
- CPP
ms.openlocfilehash: 90ec038e8f27407ba08633bacbb5576bee2a7883
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902046"
---
# <a name="per-monitor-awareness-support-for-visual-studio-extenders"></a>Per-Monitor di consapevolezza per Visual Studio estenditori

Nelle versioni precedenti Visual Studio 2019 il contesto di consapevolezza DPI era impostato in modo da riconoscere il sistema, anziché essere in grado di riconoscere DPI per monitor. L'esecuzione con riconoscimento del sistema ha comportato un'esperienza visiva ridotta (ad esempio, tipi di carattere o icone sfocati) ogni volta che il Visual Studio doveva eseguire il rendering su monitor con fattori di scala diversi o in computer remoti con configurazioni dello schermo diverse (ad esempio, il ridimensionamento di Windows diverso).

Il contesto di riconoscimento DPI di Visual Studio 2019 è impostato come PMA, quando l'ambiente lo supporta, consentendo a Visual Studio di eseguire il rendering in base alla configurazione dello schermo in cui è ospitato anziché a una singola configurazione definita dal sistema. In definitiva, la traduzione in un'interfaccia utente sempre nitida per le aree di superficie che supportano la modalità PMA.

Per altre informazioni sui termini e sullo scenario generale trattati in questo documento, vedere la documentazione high [DPI Desktop Application Development on Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) (Sviluppo di applicazioni desktop con valori DPI alti in Windows).

## <a name="quickstart"></a>Avvio rapido

- Assicurarsi Visual Studio sia in esecuzione in modalità PMA (vedere **Abilitazione di PMA)**

- Verificare che l'estensione funzioni correttamente in un set di scenari comuni (vedere **Test delle estensioni per problemi PMA)**

- Se si verificano problemi, è possibile usare le strategie/raccomandazioni illustrate in questo documento per diagnosticare e risolvere tali problemi. Sarà anche necessario aggiungere il nuovo pacchetto NuGet [Microsoft.VisualStudio.DpiAwareness](https://www.nuget.org/packages/Microsoft.VisualStudio.DpiAwareness/) al progetto per accedere alle API necessarie.

## <a name="enable-pma"></a>Abilitare PMA

Per abilitare PMA in Visual Studio, è necessario soddisfare i requisiti seguenti:

- Aggiornamento di Windows 10 (aprile 2018) (v1803, RS4) o versione successiva
- .NET Framework 4.8 RTM o versione successiva
- Visual Studio 2019 con l'opzione "Ottimizza il rendering per schermi con [densità di pixel diverse"](../../ide/reference/general-environment-options-dialog-box.md) abilitata

Una volta soddisfatti questi requisiti, Visual Studio automaticamente la modalità PMA nel processo.

> [!NOTE]
> Windows Forms contenuto in Visual Studio (ad esempio Visualizzatore proprietà) supporta PMA solo se si ha Visual Studio 2019 versione 16.1 o successiva.

## <a name="test-your-extensions-for-pma-issues"></a>Testare le estensioni per i problemi di PMA

Visual Studio supporta ufficialmente i framework dell'interfaccia utente WPF, Windows Forms, Win32 e HTML/JS. Quando Visual Studio viene attivata la modalità PMA, ogni stack dell'interfaccia utente si comporta in modo diverso. Pertanto, indipendentemente dal framework dell'interfaccia utente, è consigliabile eseguire un test superato per garantire che tutta l'interfaccia utente sia conforme alla modalità PMA.

È consigliabile convalidare gli scenari comuni seguenti:

- Modifica del fattore di scala di un singolo ambiente di monitoraggio durante l'esecuzione dell'applicazione.

  Questo scenario consente di verificare che l'interfaccia utente risponda alla modifica dinamica del valore DPI di Windows.

- Ancoraggio/disancco di un portatile in cui un monitor collegato è impostato sul computer primario e il monitor collegato ha un fattore di scala diverso rispetto al portatile mentre l'applicazione è in esecuzione.

  Questo scenario consente di verificare che l'interfaccia utente risponda alla modifica DPI di visualizzazione, nonché di gestire gli schermi aggiunti o rimossi dinamicamente.

- Avere più monitor con fattori di scala diversi e spostare l'applicazione tra di essi.

  Questo scenario consente di verificare che l'interfaccia utente risponda alla modifica DPI visualizzata
    
- Comunicazione remota in un computer quando i computer locali e remoti hanno fattori di scala diversi per il monitoraggio primario.

  Questo scenario consente di verificare che l'interfaccia utente risponda alla modifica dinamica del valore DPI di Windows.

Un buon test preliminare per verificare se l'interfaccia utente potrebbe avere problemi è se il codice usa le classi *Microsoft.VisualStudio.Utilities.Dpi.DpiHelper*, *Microsoft.VisualStudio.PlatformUI.DpiHelper* o *VsUI::CDpiHelper.* Queste classi DpiHelper meno recente supportano solo il riconoscimento DPI di sistema e non sempre funzionano correttamente quando il processo è PMA.

L'uso tipico di questi DpiHelper sarà simile al seguente:

```cs
Point screenTopRight = logicalBounds.TopRight.LogicalToDeviceUnits();

POINT screenIntTopRight = new POINT
{
    x = (int)screenTopRIght.X,
    y = (int)screenTopRIght.Y
}

// Declared via P/Invoke
IntPtr monitor = MonitorFromPoint(screenIntTopRight, MONITOR_DEFAULTTONEARST);
```

Nell'esempio precedente un rettangolo che rappresenta i limiti logici di una finestra viene convertito in unità di dispositivo in modo che possa essere passato al metodo nativo MonitorFromPoint che prevede coordinate del dispositivo per restituire un puntatore di monitoraggio accurato.

### <a name="classes-of-issues"></a>Classi di problemi
Quando la modalità PMA è abilitata per Visual Studio, l'interfaccia utente potrebbe replicare i problemi in diversi modi comuni. La maggior parte, se non tutti, di questi problemi può verificarsi in Visual Studio framework dell'interfaccia utente supportati. Inoltre, questi problemi possono verificarsi anche quando una parte dell'interfaccia utente è ospitata in scenari di ridimensionamento DPI in modalità mista . Per altre informazioni, vedere la documentazione di [Windows.](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) 

#### <a name="win32-window-creation"></a>Creazione di finestre Win32
Quando si creano finestre con CreateWindow() o CreateWindowEx(), un modello comune è creare la finestra in corrispondenza delle coordinate (0,0) (l'angolo superiore sinistro della visualizzazione principale), quindi spostarla nella posizione finale. In questo modo, tuttavia, la finestra può attivare un messaggio o un evento modificato DPI, che può inviare nuovamente altri messaggi o eventi dell'interfaccia utente e alla fine causare un comportamento o un rendering indesiderato.

#### <a name="wpf-element-placement"></a>Posizionamento degli elementi WPF
Quando si spostano elementi WPF usando la versione precedente di Microsoft.VisualStudio.Utilities.Dpi.DpiHelper, le coordinate in alto a sinistra potrebbero non essere calcolate correttamente ogni volta che gli elementi sono in un valore DPI non primario.

#### <a name="serialization-of-ui-element-sizes-or-positions"></a>Serializzazione di dimensioni o posizioni degli elementi dell'interfaccia utente
Quando le dimensioni o la posizione dell'interfaccia utente (se salvate come unità dispositivo) vengono ripristinate in un contesto DPI diverso da quello in cui è stata archiviata, verranno posizionate e ridimensionate in modo non corretto. Ciò si verifica perché le unità dispositivo hanno una relazione DPI intrinseca.

#### <a name="incorrect-scaling"></a>Ridimensionamento non corretto
Gli elementi dell'interfaccia utente creati nel valore DPI primario verranno ridimensionati correttamente, tuttavia, quando vengono spostati in una visualizzazione con un valore DPI diverso, non vengono ridimensionati e il contenuto è troppo grande o troppo piccolo.

#### <a name="incorrect-bounding"></a>Delimitazione non corretta
Analogamente al problema di ridimensionamento, gli elementi dell'interfaccia utente calcolano correttamente i limiti nel contesto DPI primario, ma quando vengono spostati in un valore DPI non primario, non calcolano correttamente i nuovi limiti. Di conseguenza, la finestra del contenuto è troppo piccola o troppo grande rispetto all'interfaccia utente di hosting, con il risultato di uno spazio vuoto o di un ritaglio.

#### <a name="drag--drop"></a>Trascinare & rilascio
Ogni volta che all'interno di scenari DPI in modalità mista (ad esempio, il rendering di elementi dell'interfaccia utente diversi in modalità di riconoscimento DPI diverse), le coordinate di trascinamento della selezione potrebbero essere calcolate in modo errato, determinando una posizione finale di rilascio non corretta.

#### <a name="out-of-process-ui"></a>Interfaccia utente out-of-process
Parte dell'interfaccia utente viene creata out-of-process e se il processo esterno di creazione è in una modalità di riconoscimento DPI diversa rispetto a Visual Studio, ciò può introdurre uno dei problemi di rendering precedenti.

#### <a name="windows-forms-controls-images-or-layouts-rendered-incorrectly"></a>Windows Forms rendering non corretto di controlli, immagini o layout
Non tutti i contenuti Windows Forms supportano la modalità PMA. Di conseguenza, è possibile che si sia verificato un problema di rendering con layout o ridimensionamenti non corretti. Una possibile soluzione in questo caso consiste nell'eseguire in modo esplicito il rendering del contenuto Windows Forms in "System Aware" DpiAwarenessContext (vedere Force a control into a specific DpiAwarenessContext ( Forzare un controllo in un [oggetto DpiAwarenessContext specifico).](#force-a-control-into-a-specific-dpiawarenesscontext)

#### <a name="windows-forms-controls-or-windows-not-displaying"></a>Windows Forms controlli o finestre non visualizzati
Una delle cause principali di questo problema è che gli sviluppatori tentano di riassare un controllo o una finestra con un oggetto DpiAwarenessContext a una finestra con un oggetto DpiAwarenessContext diverso.

Le immagini seguenti mostrano le restrizioni **del sistema** operativo Windows predefinite correnti nelle finestre padre:

![Screenshot del comportamento di padre corretto](media/PMA-parenting-behavior.PNG)

> [!Note]
> È possibile modificare questo comportamento impostando il comportamento di hosting dei thread (vedere [l Dpi_Hosting_Behavior enumere](/windows/desktop/api/windef/ne-windef-dpi_hosting_behavior)).

Di conseguenza, se si imposta una relazione padre-figlio tra modalità non supportate, l'operazione avrà esito negativo e il rendering del controllo o della finestra potrebbe non essere eseguito come previsto.

### <a name="diagnose-issues"></a>Diagnosticare i problemi

Esistono molti fattori da considerare quando si identificano i problemi correlati a PMA: 

- L'interfaccia utente o l'API prevede valori logici o del dispositivo?
    - Le API e l'interfaccia utente WPF usano in genere valori logici (ma non sempre)
    - L'interfaccia utente e le API Win32 usano in genere i valori del dispositivo

- Da dove derivano i valori?
    - Se riceve valori da un'altra interfaccia utente o API, passa i valori logici o del dispositivo.
    - Se si ricevono valori da più origini, tutti usano/si aspettano gli stessi tipi di valori o le conversioni devono essere miste e corrispondenti?

- Le costanti dell'interfaccia utente sono in uso e in quale forma sono?

- Il thread è nel contesto DPI corretto per i valori che riceve?

  Le modifiche per abilitare l'hosting DPI misto devono in genere inserire i percorsi del codice nel contesto corretto, tuttavia le operazioni eseguite all'esterno del ciclo di messaggi principale o del flusso di eventi potrebbero essere eseguite nel contesto DPI errato.

- I valori superano i limiti del contesto DPI?

  Trascinare & rilascio è una situazione comune in cui le coordinate possono attraversare contesti DPI. Window tenta di eseguire l'operazione giusta, ma in alcuni casi l'interfaccia utente host potrebbe dover eseguire operazioni di conversione per garantire limiti di contesto corrispondenti.

### <a name="pma-nuget-package"></a>Pacchetto NuGet PMA
Le nuove librerie DpiAwarness sono disponibili nel pacchetto [NuGet Microsoft.VisualStudio.DpiAwareness.](https://www.nuget.org/packages/Microsoft.VisualStudio.DpiAwareness/)

### <a name="recommended-tools"></a>Strumenti consigliati
Gli strumenti seguenti consentono di eseguire il debug di problemi correlati a PMA in alcuni dei diversi stack dell'interfaccia utente supportati da Visual Studio.

#### <a name="snoop"></a>Snoop
Snoop è uno strumento di debug XAML che include alcune funzionalità aggiuntive che non sono disponibili Visual Studio strumenti XAML predefiniti. Inoltre, Snoop non deve eseguire attivamente il debug Visual Studio essere in grado di visualizzare e modificare l'interfaccia utente WPF. I due modi principali in cui Snoop può essere utile per diagnosticare i problemi di PMA è la convalida delle coordinate di posizionamento logiche o dei limiti delle dimensioni e per la convalida dell'interfaccia utente è disponibile il valore DPI giusto.
 
#### <a name="visual-studio-xaml-tools"></a>Visual Studio xaml
Come Snoop, gli strumenti XAML in Visual Studio consentono di diagnosticare i problemi di PMA. Una volta trovato un probabile responsabile, è possibile impostare punti di interruzione e usare la finestra Struttura ad albero visuale attiva e le finestre di debug per esaminare i limiti dell'interfaccia utente e il valore DPI corrente.

## <a name="strategies-for-fixing-pma-issues"></a>Strategie per la risoluzione dei problemi di PMA

### <a name="replace-dpihelper-calls"></a>Sostituire le chiamate DpiHelper

Nella maggior parte dei casi, la correzione dei problemi dell'interfaccia utente in modalità PMA si riduce alla sostituzione delle chiamate nel codice gestito con le classi *Microsoft.VisualStudio.Utilities.Dpi.DpiHelper* e *Microsoft.VisualStudio.PlatformUI.DpiHelper,* con chiamate alla nuova classe helper *Microsoft.VisualStudio.Utilities.DpiAwareness.* 

```cs
// Remove this kind of use:
Point deviceTopLeft = new Point(window.Left, window.Top).LogicalToDeviceUnits();

// Replace with this use:
Point deviceTopLeft = window.LogicalToDevicePoint(new Point(window.Left, window.Top));
```

Per il codice nativo, comporterà la sostituzione delle chiamate alla classe *VsUI::CDpiHelper* precedente con le chiamate alla nuova *classe VsUI::CDpiAwareness.* 

```cpp
// Remove this kind of use:
int cx = VsUI::DpiHelper::LogicalToDeviceUnitsX(m_cxS);
int cy = VsUI::DpiHelper::LogicalToDeviceUnitsY(m_cyS);

// Replace with this use:
int cx = m_cxS;
int cy = m_cyS;
VsUI::CDpiAwareness::LogicalToDeviceUnitsX(m_hwnd, &cx);
VsUI::CDpiAwareness::LogicalToDeviceUnitsY(m_hwnd, &cy);
```

Le nuove classi DpiAwareness e CDpiAwareness offrono gli stessi helper di conversione unità delle classi DpiHelper, ma richiedono un parametro di input aggiuntivo: l'elemento dell'interfaccia utente da usare come riferimento per l'operazione di conversione. È importante notare che gli helper di ridimensionamento delle immagini non esistono nei nuovi helper DpiAwareness/CDpiAwareness e, se necessario, è necessario usare [invece ImageService.](../image-service-and-catalog.md)

La classe DpiAwareness gestita offre helper per oggetti visivi WPF, controlli Windows Forms e HWND Win32 e HMONITOR (entrambi nel formato IntPtrs), mentre la classe CDpiAwareness nativa offre helper HWND e HMONITOR.

### <a name="windows-forms-dialogs-windows-or-controls-displayed-in-the-wrong-dpiawarenesscontext"></a>Windows Forms finestre, finestre o controlli visualizzati in DpiAwarenessContext errato
Anche dopo un corretto controllo padre di finestre con DpiAwarenessContext diversi (a causa del comportamento predefinito di Windows), gli utenti possono comunque vedere problemi di ridimensionamento come le finestre con DpiAwarenessContext diversi ridimensionano in modo diverso. Di conseguenza, gli utenti potrebbero vedere problemi di allineamento/sfocatura del testo o dell'immagine nell'interfaccia utente.

La soluzione consiste nell'impostare l'ambito DpiAwarenessContext corretto per tutte le finestre e i controlli nell'applicazione.

### <a name="top-level-mixed-mode-tlmm-dialogs"></a>Finestre di dialogo in modalità mista di primo livello (TLMM)
Quando si creano finestre di primo livello, ad esempio dialoghe modali, è importante assicurarsi che il thread sia nello stato corretto prima della creazione della finestra (e del relativo handle). Il thread può essere inserito in Riconoscimento sistema usando l'helper CDpiScope in modalità nativa o l'helper DpiAwareness.EnterDpiScope in managed. È consigliabile usare TLMM in genere in finestre di dialogo/finestre non WPF.

### <a name="child-level-mixed-mode-clmm"></a>Modalità mista a livello di figlio (CLMM)
Per impostazione predefinita, le finestre figlio ricevono il contesto di riconoscimento DPI del thread corrente se creato senza un elemento padre o il contesto di riconoscimento DPI dell'elemento padre quando viene creato con un elemento padre. Per creare un elemento figlio con un contesto di riconoscimento DPI diverso da quello padre, il thread può essere inserito nel contesto di riconoscimento DPI desiderato. È quindi possibile creare l'elemento figlio senza un elemento padre e riasparentare manualmente la finestra padre.

#### <a name="clmm-issues"></a>Problemi di CLMM
La maggior parte delle operazioni di calcolo dell'interfaccia utente eseguite come parte del ciclo di messaggistica principale o della catena di eventi deve essere già in esecuzione nel contesto di riconoscimento DPI giusto. Tuttavia, se i calcoli delle coordinate o del ridimensionamento vengono esatti al di fuori di questi flussi di lavoro principali, ad esempio durante un'attività in fase di inattività o all'esterno del thread dell'interfaccia utente, il contesto di riconoscimento DPI corrente potrebbe non essere corretto, causando problemi di posizione errata o di ridimensionamento errato dell'interfaccia utente. L'inserimento del thread nello stato corretto per il lavoro dell'interfaccia utente risolve in genere il problema.
 
#### <a name="opt-out-of-clmm"></a>Rifiutare esplicitamente CLMM
Se viene eseguita la migrazione di una finestra degli strumenti non WPF per supportare completamente PMA, sarà necessario rifiutare esplicitamente CLMM. A tale scopo, deve essere implementata una nuova interfaccia: IVsDpiAware.

```cs
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown)]
public interface IVsDpiAware
{
    [ComAliasName("Microsoft.VisualStudio.Shell.Interop.VSDPIMode")]
    uint Mode {get;}
}
```

```cpp
IVsDpiAware : public IUnknown
{
    public:
        HRRESULT STDMETHODCALLTYPE get_Mode(__RCP__out VSDPIMODE *dwMode);
};
```

Per i linguaggi gestiti, la posizione migliore per implementare questa interfaccia è nella stessa classe che deriva da *Microsoft.VisualStudio.Shell.ToolWindowPane*. Per C++, la posizione migliore per implementare questa interfaccia è nella stessa classe che implementa *IVsWindowPane* da vsshell.h.

Il valore restituito dalla proprietà Mode nell'interfaccia è un __VSDPIMODE (e cast a uint in managed):

```cs
enum __VSDPIMODE
{
    VSDM_Unaware    = 0x01,
    VSDM_System     = 0x02,
    VSDM_PerMonitor = 0x03,
}
```

- Inconsapevole significa che la finestra degli strumenti deve gestire 96 DPI, Windows gestirà il ridimensionamento per tutti gli altri DPI. Il contenuto risulta leggermente sfocato.
- System indica che la finestra degli strumenti deve gestire il valore DPI per il valore DPI di visualizzazione principale. Qualsiasi visualizzazione con un valore DPI corrispondente avrà un aspetto nitido, ma se il valore DPI è diverso o cambia durante la sessione, Windows gestirà il ridimensionamento e sarà leggermente sfocato.
- PerMonitor indica che la finestra degli strumenti deve gestire tutti gli indicatori DPI in tutti gli schermi e ogni volta che cambia il valore DPI.

> [!NOTE]
> Visual Studio supporta solo il riconoscimento PerMonitorV2, quindi il valore dell'enumerazione PerMonitor viene tradotto nel valore windows di DPI_AWARENESS_CONTEXT_PER_MONITOR_AWARE_V2.

#### <a name="force-a-control-into-a-specific-dpiawarenesscontext"></a>Forzare un controllo in un oggetto DpiAwarenessContext specifico

L'interfaccia utente legacy che non viene aggiornata per supportare la modalità PMA potrebbe comunque richiedere modifiche secondarie mentre Visual Studio in esecuzione in modalità PMA. Una di queste correzioni prevede la creazione dell'interfaccia utente nel contesto DpiAwarenessContext corretto. Per forzare l'interfaccia utente in un oggetto DpiAwarenessContext specifico, è possibile immettere un ambito DPI con il codice seguente:

```cs
using (DpiAwareness.EnterDpiScope(DpiAwarenessContext.SystemAware))
{
    Form form = new MyForm();
    form.ShowDialog();
}
```

```cpp
void MyClass::ShowDialog()
{
    VsUI::CDpiScope dpiScope(DPI_AWARENESS_CONTEXT_SYSTEM_AWARE);
    HWND hwnd = ::CreateWindow(...);
}
```

> [!NOTE]
> L'applicazione forzata di DpiAwarenessContext funziona solo in finestre di dialogo WPF non WPF e di primo livello. Quando si crea l'interfaccia utente WPF che deve essere ospitata all'interno di finestre degli strumenti o finestre di progettazione, non appena il contenuto viene inserito nell'albero dell'interfaccia utente WPF, viene convertito nel processo corrente DpiAwarenessContext.

## <a name="known-issues"></a>Problemi noti

### <a name="windows-forms"></a>Windows Forms

Per ottimizzare i nuovi scenari in modalità mista, Windows Forms modo in cui crea controlli e finestre ogni volta che l'elemento padre non è stato impostato in modo esplicito. In precedenza, i controlli senza un elemento padre esplicito usava una "finestra di parcheggio" interna come padre temporaneo per il controllo o la finestra in fase di creazione. 

Prima di .NET 4.8, era presente una singola "finestra di parcheggio" che ottiene il proprio oggetto DpiAwarenessContext dal contesto di riconoscimento DPI del thread corrente al momento della creazione della finestra. Qualsiasi controllo senza padre eredita lo stesso oggetto DpiAwarenessContext della finestra di parcheggio quando viene creato l'handle del controllo e verrà riasparentato all'elemento padre finale/previsto dallo sviluppatore dell'applicazione. Ciò causerebbe errori basati sulla temporizzazione se "Finestra di parcheggio" ha un DpiAwarenessContext superiore rispetto alla finestra padre finale.

A data di .NET 4.8 è ora disponibile una "finestra di parcheggio" per ogni oggetto DpiAwarenessContext rilevato. L'altra differenza principale è che DpiAwarenessContext usato per il controllo viene memorizzato nella cache quando viene creato il controllo, non quando viene creato l'handle. Ciò significa che il comportamento finale complessivo è lo stesso, ma può trasformare quello che era un problema basato sulla temporizzazione in un problema coerente. Offre anche allo sviluppatore dell'applicazione un comportamento più deterministico per la scrittura del codice dell'interfaccia utente e l'ambito corretto.
