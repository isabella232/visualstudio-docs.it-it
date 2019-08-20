---
title: Supporto per la sensibilizzazione per monitor per Extender di Visual Studio
titleSuffix: ''
description: Informazioni sul nuovo supporto Extender per il riconoscimento per monitoraggio disponibile in Visual Studio 2019.
ms.date: 04/10/2019
helpviewer_keywords:
- Visual Studio, PMA, per-monitor-awareness, extenders, Windows Forms
- Per-Monitor Awareness support for extenders
author: rub8n
ms.author: rurios
manager: anthc
monikerRange: vs-2019
ms.topic: conceptual
dev_langs:
- CSharp
- CPP
ms.openlocfilehash: 09ec5d82251fa4598096fca8a59c9a1fd29e3f27
ms.sourcegitcommit: b83fefa8177c5554cbe2c59c4d102cbc534f7cc6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/19/2019
ms.locfileid: "69585377"
---
# <a name="per-monitor-awareness-support-for-visual-studio-extenders"></a>Supporto per la sensibilizzazione per monitor per Extender di Visual Studio

Nelle versioni precedenti a Visual Studio 2019 il contesto di riconoscimento DPI è stato impostato su System Aware, anziché per il monitor DPI Aware (PMA). L'esecuzione nella consapevolezza del sistema ha comportato un'esperienza visiva degradata (ad esempio, i tipi di carattere o le icone sfocate) quando Visual Studio doveva eseguire il rendering tra monitoraggi con fattori di scala diversi o in computer con configurazioni di visualizzazione diverse (ad esempio, diversi Ridimensionamento di Windows).

Il contesto di riconoscimento DPI di Visual Studio 2019 è impostato come PMA, quando l'ambiente lo supporta, consentendo a Visual Studio di eseguire il rendering in base alla configurazione dello schermo in cui è ospitato anziché una singola configurazione definita dal sistema. Infine, la conversione in un'interfaccia utente sempre nitida per aree di superficie che supportano la modalità PMA.

Per ulteriori informazioni sui termini e sullo scenario generale trattati in questo documento, vedere la documentazione relativa [allo sviluppo di applicazioni desktop con DPI elevato in Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) .

## <a name="quickstart"></a>Guida introduttiva

- Verificare che Visual Studio sia in esecuzione in modalità PMA (vedere Abilitazione di **PMA**)

- Verificare che l'estensione funzioni correttamente in un set di scenari comuni (vedere **test delle estensioni per i problemi PMA**)

- Se si riscontrano problemi, è possibile usare le strategie e le raccomandazioni descritte in questo documento per diagnosticare e risolvere tali problemi. Sarà anche necessario aggiungere il nuovo pacchetto NuGet [Microsoft. VisualStudio. DpiAwareness](https://www.nuget.org/packages/Microsoft.VisualStudio.DpiAwareness/) al progetto per accedere alle API richieste.

## <a name="enable-pma"></a>Abilita PMA

Per abilitare PMA in Visual Studio, è necessario soddisfare i requisiti seguenti:

- Aggiornamento di Windows 10 aprile 2018 (v1803, RS4) o versione successiva
- .NET Framework 4,8 RTM o versione successiva
- Visual Studio 2019 con l'opzione ["Ottimizza rendering per schermate con densità di pixel diverse"](../../ide/reference/general-environment-options-dialog-box.md) abilitata

Una volta soddisfatti questi requisiti, Visual Studio Abilita automaticamente la modalità PMA nel processo.

> [!NOTE]
> Windows Forms contenuto di Visual Studio (ad esempio il Visualizzatore proprietà) supporta PMA solo se si dispone di Visual Studio 2019 versione 16,1 o successiva.

## <a name="test-your-extensions-for-pma-issues"></a>Testare le estensioni per i problemi PMA

Visual Studio supporta ufficialmente i Framework dell'interfaccia utente WPF, Windows Forms, Win32 e HTML/JS. Quando Visual Studio viene inserito in modalità PMA, ogni stack dell'interfaccia utente si comporta in modo diverso. Di conseguenza, indipendentemente dal framework dell'interfaccia utente, è consigliabile eseguire un test superato per assicurarsi che tutte le interfacce utente siano conformi alla modalità PMA.

Si consiglia di convalidare gli scenari comuni seguenti:

- Modifica del fattore di scala di un singolo ambiente di monitoraggio durante l'esecuzione dell'applicazione.

  Questo scenario consente di verificare che l'interfaccia utente stia rispondendo alla modifica DPI dinamica di Windows.

- Ancoraggio/disancoraggio di un computer portatile in cui un monitor collegato è impostato sul database primario e il monitoraggio collegato presenta un fattore di scala diverso rispetto al portatile mentre l'applicazione è in esecuzione.

  Questo scenario consente di verificare che l'interfaccia utente stia rispondendo alla modifica del valore DPI visualizzato, oltre che alla gestione delle visualizzazioni aggiunte o rimosse dinamicamente.

- Presenza di più monitoraggi con diversi fattori di scala e spostando l'applicazione tra di essi.

  Questo scenario consente di verificare che l'interfaccia utente stia rispondendo alla modifica dello schermo DPI
    
- Comunicazione remota in un computer quando i computer locali e remoti hanno fattori di scala diversi per il monitor primario.

  Questo scenario consente di verificare che l'interfaccia utente stia rispondendo alla modifica DPI dinamica di Windows.

Un valido test preliminare per determinare se l'interfaccia utente potrebbe avere problemi se il codice usa le classi *Microsoft. VisualStudio. Utilities. dpi. DpiHelper*, *Microsoft. VisualStudio. PlatformUI. DpiHelper*o *incorporati vsui:: CDpiHelper* . Queste classi DpiHelper precedenti supportano solo la consapevolezza DPI del sistema e non funzioneranno sempre correttamente quando il processo è PMA.

L'utilizzo tipico di questi DpiHelpers sarà simile al seguente:

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

Nell'esempio precedente, un rettangolo che rappresenta i limiti logici di una finestra viene convertito in unità di dispositivo in modo che possa essere passato al metodo nativo MonitorFromPoint che prevede le coordinate del dispositivo per restituire un puntatore di monitoraggio accurato.

### <a name="classes-of-issues"></a>Classi di problemi
Quando è abilitata la modalità PMA per Visual Studio, l'interfaccia utente può replicare i problemi in diversi modi. La maggior parte, se non tutti, di questi problemi può verificarsi in qualsiasi framework dell'interfaccia utente supportato da Visual Studio. Inoltre, questi problemi possono verificarsi anche quando una parte dell'interfaccia utente viene ospitata in scenari di scalabilità DPI in modalità mista. per ulteriori informazioni, vedere la [documentazione](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) di Windows. 

#### <a name="win32-window-creation"></a>Creazione finestra Win32
Quando si crea Windows con CreateWindow () o CreateWindowEx (), un modello comune consiste nel creare la finestra in corrispondenza delle coordinate (0,0), ovvero l'angolo superiore sinistro dello schermo principale, quindi spostarlo nella posizione finale. Questa operazione può tuttavia comportare l'attivazione di un messaggio o un evento di modifica DPI da parte della finestra, che può riattivare altri messaggi o eventi dell'interfaccia utente e, infine, causare il rendering o il comportamento indesiderato.

#### <a name="wpf-element-placement"></a>Posizionamento elementi WPF
Quando si trascinano elementi WPF utilizzando il vecchio Microsoft. VisualStudio. Utilities. dpi. DpiHelper, le coordinate top-left potrebbero non essere calcolate correttamente ogni volta che gli elementi si trovano in un valore DPI non primario.

#### <a name="serialization-of-ui-element-sizes-or-positions"></a>Serializzazione di dimensioni o posizioni degli elementi dell'interfaccia utente
Quando le dimensioni o la posizione dell'interfaccia utente (se salvate come unità dispositivo) vengono ripristinate in un contesto DPI diverso rispetto a quello in cui è stato archiviato, verranno posizionate e ridimensionate in modo errato. Questo problema si verifica perché le unità del dispositivo hanno una relazione DPI intrinseca.

#### <a name="incorrect-scaling"></a>Ridimensionamento non corretto
Gli elementi dell'interfaccia utente creati sul valore DPI primario vengono ridimensionati correttamente, tuttavia, se spostati in una visualizzazione con un valore DPI diverso, non vengono ridimensionati e il relativo contenuto è troppo grande o troppo piccolo.

#### <a name="incorrect-bounding"></a>Delimitazione non corretta
Analogamente al problema di scalabilità, gli elementi dell'interfaccia utente calcolano correttamente i limiti nel contesto DPI primario. Tuttavia, quando vengono spostati in un valore DPI non primario, i nuovi limiti non vengono calcolati correttamente. Di conseguenza, la finestra del contenuto è troppo piccola o troppo grande rispetto all'interfaccia utente host, che comporta spazio vuoto o ritaglio.

#### <a name="drag--drop"></a>Trascina & rilasciare
Ogni volta che negli scenari con valori DPI in modalità mista (ad esempio, il rendering di elementi dell'interfaccia utente differenti in modalità di riconoscimento DPI diverse), le coordinate di trascinamento e rilascio potrebbero essere calcolate in modo errato e la posizione finale finale non è corretta.

#### <a name="out-of-process-ui"></a>Interfaccia utente out-of-process
Una parte dell'interfaccia utente viene creata out-of-process e se il processo esterno di creazione si trova in una modalità di riconoscimento DPI diversa da Visual Studio, è possibile che si verifichino i problemi di rendering precedenti.

#### <a name="windows-forms-controls-images-or-layouts-rendered-incorrectly"></a>Rendering di controlli, immagini o layout Windows Forms non corretti
Non tutti i contenuti del Windows Forms supportano la modalità PMA. Di conseguenza, è possibile che venga visualizzato un problema di rendering con layout non corretti o con scalabilità. Una possibile soluzione in questo caso consiste nel eseguire il rendering esplicito di Windows Forms contenuto in DpiAwarenessContext "System Aware" (fare riferimento a [forzare un controllo in un DpiAwarenessContext specifico](#force-a-control-into-a-specific-dpiawarenesscontext)).

#### <a name="windows-forms-controls-or-windows-not-displaying"></a>Controlli Windows Forms o Windows non visualizzati
Una delle cause principali di questo problema è rappresentata dagli sviluppatori che tentano di riassociare un controllo o una finestra con un DpiAwarenessContext a una finestra con un DpiAwarenessContext diverso.

Le immagini seguenti mostrano le restrizioni correnti del sistema operativo Windows in finestre padre:

![Screenshot del comportamento corretto dell'elemento padre](media/PMA-parenting-behavior.PNG)

> [!Note]
> È possibile modificare questo comportamento impostando il comportamento di hosting del thread (vedere l' [enumerazione Dpi_Hosting_Behavior](/windows/desktop/api/windef/ne-windef-dpi_hosting_behavior)).

Di conseguenza, se si imposta la relazione padre-figlio tra modalità non supportate, l'operazione avrà esito negativo e non sarà possibile eseguire il rendering del controllo o della finestra come previsto.

### <a name="diagnose-issues"></a>Diagnosticare i problemi

Esistono molti fattori da considerare quando si identificano i problemi relativi a PMA: 

- L'interfaccia utente o l'API prevede valori logici o del dispositivo?
    - Le API e l'interfaccia utente WPF usano in genere valori logici (ma non sempre)
    - L'interfaccia utente Win32 e le API usano in genere i valori del dispositivo

- Da dove provengono i valori?
    - Se si ricevono valori da un'altra interfaccia utente o da un'altra API, sta passando i valori logici o del dispositivo.
    - Se si ricevono valori da più origini, è necessario che tutti usino/prevedano gli stessi tipi di valori o che le conversioni debbano essere combinate e confrontate?

- Le costanti dell'interfaccia utente sono in uso e il formato in cui si trovano?

- Il thread è nel contesto DPI corretto per i valori che riceve?

  Le modifiche per abilitare l'hosting con DPI misto dovrebbero in genere inserire i percorsi del codice nel contesto corretto. Tuttavia, il lavoro eseguito all'esterno del ciclo di messaggi principale o del flusso di eventi potrebbe essere eseguito nel contesto DPI errato.

- I valori sono i limiti del contesto tra DPI?

  Il trascinamento della selezione & è una situazione comune in cui le coordinate possono superare i contesti DPI. La finestra tenta di eseguire l'operazione corretta, ma in alcuni casi è possibile che l'interfaccia utente host debba eseguire operazioni di conversione per garantire la corrispondenza dei limiti del contesto.

### <a name="pma-nuget-package"></a>Pacchetto NuGet PMA
Le nuove librerie DpiAwarness sono disponibili nel pacchetto NuGet [Microsoft. VisualStudio. DpiAwareness](https://www.nuget.org/packages/Microsoft.VisualStudio.DpiAwareness/) .

### <a name="recommended-tools"></a>Strumenti consigliati
Gli strumenti seguenti consentono di eseguire il debug di problemi correlati a PMA in alcuni dei diversi stack dell'interfaccia utente supportati da Visual Studio.

#### <a name="snoop"></a>Snoop
Snoop è uno strumento di debug XAML che presenta alcune funzionalità aggiuntive che non sono disponibili negli strumenti XAML predefiniti di Visual Studio. Inoltre, Snoop non deve eseguire attivamente il debug di Visual Studio per poter visualizzare e modificare l'interfaccia utente WPF. I due modi principali di Snoop possono essere utili per la diagnosi dei problemi PMA per la convalida delle coordinate di posizionamento logiche o dei limiti di dimensione e per la convalida dell'interfaccia utente con il valore DPI corretto.
 
#### <a name="visual-studio-xaml-tools"></a>Strumenti XAML di Visual Studio
Come Snoop, gli strumenti XAML in Visual Studio consentono di diagnosticare i problemi PMA. Una volta individuato un colpevole probabile, è possibile impostare punti di interruzione e utilizzare la finestra albero elementi visivi attivi e le finestre di debug per controllare i limiti dell'interfaccia utente e il valore DPI corrente.

## <a name="strategies-for-fixing-pma-issues"></a>Strategie per la correzione dei problemi PMA

### <a name="replace-dpihelper-calls"></a>Sostituisci chiamate DpiHelper

Nella maggior parte dei casi, la correzione dei problemi dell'interfaccia utente in modalità PMA si riduce alla sostituzione delle chiamate nel codice gestito alle classi *Microsoft. VisualStudio. Utilities. dpi. DpiHelper* e *Microsoft. VisualStudio. PlatformUI. DpiHelper* precedenti, con chiamate al nuovo  *Classe helper Microsoft. VisualStudio. Utilities. DpiAwareness* . 

```cs
// Remove this kind of use:
Point deviceTopLeft = new Point(window.Left, window.Top).LogicalToDeviceUnits();

// Replace with this use:
Point deviceTopLeft = window.LogicalToDevicePoint(new Point(window.Left, window.Top));
```

Per il codice nativo, comporterà la sostituzione delle chiamate alla classe *incorporati vsui:: CDpiHelper* precedente con le chiamate alla nuova classe *incorporati vsui:: CDpiAwareness* . 

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

Le nuove classi DpiAwareness e CDpiAwareness offrono gli stessi helper di conversione unità delle classi DpiHelper ma richiedono un parametro di input aggiuntivo, ovvero l'elemento dell'interfaccia utente da usare come riferimento per l'operazione di conversione. È importante notare che gli helper di ridimensionamento delle immagini non esistono nei nuovi Helper DpiAwareness/CDpiAwareness e, se necessario, è consigliabile usare il [ImageService](../image-service-and-catalog.md) .

La classe DpiAwareness gestita offre helper per oggetti visivi WPF, controlli Windows Forms e HWND Win32 e HMONITORs (entrambi nel formato IntPtrs), mentre la classe CDpiAwareness nativa offre Helper HWND e HMONITOR.

### <a name="windows-forms-dialogs-windows-or-controls-displayed-in-the-wrong-dpiawarenesscontext"></a>Windows Forms finestre di dialogo, finestre o controlli visualizzati nel DpiAwarenessContext errato
Anche dopo aver completato l'elemento padre di Windows con DpiAwarenessContexts diversi (a causa del comportamento predefinito di Windows), è possibile che gli utenti visualizzino ancora problemi di scalabilità come Windows con scalabilità DpiAwarenessContexts diversa. Di conseguenza, gli utenti possono visualizzare problemi di allineamento/sfocatura o immagini nell'interfaccia utente.

La soluzione consiste nell'impostare l'ambito DpiAwarenessContext corretto per tutte le finestre e i controlli nell'applicazione.

### <a name="top-level-mixed-mode-tlmm-dialogs"></a>Finestre di dialogo in modalità mista di primo livello (TLMM)
Quando si creano finestre di primo livello, come le finestre di dialogo modali, è importante assicurarsi che il thread si trovi nello stato corretto prima della creazione della finestra (e del relativo handle). Il thread può essere inserito nella consapevolezza del sistema usando l'helper CDpiScope in native o DpiAwareness. EnterDpiScope helper in Managed. (TLMM deve essere in genere usato in finestre di dialogo/finestre non WPF).

### <a name="child-level-mixed-mode-clmm"></a>Modalità mista a livello di figlio (CLMM)
Per impostazione predefinita, le finestre figlio ricevono il contesto di riconoscimento DPI del thread corrente se viene creato senza un elemento padre o il contesto di riconoscimento DPI dell'elemento padre quando viene creato con un elemento padre. Per creare un elemento figlio con un contesto di compatibilità DPI diverso rispetto al relativo padre, il thread può essere inserito nel contesto di riconoscimento DPI desiderato. Il figlio può quindi essere creato senza un elemento padre e associato manualmente alla finestra padre.

#### <a name="clmm-issues"></a>Problemi di CLMM
La maggior parte delle operazioni di calcolo dell'interfaccia utente eseguite come parte del ciclo di messaggistica principale o della catena di eventi dovrebbe essere già in esecuzione nel contesto di compatibilità con DPI destro. Tuttavia, se i calcoli di coordinate o di ridimensionamento vengono eseguiti al di fuori di questi flussi di lavoro principali, ad esempio durante un'attività del tempo di inattività o il thread dell'interfaccia utente, il contesto di consapevolezza DPI corrente potrebbe non essere corretto, causando problemi di ridimensionamento dell'interfaccia utente o di dimensioni errate. L'inserimento del thread nello stato corretto per il lavoro dell'interfaccia utente in genere corregge il problema.
 
#### <a name="opt-out-of-clmm"></a>Rifiutare esplicitamente CLMM
Se viene eseguita la migrazione di una finestra degli strumenti non WPF per supportare completamente PMA, sarà necessario rifiutare esplicitamente CLMM. A tale scopo, è necessario implementare una nuova interfaccia: IVsDpiAware.

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

Per i linguaggi gestiti, il posto migliore per implementare questa interfaccia si trova nella stessa classe che deriva da *Microsoft. VisualStudio. Shell. ToolWindowPane*. Per C++, la posizione migliore in cui implementare questa interfaccia si trova nella stessa classe che implementa *IVsWindowPane* da vsshell. h.

Il valore restituito dalla proprietà Mode sull'interfaccia è un __VSDPIMODE (ed eseguito il cast a uint in Managed):

```cs
enum __VSDPIMODE
{
    VSDM_Unaware    = 0x01,
    VSDM_System     = 0x02,
    VSDM_PerMonitor = 0x03,
}
```

- Se non si è a conoscenza della finestra degli strumenti è necessario gestire 96 DPI, Windows gestirà il ridimensionamento per tutti gli altri dpi. Il contenuto risulta leggermente sfocato.
- Sistema significa che la finestra degli strumenti deve gestire il valore DPI per il DPI di visualizzazione principale. Qualsiasi visualizzazione con un valore DPI corrispondente avrà un aspetto nitido, ma se il DPI è diverso o cambia durante la sessione, Windows gestirà la scalabilità e sarà leggermente sfocata.
- PerMonitor significa che la finestra degli strumenti deve gestire tutti i dpi in tutte le visualizzazioni e ogni volta che viene modificato il valore DPI.

> [!NOTE]
> Visual Studio supporta solo PerMonitorV2 Awareness, quindi il PerMonitor enum value viene convertito nel valore di Windows DPI_AWARENESS_CONTEXT_PER_MONITOR_AWARE_V2.

#### <a name="force-a-control-into-a-specific-dpiawarenesscontext"></a>Forzare un controllo in un DpiAwarenessContext specifico

L'interfaccia utente legacy che non è in fase di aggiornamento per supportare la modalità PMA può comunque richiedere modifiche minime per funzionare mentre Visual Studio è in esecuzione in modalità PMA. Una di queste correzioni prevede che l'interfaccia utente venga creata nel DpiAwarenessContext corretto. Per forzare l'interfaccia utente in un particolare DpiAwarenessContext, è possibile immettere un ambito DPI con il codice seguente:

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
> La forzatura di DpiAwarenessContext funziona solo su interfaccia utente non WPF e finestre di dialogo WPF di primo livello. Quando si crea un'interfaccia utente WPF che deve essere ospitata all'interno di finestre degli strumenti o finestre di progettazione, non appena il contenuto viene inserito nell'albero dell'interfaccia utente WPF, viene convertito nel processo DpiAwarenessContext corrente.

## <a name="known-issues"></a>Problemi noti

### <a name="windows-forms"></a>Windows Form

Per ottimizzare i nuovi scenari in modalità mista, Windows Forms modificato il modo in cui crea i controlli e le finestre ogni volta che l'elemento padre non è stato impostato in modo esplicito. In precedenza, i controlli senza un elemento padre esplicito usavano una "finestra di parcheggio" interna come elemento padre temporaneo per il controllo o la finestra da creare. 

Prima di .NET 4,8, era presente una singola "finestra di parcheggio" che ottiene la DpiAwarenessContext dal contesto di consapevolezza dei DPI del thread corrente al momento della creazione della finestra. Qualsiasi controllo senza padre eredita lo stesso DpiAwarenessContext della finestra di parcheggio quando viene creato l'handle del controllo e viene associato al padre finale/previsto dallo sviluppatore di applicazioni. Ciò provocherebbe errori basati sulla temporizzazione se la "finestra di parcheggio" aveva un valore di DpiAwarenessContext superiore rispetto alla finestra padre finale.

A partire da .NET 4,8, è ora disponibile una "finestra di parcheggio" per ogni DpiAwarenessContext rilevata. L'altra differenza principale è che il DpiAwarenessContext usato per il controllo viene memorizzato nella cache quando viene creato il controllo, non quando viene creato l'handle. Ciò significa che il comportamento finale complessivo è lo stesso, ma può trasformare ciò che è stato usato per un problema basato sulla temporizzazione in un problema coerente. Fornisce inoltre allo sviluppatore di applicazioni un comportamento più deterministico per la scrittura del codice dell'interfaccia utente e l'ambito corretto.
