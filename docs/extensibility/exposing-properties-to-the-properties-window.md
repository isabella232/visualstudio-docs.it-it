---
title: Esposizione di proprietà alla finestra Proprietà | Microsoft Docs
description: Informazioni sulle proprietà pubbliche di un oggetto. Le modifiche apportate a queste proprietà si riflettono nella Finestra Proprietà.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- properties [Visual Studio SDK], exposing in Property Browser
- properties [Visual Studio SDK]
- Property Browser, exposing properties
ms.assetid: 47f295b5-1ca5-4e7b-bb52-7b926b136622
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 957a6445934d9d3af7cb0f9d61b72171d48521755a1ff9ff4410b31fbe9893a4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121388695"
---
# <a name="expose-properties-to-the-properties-window"></a>Esporre le proprietà al Finestra Proprietà

Questa procedura dettagliata espone le proprietà pubbliche di un oggetto alla **finestra** Proprietà. Le modifiche apportate a queste proprietà si riflettono nella **finestra** Proprietà.

## <a name="prerequisites"></a>Prerequisiti

A partire Visual Studio 2015, non si installa Visual Studio SDK dall'Area download. È incluso come funzionalità facoltativa nell'Visual Studio configurazione. È anche possibile installare VS SDK in un secondo momento. Per altre informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="expose-properties-to-the-properties-window"></a>Esporre le proprietà al Finestra Proprietà

In questa sezione viene creata una finestra degli strumenti personalizzata e vengono visualizzate le proprietà pubbliche dell'oggetto riquadro della finestra associato nella **finestra** Proprietà.

### <a name="to-expose-properties-to-the-properties-window"></a>Per esporre le proprietà al Finestra Proprietà

1. Ogni Visual Studio'estensione inizia con un progetto di distribuzione VSIX, che conterrà gli asset di estensione. Creare un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] progetto VSIX denominato `MyObjectPropertiesExtension` . È possibile trovare il modello di progetto VSIX nella finestra **di dialogo Project** ricerca di "vsix".

2. Aggiungere una finestra degli strumenti aggiungendo un modello di elemento della finestra degli strumenti personalizzato denominato `MyToolWindow` . Nella finestra di **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo del progetto e **scegliere Aggiungi**  >  **nuovo elemento.** Nella finestra **di dialogo Aggiungi nuovo elemento** passare a Estendibilità degli elementi di **Visual C#** e selezionare Finestra degli strumenti  >   **personalizzata.** Nel campo **Nome** nella parte inferiore della finestra di dialogo modificare il nome del file in *MyToolWindow.cs*. Per altre informazioni su come creare una finestra degli strumenti personalizzata, vedere [Creare un'estensione con una finestra degli strumenti.](../extensibility/creating-an-extension-with-a-tool-window.md)

3. Aprire *MyToolWindow.cs e* aggiungere l'istruzione using seguente:

   ```csharp
   using System.Collections;
   using System.ComponentModel;
   using Microsoft.VisualStudio.Shell.Interop;
   ```

4. Aggiungere ora i campi seguenti alla `MyToolWindow` classe .

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

    La `TrackSelection` proprietà utilizza per ottenere un servizio che fornisce `GetService` `STrackSelection` <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> un'interfaccia . Il `OnToolWindowCreated` gestore eventi e il metodo creano insieme un elenco di oggetti selezionati che contiene solo `SelectList` l'oggetto riquadro della finestra degli strumenti stesso. Il `UpdateSelection` metodo indica alla finestra **Proprietà** di visualizzare le proprietà pubbliche del riquadro della finestra degli strumenti.

6. Compilare il progetto e avviare il debug. Verrà visualizzata l'istanza Visual Studio sperimentale.

7. Se la **finestra** Proprietà non è visibile, aprirla premendo **F4.**

8. Aprire la **finestra MyToolWindow.** È possibile trovarlo in **Visualizza**  >  **altro Windows**.

    La finestra si apre e le proprietà pubbliche del riquadro della finestra vengono visualizzate nella **finestra** Proprietà.

9. Modificare la **proprietà Caption** nella **finestra Proprietà** in My **Object Properties**.

     La didascalia della finestra MyToolWindow cambia di conseguenza.

## <a name="expose-tool-window-properties"></a>Esporre le proprietà della finestra degli strumenti

In questa sezione si aggiunge una finestra degli strumenti e si espongono le relative proprietà. Le modifiche apportate alle proprietà si riflettono nella **finestra** Proprietà.

### <a name="to-expose-tool-window-properties"></a>Per esporre le proprietà della finestra degli strumenti

1. Aprire *MyToolWindow.cs* e aggiungere la proprietà booleana pubblica IsChecked alla `MyToolWindow` classe .

    ```csharp
    [Category("My Properties")]
    [Description("MyToolWindowControl properties")]
    public bool IsChecked
    {
        get {
            if (base.Content == null)  return false;
            return (bool)(( MyToolWindowControl) base.Content).checkBox.IsChecked;
        }
        set {
            ((MyToolWindowControl) base.Content).checkBox.IsChecked = value;
        }
    }
    ```

     Questa proprietà ottiene lo stato dalla casella di controllo WPF che verrà creata in un secondo momento.

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

     In questo modo `MyToolWindowControl` è possibile accedere al `MyToolWindow` riquadro.

3. In *MyToolWindow.cs* modificare il `MyToolWindow` costruttore come segue:

    ```csharp
    base.Content = new MyToolWindowControl(this);
    ```

4. Passare alla visualizzazione progettazione di MyToolWindowControl.

5. Eliminare il pulsante e aggiungere una casella di controllo dalla Casella **degli strumenti** nell'angolo superiore sinistro.

6. Aggiungere gli eventi Checked e Unchecked. Selezionare la casella di controllo nella visualizzazione Progettazione. Nella finestra **Proprietà** fare clic sul pulsante gestori eventi in alto a destra nella **finestra** Proprietà. Trovare **Selezionato** e digitare **checkbox_Checked** nella casella di  testo, quindi trovare Deselezionato **e** digitare checkbox_Unchecked nella casella di testo.

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

9. Nell'istanza sperimentale aprire la **finestra MyToolWindow.**

     Cercare le proprietà della finestra nella **finestra** Proprietà. La **proprietà IsChecked** viene visualizzata nella parte inferiore della finestra, nella **categoria Proprietà.**

10. Selezionare la casella di controllo nella **finestra MyToolWindow.** **IsChecked** nella **finestra Proprietà** viene modificato in **True.** Deselezionare la casella di controllo **nella finestra MyToolWindow.** **IsChecked** nella finestra **Proprietà** viene modificato in **False.** Modificare il valore **di IsChecked** nella **finestra** Proprietà. La casella di controllo nella **finestra MyToolWindow** cambia in modo da corrispondere al nuovo valore.

    > [!NOTE]
    > Se è necessario eliminare un oggetto visualizzato  nella finestra Proprietà, chiamare prima con `OnSelectChange` un `null` contenitore di selezione. Dopo aver esposto la proprietà o l'oggetto , è possibile passare a un contenitore di selezione con elenchi <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A> e <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A> aggiornati.

## <a name="change-selection-lists"></a>Modificare gli elenchi di selezione

 In questa sezione si aggiunge un elenco di selezione per una classe di proprietà di base e si usa l'interfaccia della finestra degli strumenti per scegliere l'elenco di selezione da visualizzare.

### <a name="to-change-selection-lists"></a>Per modificare gli elenchi di selezione

1. Aprire *MyToolWindow.cs* e aggiungere una classe pubblica denominata `Simple` .

    ```csharp
    public class Simple
    {
        private string someText = "";

        [Category("My Properties")]
        [Description("Simple Properties")]
        [DisplayName("My Text")]
        public string SomeText
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

2. Aggiungere una proprietà alla classe e due metodi per alternare la selezione della finestra Proprietà tra `SimpleObject` il riquadro della finestra e `MyToolWindow` l'oggetto  `Simple` .

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

3. In *MyToolWindowControl.cs* sostituire i gestori delle caselle di controllo con queste righe di codice:

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

5. Nell'istanza sperimentale aprire la **finestra MyToolWindow.**

6. Selezionare la casella di controllo nella **finestra MyToolWindow.** Nella **finestra Proprietà** vengono visualizzate le proprietà `Simple` dell'oggetto, **SomeText** e **ReadOnly.** Deselezionare la casella di controllo. Le proprietà pubbliche della finestra vengono visualizzate nella **finestra** Proprietà.

    > [!NOTE]
    > Il nome visualizzato di **SomeText** è **My Text.**

## <a name="best-practice"></a>Procedura consigliata

In questa procedura dettagliata viene implementato in modo che la raccolta di oggetti selezionabili e la raccolta di <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> oggetti selezionati siano la stessa raccolta. Nell'elenco Visualizzatore proprietà viene visualizzato solo l'oggetto selezionato. Per un'implementazione più completa di ISelectionContainer, vedi gli esempi reference.ToolWindow.

Visual Studio le finestre degli strumenti vengono mantenute tra Visual Studio sessioni. Per altre informazioni sulla persistenza dello stato della finestra degli strumenti, vedere <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> .

## <a name="see-also"></a>Vedi anche

- [Estendere le proprietà e la finestra Proprietà](../extensibility/extending-properties-and-the-property-window.md)
