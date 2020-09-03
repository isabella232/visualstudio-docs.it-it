---
title: Esposizione delle proprietà alla finestra Proprietà | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80711833"
---
# <a name="expose-properties-to-the-properties-window"></a>Esporre le proprietà al Finestra Proprietà

Questa procedura dettagliata espone le proprietà pubbliche di un oggetto alla finestra **Proprietà** . Le modifiche apportate a queste proprietà vengono riflesse nella finestra **Proprietà** .

## <a name="prerequisites"></a>Prerequisiti

A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. Viene inclusa come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare Visual Studio SDK in un secondo momento. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="expose-properties-to-the-properties-window"></a>Esporre le proprietà al Finestra Proprietà

In questa sezione si crea una finestra degli strumenti personalizzata e si visualizzano le proprietà pubbliche dell'oggetto riquadro finestra associato nella finestra **Proprietà** .

### <a name="to-expose-properties-to-the-properties-window"></a>Per esporre le proprietà al Finestra Proprietà

1. Ogni estensione di Visual Studio inizia con un progetto di distribuzione VSIX, che conterrà gli asset di estensione. Creare un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] progetto VSIX denominato `MyObjectPropertiesExtension` . È possibile trovare il modello di progetto VSIX nella finestra di dialogo **nuovo progetto** cercando "VSIX".

2. Aggiungere una finestra degli strumenti aggiungendo un modello di elemento della finestra degli strumenti personalizzato denominato `MyToolWindow` . Nella **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Aggiungi**  >  **nuovo elemento**. Nella finestra di **dialogo Aggiungi nuovo elemento**passare a **Visual C# elementi**  >  **estensibilità** e selezionare **finestra degli strumenti personalizzata**. Nel campo **nome** nella parte inferiore della finestra di dialogo modificare il nome del file in *MyToolWindow.cs*. Per ulteriori informazioni sulla creazione di una finestra degli strumenti personalizzata, vedere [creare un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md).

3. Aprire *MyToolWindow.cs* e aggiungere l'istruzione using seguente:

   ```csharp
   using System.Collections;
   using System.ComponentModel;
   using Microsoft.VisualStudio.Shell.Interop;
   ```

4. A questo punto aggiungere i campi seguenti alla `MyToolWindow` classe.

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

    La `TrackSelection` Proprietà USA `GetService` per ottenere un `STrackSelection` servizio che fornisce un' <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> interfaccia. Il `OnToolWindowCreated` gestore eventi e il `SelectList` Metodo creano insieme un elenco di oggetti selezionati che contiene solo l'oggetto riquadro della finestra degli strumenti. Il `UpdateSelection` metodo indica alla finestra **Proprietà** di visualizzare le proprietà pubbliche del riquadro della finestra degli strumenti.

6. Compilare il progetto e avviare il debug. Verrà visualizzata l'istanza sperimentale di Visual Studio.

7. Se la finestra **Proprietà** non è visibile, aprirla premendo **F4**.

8. Aprire la finestra **MyToolWindow** . È possibile trovarla in **Visualizza**  >  **altre finestre**.

    Viene visualizzata la finestra e le proprietà pubbliche del riquadro della finestra vengono visualizzate nella finestra **Proprietà** .

9. Modificare la proprietà **Caption** nella finestra **Proprietà** in **Proprietà oggetto**.

     Il titolo della finestra MyToolWindow viene modificato di conseguenza.

## <a name="expose-tool-window-properties"></a>Esporre le proprietà della finestra degli strumenti

In questa sezione si aggiunge una finestra degli strumenti ed espongono le relative proprietà. Le modifiche apportate alle proprietà vengono riflesse nella finestra **Proprietà** .

### <a name="to-expose-tool-window-properties"></a>Per esporre le proprietà della finestra degli strumenti

1. Aprire *MyToolWindow.cs*e aggiungere la proprietà booleana public sottoverificata alla `MyToolWindow` classe.

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

     Questa proprietà ottiene il proprio stato dalla casella di controllo WPF che verrà creata in un secondo momento.

2. Aprire *MyToolWindowControl.XAML.cs* e sostituire il costruttore MyToolWindowControl con il codice seguente.

    ```vb
    private MyToolWindow pane;
    public MyToolWindowControl(MyToolWindow pane)
    {
        InitializeComponent();
        this.pane = pane;
        checkBox.IsChecked = false;
    }
    ```

     Ciò consente `MyToolWindowControl` di accedere al `MyToolWindow` riquadro.

3. In *MyToolWindow.cs*modificare il `MyToolWindow` costruttore come segue:

    ```csharp
    base.Content = new MyToolWindowControl(this);
    ```

4. Passare alla visualizzazione progettazione di MyToolWindowControl.

5. Eliminare il pulsante e aggiungere una casella di controllo dalla **casella degli strumenti** nell'angolo superiore sinistro.

6. Aggiungere gli eventi Checked e unchecked. Selezionare la casella di controllo nella visualizzazione progettazione. Nella finestra **Proprietà** fare clic sul pulsante gestori eventi (nella parte superiore destra della finestra **Proprietà** ). Individuare **checked** e digitare **checkbox_Checked** nella casella di testo, quindi individuare **deselezionato** e digitare **checkbox_Unchecked** nella casella di testo.

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

9. Nell'istanza sperimentale aprire la finestra **MyToolWindow** .

     Cercare le proprietà della finestra nella finestra **Proprietà** . La proprietà **deselezionata** viene visualizzata nella parte inferiore della finestra, sotto la categoria **proprietà personali** .

10. Selezionare la casella di controllo nella finestra **MyToolWindow** . L' **opzione deselezionata** nella finestra **Proprietà** diventa **true**. Deselezionare la casella di controllo nella finestra **MyToolWindow** . L' **opzione deselezionata** nella finestra **Proprietà** diventa **false**. Modificare il valore di **Dechecked** nella finestra **Proprietà** . La casella di controllo nella finestra **MyToolWindow** viene modificata in modo che corrisponda al nuovo valore.

    > [!NOTE]
    > Se è necessario eliminare un oggetto visualizzato nella finestra **Proprietà** , chiamare `OnSelectChange` prima con un `null` contenitore di selezione. Dopo aver eliminato la proprietà o l'oggetto, è possibile passare a un contenitore di selezione che ha aggiornato gli <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A> <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A> elenchi e.

## <a name="change-selection-lists"></a>Modificare gli elenchi di selezione

 In questa sezione si aggiunge un elenco di selezione per una classe di proprietà di base e si utilizza l'interfaccia della finestra degli strumenti per scegliere quale elenco di selezione visualizzare.

### <a name="to-change-selection-lists"></a>Per modificare gli elenchi di selezione

1. Aprire *MyToolWindow.cs* e aggiungere una classe pubblica denominata `Simple` .

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

2. Aggiungere una `SimpleObject` proprietà alla `MyToolWindow` classe, oltre a due metodi per modificare la selezione della finestra **proprietà** tra il riquadro della finestra e l' `Simple` oggetto.

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

3. In *MyToolWindowControl.cs*sostituire i gestori della casella di controllo con queste righe di codice:

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

5. Nell'istanza sperimentale aprire la finestra **MyToolWindow** .

6. Selezionare la casella di controllo nella finestra **MyToolWindow** . Nella finestra **Proprietà** vengono visualizzate le `Simple` proprietà dell'oggetto **someText** e **ReadOnly**. Deselezionare la casella di controllo. Le proprietà pubbliche della finestra vengono visualizzate nella finestra **Proprietà** .

    > [!NOTE]
    > Il nome visualizzato di **someText** è il **testo**.

## <a name="best-practice"></a>Procedura consigliata

In questa procedura dettagliata, <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> viene implementato in modo che la raccolta di oggetti selezionabile e la raccolta di oggetti selezionati siano uguali. Nell'elenco Visualizzatore proprietà verrà visualizzato solo l'oggetto selezionato. Per un'implementazione ISelectionContainer più completa, vedere gli esempi Reference. ToolWindow.

Le finestre degli strumenti di Visual Studio vengono mantenute tra le sessioni di Visual Studio. Per ulteriori informazioni sulla permanenza dello stato della finestra degli strumenti, vedere <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> .

## <a name="see-also"></a>Vedere anche

- [Estendi proprietà e finestra delle proprietà](../extensibility/extending-properties-and-the-property-window.md)
