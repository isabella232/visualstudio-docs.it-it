---
title: Creare le informazioni utente con Visual Studio finestra di progettazione XAML
description: Informazioni sull'interfaccia utente dell'area di lavoro e sulle funzionalità del finestra di progettazione XAML in Blend per Visual Studio che fornisce un'interfaccia visiva grafica che consente di progettare app basate su XAML.
ms.date: 03/03/2020
ms.topic: conceptual
ms.custom: contperf-fy21q4, SEO-VS-2020
f1_keywords:
- VS.XamlDesigner
- VS.DevicePanel
- VS.DocumentOutline
- Blend.Start.Dev12
ms.devlang: CSharp
ms.assetid: c54969a7-d75a-4a35-9b37-af7a596a7c24
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xaml-tools
ms.openlocfilehash: 448e465c1458d3a931e5c47c0236d0d733d322970ebd9aeaa9cb5c853d6dc627
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121365777"
---
# <a name="create-a-ui-by-using-xaml-designer"></a>Creare un'interfaccia utente tramite la finestra di progettazione XAML

Il finestra di progettazione XAML in Visual Studio e Blend per Visual Studio un'interfaccia visiva grafica che consente di progettare app basate su XAML, ad esempio WPF e UWP. È possibile creare interfacce utente per le app trascinando i controlli dalla finestra della casella degli strumenti (finestra Asset in Blend per Visual Studio) e impostando le proprietà nella finestra Proprietà. È anche possibile modificare il codice XAML direttamente nella visualizzazione XAML.

Per gli utenti avanzati è anche possibile [personalizzare la finestra di progettazione XAML](https://github.com/microsoft/xaml-designer-extensibility/blob/master/documents/xaml-designer-extensibility-migration.md).

> [!NOTE]
> Xamarin.Forms non supporta una finestra di progettazione XAML. Per visualizzare le UI XAML di Xamarin.Forms e modificarle mentre l'app è in esecuzione, usare Ricaricamento rapido XAML per Xamarin.Forms. Per altre informazioni, vedere la [Ricaricamento rapido XAML per Xamarin.Forms (anteprima).](/xamarin/xamarin-forms/xaml/hot-reload/)

## <a name="xaml-designer-workspace"></a>Area di lavoro della finestra di progettazione XAML

L'area di lavoro della finestra di progettazione XAML è costituita da alcuni elementi dell'interfaccia visiva, tra cui la *tavola da disegno* (ovvero l'area di progettazione visiva), l'editor XAML, la finestra Struttura documento (finestra Oggetti e sequenza temporale in Blend per Visual Studio) e la finestra Proprietà. Per aprire la finestra di progettazione XAML, fare clic con il pulsante destro del mouse su un file XAML in **Esplora soluzioni** , quindi scegliere **Progettazione visualizzazioni**.

La finestra di progettazione XAML include una visualizzazione XAML e una visualizzazione Progettazione sincronizzata del markup XAML dell'app sottoposto a rendering. Con un file XAML aperto in Visual Studio o Blend per Visual Studio, è possibile spostarsi tra la visualizzazione Progettazione e la visualizzazione XAML mediante le schede **Progettazione** e **XAML**. È possibile usare il pulsante **Scambia riquadri** nella ![finestra di progettazione XAML](media/swap-panes.PNG) per visualizzare in primo piano alternativamente la tavola da disegno o l'editor XAML.

### <a name="design-view"></a>Visualizzazione progettazione

Nella visualizzazione Progettazione la finestra che include la tavola da disegno è la finestra attiva ed è possibile usarla come area di lavoro principale. Permette di progettare visivamente una pagina nell'app aggiungendo, disegnando o modificando elementi. Per altre informazioni, vedere [Usare gli elementi nella finestra di progettazione XAML](../xaml-tools/working-with-elements-in-xaml-designer.md). Questa figura mostra la tavola da disegno nella visualizzazione Progettazione.

![Visualizzazione Progettazione della finestra di progettazione XAML](media/xaml-artboard.png)

Nella tavola da disegno sono disponibili le funzionalità seguenti:

**Guide di allineamento**

Le guide di allineamento sono *limiti di allineamento*, visualizzati sotto forma di linee tratteggiate rosse, per indicare quando i bordi dei controlli sono allineati o quando le linee di base del testo sono allineate. I limiti di allineamento vengono visualizzati solo quando è abilitato l' **allineamento alle guide di allineamento** .

**Sbarre della griglia**

Le barre di scorrimento della griglia consentono di gestire righe e colonne in un pannello [Griglia](xref:Windows.UI.Xaml.Controls.Grid). È possibile creare ed eliminare righe e colonne e modificare le rispettive larghezze e altezze. La sbarra verticale della griglia, visualizzata nel lato sinistro della tavola da disegno, viene usata per le righe, mentre la sbarra orizzontale, visualizzata in alto, viene usata per le colonne.

**Strumenti decorativi griglia**

Uno strumento decorativo griglia viene visualizzato sotto forma di triangolo a cui è collegata una linea verticale o orizzontale sulla barra di scorrimento della griglia. Quando si trascina uno strumento decorativo griglia, le larghezze o altezze delle colonne o righe adiacenti vengono aggiornate in base allo spostamento del mouse.

Gli strumenti decorativi griglia vengono usati per controllare la larghezza e l'altezza delle righe e delle colonne di una griglia. È possibile aggiungere una nuova colonna o riga facendo clic sulle barre di scorrimento della griglia. Quando si aggiunge una nuova linea di riga o colonna per un pannello Griglia che include due o più colonne o righe, una barra degli strumenti ridotta viene visualizzata all'esterno della barra di scorrimento e permette di impostare esplicitamente la larghezza e l'altezza. La barra degli strumenti ridotta permette di configurare le opzioni di ridimensionamento per le righe e le colonne della griglia.

![Strumento decorativo griglia nella finestra di progettazione XAML](media/grid-adorner.png)

**Quadratini di ridimensionamento**

I quadratini di ridimensionamento vengono visualizzati sui controlli selezionati e ne permettono il ridimensionamento. Quando si ridimensiona un controllo, vengono in genere visualizzati i valori relativi a larghezza e altezza per semplificare il ridimensionamento del controllo. Per altre informazioni sulla modifica dei controlli nella visualizzazione **Progettazione**, vedere [Usare gli elementi nella finestra di progettazione XAML](../xaml-tools/working-with-elements-in-xaml-designer.md).

**Margini**

I margini rappresentano la quantità di spazio fisso tra il bordo di un controllo e il bordo del rispettivo contenitore. È possibile impostare i margini di un controllo usando le proprietà [Margin](xref:Windows.UI.Xaml.FrameworkElement.Margin) in **Layout** nella finestra **Proprietà**.

**Strumenti decorativi del margine**

È possibile usare gli strumenti decorativi del margine per modificare i margini di un elemento in relazione al rispettivo contenitore di layout. Se uno strumento decorativo del margine è aperto, il margine non viene impostato e viene visualizzata una catena interrotta. Se il margine non è impostato, gli elementi restano al proprio posto quando il contenitore di layout viene ridimensionato in fase di esecuzione. Se uno strumento decorativo del margine viene chiuso, viene visualizzata una catena ininterrotta e gli elementi vengono spostati insieme al margine quando il contenitore di layout viene ridimensionato in fase di esecuzione (il margine resta fisso).

**Handle degli elementi**

È possibile modificare un elemento usando i rispettivi handle visualizzati sulla tavola da disegno quando si sposta il puntatore sugli angoli della casella blu che circonda l'elemento. Gli handle consentono di ruotare, ridimensionare, capovolgere, spostare o aggiungere un raggio dell'angolo all'elemento. Il simbolo per l'handle dell'elemento varia in base alla funzione e cambia a seconda della posizione esatta del puntatore. Se gli handle non sono visibili, verificare che l'elemento sia selezionato.

Nella visualizzazione **Progettazione** sono disponibili comandi aggiuntivi della tavola da disegno nell'area inferiore sinistra della finestra, come illustrato di seguito:

![Comandi della visualizzazione Progettazione](media/xaml-design-view-controls.png)

Nella barra degli strumenti sono disponibili i comandi seguenti:

**Zoom**

Lo zoom consente di ridimensionare l'area di progettazione. È possibile ingrandire dal 12,5% all'800% o selezionare opzioni come **Adatta alla selezione** e **Adatta tutto**.

**Mostra/Nascondi griglia di allineamento**

Visualizza o nasconde la griglia di allineamento che mostra le griglie. Le griglie vengono usate quando è abilitato lo **snapping sulle linee della griglia** o lo **snapping sulle guide di allineamento**.

**Attiva/Disattiva allineamento alla griglia**

Se **l'allineamento alla griglia** è abilitato, un elemento tende ad allinearsi alle linee della griglia orizzontale e verticale più vicine quando lo si trascina sulla tavola da disegno.

**Attiva/Disattiva sfondo tavola da disegno**

Consente di passare da uno sfondo chiaro a uno scuro o viceversa.

**Attiva/Disattiva allineamento alle guide di allineamento**

Le guide di allineamento consentono di allineare i controlli l'uno rispetto all'altro. Se è abilitato l' **allineamento alle guide di allineamento** , quando si trascina un controllo in relazione ad altri controlli, vengono visualizzati i limiti di allineamento quando i bordi e il testo di alcuni controlli sono allineati orizzontalmente o verticalmente. Il limite di allineamento viene mostrato come una linea tratteggiata rossa.

**Disabilita il codice del progetto**

Disabilita [il codice del progetto](debugging-or-disabling-project-code-in-xaml-designer.md), ad esempio i controlli personalizzati e i convertitori di valori, e ricarica la finestra di progettazione.

### <a name="xaml-view"></a>Visualizzazione XAML

Nella visualizzazione **XAML**, la finestra contenente l'editor XAML è la finestra attiva e l'editor XAML è lo strumento di creazione primario. Il linguaggio Extensible Application Markup Language (XAML) fornisce un vocabolario dichiarativo basato su XML per la specifica dell'interfaccia utente di un'applicazione. La visualizzazione XAML include IntelliSense, la formattazione automatica, l'evidenziazione della sintassi e la navigazione tra tag. La figura seguente mostra la visualizzazione XAML con un menu di IntelliSense aperto:

![Visualizzazione XAML](media/xaml-editor.png)

## <a name="document-outline-window"></a>Finestra Struttura documento

La finestra Struttura documento in Visual Studio è simile alla finestra [Oggetti e sequenza temporale](creating-a-ui-by-using-blend-for-visual-studio.md#objects-and-timeline-window) in Blend per Visual Studio. Struttura documento consente di eseguire le attività seguenti:

- Visualizzare la struttura gerarchica di tutti gli elementi sulla tavola da disegno.

- Selezionare gli elementi in modo che sia possibile modificarli. Ad esempio, è possibile spostarli nella gerarchia o impostarne le proprietà nella Finestra Proprietà. Per altre informazioni, vedere [Usare gli elementi nella finestra di progettazione XAML](../xaml-tools/working-with-elements-in-xaml-designer.md).

- Creare e modificare modelli per gli elementi che sono controlli.

- [Crea animazioni](animate-objects-in-xaml-designer.md) (solo Blend per Visual Studio).

Per visualizzare la finestra Struttura documento in Visual Studio, sulla barra dei menu  >  **selezionare Visualizza altro Windows** Struttura  >  **documento**.
Per visualizzare la finestra Oggetti e sequenza temporale in Blend per Visual Studio, nella barra dei menu selezionare **Visualizza**  >  **struttura documento.**

![Finestra Struttura documento in Visual Studio](media/document-outline-window.png)

La visualizzazione principale nella finestra Struttura documento/Oggetti e sequenza temporale mostra la gerarchia di un documento in una struttura ad albero. È possibile usare la natura gerarchica della struttura documento per esaminare il documento con diversi livelli di dettaglio e per bloccare e nascondere gli elementi singolarmente o in gruppo. Le opzioni seguenti sono disponibili nella finestra Struttura documento/Oggetti e sequenza temporale documento:

**Mostra/Nascondi**

Visualizza o nasconde gli elementi della tavola da disegno. Appare come simbolo di un occhio quando gli elementi sono visualizzati. È anche possibile premere **CTRL** + **H** per nascondere un elemento e **MAIUSC** + **CTRL** + **H** per mostrarlo.

**Blocca/Sblocca**

Blocca o sblocca gli elementi della tavola da disegno. Gli elementi bloccati non possono essere modificati. Appare come simbolo di un lucchetto quando è applicato il blocco. È anche possibile premere **CTRL** + **L** per bloccare un elemento e **MAIUSC** + **CTRL** + **L** per sbloccarlo.

**Reimposta l'ambito pageRoot**

L'opzione nella parte superiore della finestra Struttura documento/Oggetti e sequenza temporale, che mostra un simbolo di freccia rivolta verso l'alto, consente di passare all'ambito precedente. Questa operazione può essere eseguita solo nell'ambito di uno stile o di un modello.

## <a name="properties-window"></a>Finestra Proprietà

La finestra **Proprietà** consente di impostare valori di proprietà sui controlli. Di seguito è riportata un'immagine di tale finestra:

![Finestra Proprietà](media/xaml-designer-properties-window.png)

Nella parte superiore della finestra **Proprietà** sono disponibili varie opzioni:

- È possibile modificare il nome dell'elemento selezionato nella casella **Nome**.
- Nell'angolo superiore sinistro è presente un'icona che rappresenta l'elemento selezionato.
- Per disporre le proprietà per categoria o in ordine alfabetico, fare clic su **Categoria**, **Nome** oppure **Origine** nell'elenco **Disponi per** .
- Per visualizzare l'elenco di eventi per un controllo, fare clic sul pulsante **Eventi**, identificato dal simbolo di un fulmine.
- Per cercare una proprietà, iniziare a digitare il nome corrispondente nella casella di ricerca. La finestra **Proprietà** mostra le proprietà corrispondenti alla ricerca durante la digitazione.

In alcuni casi è possibile impostare proprietà avanzate selezionando un pulsante Freccia GIÙ.

A destra di ogni valore di proprietà è presente un *marcatore della proprietà* , visualizzato sotto forma di simbolo di casella. L'aspetto del marcatore della proprietà indica se è presente un data binding o una risorsa applicata alla proprietà. Ad esempio, una casella bianca indica un valore predefinito, una casella nera indica che è stata applicata una risorsa locale e una casella arancione indica che è stato applicato un data binding. Quando si fa clic su questo marcatore, è possibile passare alla definizione di uno stile, aprire il generatore di data binding oppure aprire il selettore risorse.

Per altre informazioni sull'uso delle proprietà e sulla gestione degli eventi, vedere [Introduzione a controlli e modelli](/windows/uwp/design/controls-and-patterns/controls-and-events-intro).

## <a name="see-also"></a>Vedi anche

- [Usare gli elementi nella finestra di progettazione XAML](../xaml-tools/working-with-elements-in-xaml-designer.md)
- [Procedura per creare e applicare una risorsa](../xaml-tools/how-to-create-and-apply-a-resource.md)
- [Procedura dettagliata: Eseguire il binding ai dati nella finestra di progettazione XAML](../xaml-tools/walkthrough-binding-to-data-in-xaml-designer.md)
