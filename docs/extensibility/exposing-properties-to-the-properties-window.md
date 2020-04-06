---
title: Esposizione delle proprietà alla finestra Proprietà Documenti Microsoft
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], exposing in Property Browser
- properties [Visual Studio SDK]
- Property Browser, exposing properties
ms.assetid: 47f295b5-1ca5-4e7b-bb52-7b926b136622
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f84962628ae550676e2c2eeb10c0f3baeca1bb58
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711833"
---
# <a name="expose-properties-to-the-properties-window"></a>Esporre le proprietà alla finestra Proprietà

In questa procedura dettagliata vengono esposte le proprietà pubbliche di un oggetto per il **proprietà** finestra. Le modifiche apportate a queste proprietà vengono riflesse nella finestra **Proprietà.The** changes you make to these properties are reflected in the Properties window.

## <a name="prerequisites"></a>Prerequisiti

A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio.It is included as an optional feature in Visual Studio setup. È anche possibile installare l'SDK di VISUAL SMI in un secondo momento. Per ulteriori informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="expose-properties-to-the-properties-window"></a>Esporre le proprietà alla finestra Proprietà

In questa sezione viene creata una finestra degli strumenti personalizzata e vengono visualizzate le proprietà pubbliche dell'oggetto riquadro finestra associato nella finestra **Proprietà.**

### <a name="to-expose-properties-to-the-properties-window"></a>Per esporre le proprietà alla finestra Proprietà

1. Ogni estensione di Visual Studio inizia con un progetto di distribuzione VSIX, che conterrà gli asset di estensione. Creare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] un progetto `MyObjectPropertiesExtension`VSIX denominato . È possibile trovare il modello di progetto VSIX nella finestra di dialogo **Nuovo progetto** cercando "vsix".

2. Aggiungere una finestra degli strumenti aggiungendo un `MyToolWindow`modello di elemento Finestra degli strumenti personalizzata denominato . In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nodo del progetto e **scegliere Aggiungi** > **nuovo elemento**. Nella finestra di **dialogo Aggiungi nuovo elemento**, passare a**Estensibilità** degli elementi > di **Visual C,** quindi selezionare **Finestra degli strumenti personalizzata**. Nel campo **Nome** nella parte inferiore della finestra di dialogo modificare il nome del file *in MyToolWindow.cs*. Per ulteriori informazioni su come creare una finestra degli strumenti personalizzata, vedere [Creare un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md).

3. Aprire MyToolWindow.cs e aggiungere l'istruzione using seguente:Open *MyToolWindow.cs* and add the following using statement:

   ```csharp
   using System.Collections;
   using System.ComponentModel;
   using Microsoft.VisualStudio.Shell.Interop;
   ```

4. Aggiungere ora i seguenti `MyToolWindow` campi alla classe.

   ```csharp
   private ITrackSelection trackSel;
   private SelectionContainer selContainer;

   ```

5. Aggiungere il codice seguente alla classe `MyToolWindow` .

   ```csharp
   private ITrackSelection TrackSelection
   {
       get
       {
           if (trackSel == null)
               trackSel =
                  GetService(typeof(STrackSelection)) as ITrackSelection;
           return trackSel;
       }
   }

   public void UpdateSelection()
   {
       ITrackSelection track = TrackSelection;
       if (track != null)
           track.OnSelectChange((ISelectionContainer)selContainer);
   }

   public void SelectList(ArrayList list)
   {
       selContainer = new SelectionContainer(true, false);
       selContainer.SelectableObjects = list;
       selContainer.SelectedObjects = list;
       UpdateSelection();
   }

   public override void OnToolWindowCreated()
   {
       ArrayList listObjects = new ArrayList();
       listObjects.Add(this);
       SelectList(listObjects);
   }
   ```

    La `TrackSelection` proprietà `GetService` utilizza `STrackSelection` per ottenere un <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> servizio, che fornisce un'interfaccia. Il `OnToolWindowCreated` gestore `SelectList` eventi e il metodo insieme creano un elenco di oggetti selezionati che contiene solo l'oggetto riquadro della finestra degli strumenti stesso. Il `UpdateSelection` metodo indica il **proprietà** finestra per visualizzare le proprietà pubbliche del riquadro della finestra degli strumenti.

6. Compilare il progetto e avviare il debug. Verrà visualizzata l'istanza sperimentale di Visual Studio.The experimental instance of Visual Studio should appear.

7. Se la finestra **Proprietà** non è visibile, aprirla premendo **F4**.

8. Aprire la finestra **MyToolWindow.** È possibile trovarlo in **Visualizza** > **altre finestre**.

    Viene visualizzata la finestra in cui le proprietà pubbliche del riquadro della finestra vengono visualizzate nella finestra **Proprietà.**

9. Modificare la proprietà **Didascalia** nella finestra **Proprietà** in **Proprietà oggetto**personale .

     La didascalia della finestra MyToolWindow cambia di conseguenza.

## <a name="expose-tool-window-properties"></a>Esporre le proprietà della finestra degli strumenti

In questa sezione si aggiunge una finestra degli strumenti e ne vengono esposte le proprietà. Le modifiche apportate alle proprietà vengono riflesse nella finestra **Proprietà.The** changes you make to properties are reflected in the Properties window.

### <a name="to-expose-tool-window-properties"></a>Per esporre le proprietà della finestra degli strumenti

1. Aprire *MyToolWindow.cs*e aggiungere la proprietà booleana pubblica IsChecked alla `MyToolWindow` classe .

    ```csharp
    [Category("My Properties")]
    [Description("MyToolWindowControl properties")]
    public bool IsChecked
    {
        get {
            if (base.Content == null)  return false;
            return (bool)(( MyToolWindowControl) base.Content).checkBox.IsChecked;
        }
        set {
            ((MyToolWindowControl) base.Content).checkBox.IsChecked = value;
        }
    }
    ```

     Questa proprietà ottiene il relativo stato dalla casella di controllo WPFWPF che verrà creata in un secondo momento.

2. Aprire *MyToolWindowControl.xaml.cs* e sostituire il costruttore MyToolWindowControl con il codice seguente.

    ```vb
    private MyToolWindow pane;
    public MyToolWindowControl(MyToolWindow pane)
    {
        InitializeComponent();
        this.pane = pane;
        checkBox.IsChecked = false;
    }
    ```

     In `MyToolWindowControl` questo modo `MyToolWindow` si accede al riquadro.

3. In *MyToolWindow.cs*modificare `MyToolWindow` il costruttore come segue:

    ```csharp
    base.Content = new MyToolWindowControl(this);
    ```

4. Passare alla visualizzazione Progettazione di MyToolWindowControl.

5. Eliminare il pulsante e aggiungere una casella di controllo dalla **Casella degli strumenti** nell'angolo superiore sinistro.

6. Aggiungere gli eventi Checked e Unchecked. Selezionare la casella di controllo nella vista Progettazione. Nella finestra **Proprietà** fare clic sul pulsante dei gestori eventi (nella parte superiore destra della finestra **Proprietà).** Trova **Selezionato** e digita **checkbox_Checked** nella casella di testo, quindi trova **Deselezionato** e digita **checkbox_Unchecked** nella casella di testo.

7. Aggiungere i gestori eventi della casella di controllo:

    ```csharp
    private void checkbox_Checked(object sender, RoutedEventArgs e)
    {
        pane.IsChecked = true;
        pane.UpdateSelection();
    }
    private void checkbox_Unchecked(object sender, RoutedEventArgs e)
    {
        pane.IsChecked = false;
        pane.UpdateSelection();
    }
    ```

8. Compilare il progetto e avviare il debug.

9. Nell'istanza sperimentale aprire la finestra **MyToolWindow.**

     Cercare le proprietà della finestra nella finestra **Proprietà.Look** for the window's properties in the Properties window. La proprietà **IsChecked** viene visualizzata nella parte inferiore della finestra, nella categoria **Proprietà personali.**

10. Selezionare la casella di controllo nella finestra **MyToolWindow.** **IsChecked** nella finestra **Proprietà** viene modificata in **True**. Deselezionare la casella di controllo nella finestra **MyToolWindow.** **IsChecked** nella finestra **Proprietà** diventa **False**. Modificare il valore di **IsChecked** nella finestra **Proprietà.** La casella di controllo nella finestra **MyToolWindow** cambia in base al nuovo valore.

    > [!NOTE]
    > Se è necessario eliminare un oggetto visualizzato nella finestra `OnSelectChange` **Proprietà,** chiamare prima con un `null` contenitore di selezione. Dopo aver eliminato la proprietà o l'oggetto, è <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A> <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A> possibile passare a un contenitore di selezione che è stato aggiornato ed elencato.

## <a name="change-selection-lists"></a>Modificare gli elenchi di selezione

 In questa sezione si aggiunge un elenco di selezione per una classe di proprietà di base e si utilizza l'interfaccia della finestra degli strumenti per scegliere l'elenco di selezione da visualizzare.

### <a name="to-change-selection-lists"></a>Per modificare gli elenchi di selezione

1. Aprire *MyToolWindow.cs* e aggiungere `Simple`una classe pubblica denominata .

    ```csharp
    public class Simple
    {
        private string someText = "";

        [Category("My Properties")]
        [Description("Simple Properties")]
        [DisplayName("My Text")]
        public string SomeText
        {
            get { return someText; }
            set { someText = value; }
        }

        [Category("My Properties")]
        [Description("Read-only property")]
        public bool ReadOnly
        {
            get { return false; }
        }
    }
    ```

2. Aggiungere `SimpleObject` una proprietà `MyToolWindow` alla classe, oltre a due metodi per passare `Simple` la selezione della finestra **Proprietà** tra il riquadro della finestra e l'oggetto.

    ```csharp
    private Simple simpleObject = null;
    public Simple SimpleObject
    {
        get
        {
            if (simpleObject == null) simpleObject = new Simple();
            return simpleObject;
        }
    }

    public void SelectSimpleList()
    {
        ArrayList listObjects = new ArrayList();
        listObjects.Add(SimpleObject);
        SelectList(listObjects);
    }

    public void SelectThisList()
    {
        ArrayList listObjects = new ArrayList();
        listObjects.Add(this);
        SelectList(listObjects);
    }
    ```

3. In *MyToolWindowControl.cs*sostituire i gestori di caselle di controllo con le seguenti righe di codice:

    ```csharp
    private void checkbox_Checked(object sender, RoutedEventArgs e)
     {
        pane.IsChecked = true;
        pane.SelectSimpleList();
        pane.UpdateSelection();
    }
    private void checkbox_Unchecked(object sender, RoutedEventArgs e)
    {
        pane.IsChecked = false;
        pane.SelectThisList();
        pane.UpdateSelection();
    }
    ```

4. Compilare il progetto e avviare il debug.

5. Nell'istanza sperimentale aprire la finestra **MyToolWindow.**

6. Selezionare la casella di controllo nella finestra **MyToolWindow.** Nella **Properties** finestra Proprietà `Simple` vengono visualizzate le proprietà dell'oggetto, **SomeText** e **ReadOnly**. Deselezionare la casella di controllo. Le proprietà pubbliche della finestra vengono visualizzate nella finestra **Proprietà.**

    > [!NOTE]
    > Il nome visualizzato di **SomeText** è **My Text**.

## <a name="best-practice"></a>Procedura consigliata

In questa <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> procedura dettagliata, viene implementata in modo che la raccolta di oggetti selezionabili e la raccolta di oggetti selezionati siano la stessa raccolta. Nell'elenco Visualizzatore proprietà viene visualizzato solo l'oggetto selezionato. Per un'implementazione più completa di ISelectionContainer, vedere gli esempi Reference.ToolWindow.For a more complete ISelectionContainer implementation, see the Reference.ToolWindow samples.

Finestre degli strumenti di Visual Studio persistono tra le sessioni di Visual Studio.Visual Studio tool windows persist between Visual Studio sessions. Per ulteriori informazioni sulla persistenza dello <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>stato della finestra degli strumenti, vedere .

## <a name="see-also"></a>Vedere anche

- [Estendere le proprietà e la finestra ProprietàExtend properties and the Property window](../extensibility/extending-properties-and-the-property-window.md)
