---
title: Esposizione di proprietà nella finestra proprietà | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], exposing in Property Browser
- properties [Visual Studio SDK]
- Property Browser, exposing properties
ms.assetid: 47f295b5-1ca5-4e7b-bb52-7b926b136622
caps.latest.revision: 37
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0b7b9e352c3042e5175b7420a9d4203ca7f59e7f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60117141"
---
# <a name="exposing-properties-to-the-properties-window"></a>Esposizione di proprietà nella finestra Proprietà
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa procedura dettagliata espone le proprietà pubbliche di un oggetto per il **proprietà** finestra. Le modifiche apportate a queste proprietà vengono riflesse nel **proprietà** finestra.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="exposing-properties-to-the-properties-window"></a>Esposizione di proprietà nella finestra Proprietà  
 In questa sezione si crea una finestra degli strumenti personalizzata e visualizzare le proprietà pubbliche dell'oggetto nel riquadro finestra associata la **proprietà** finestra.  
  
#### <a name="to-expose-properties-to-the-properties-window"></a>Per esporre le proprietà nella finestra proprietà  
  
1. Ogni estensione di Visual Studio inizia con un progetto di distribuzione VSIX che contiene gli asset di estensione. Creare un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] progetto VSIX denominato `MyObjectPropertiesExtension`. È possibile trovare il modello di progetto VSIX nel **nuovo progetto** nella finestra di dialogo **Visual c# / Extensibility**.  
  
2. Aggiungere una finestra degli strumenti tramite l'aggiunta di un modello di elemento di finestra degli strumenti personalizzata denominato `MyToolWindow`. Nel **Esplora soluzioni**, fare doppio clic sul nodo del progetto e selezionare **Aggiungi / nuovo elemento**. Nel **finestra di dialogo Aggiungi nuovo elemento**, passare a **elementi di Visual c# / Extensibility** e selezionare **finestra degli strumenti personalizzata**. Nel **Name** campo nella parte inferiore della finestra di dialogo, modificare il nome del file per `MyToolWindow.cs`. Per altre informazioni su come creare una finestra degli strumenti personalizzata, vedere [creazione di un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
3. Aprire MyToolWindow.cs e aggiungere la seguente istruzione using:  
  
    ```  
    using System.Collections;  
    using System.ComponentModel;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
4. A questo punto aggiungere i campi seguenti al `MyToolWindow` classe.  
  
    ```csharp  
    private ITrackSelection trackSel;  
    private SelectionContainer selContainer;  
  
    ```  
  
5. Aggiungere il codice seguente alla classe MyToolWindow.  
  
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
  
    public void UpdateSelection()  
    {  
        ITrackSelection track = TrackSelection;  
        if (track != null)  
            track.OnSelectChange((ISelectionContainer)selContainer);  
    }  
  
    public void SelectList(ArrayList list)  
    {  
        selContainer = new SelectionContainer(true, false);  
        selContainer.SelectableObjects = list;  
        selContainer.SelectedObjects = list;  
        UpdateSelection();  
    }  
  
    public override void OnToolWindowCreated()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(this);  
        SelectList(listObjects);  
    }  
    ```  
  
     Il `TrackSelection` utilizzata dalla proprietà `GetService` per ottenere un `STrackSelection` servizio, che offre un <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> interfaccia. Il `OnToolWindowCreated` gestore dell'evento e `SelectList` metodo creare contemporaneamente un elenco degli oggetti selezionati che contiene solo l'oggetto finestra degli strumenti riquadro stesso. Il `UpdateSelection` metodo indica il **proprietà** finestra per visualizzare le proprietà pubbliche del riquadro della finestra degli strumenti.  
  
6. Compilare il progetto e avviare il debug. L'istanza sperimentale di Visual Studio dovrebbe essere visualizzato.  
  
7. Se il **proprietà** finestra non è visibile, aprirlo premendo F4.  
  
8. Aprire il **MyToolWindow** finestra. È possibile trovarlo nel **Vista / Windows altri**.  
  
     Viene visualizzata la finestra e le proprietà pubbliche del riquadro della finestra vengono visualizzati nei **proprietà** finestra.  
  
9. Modifica il **didascalia** proprietà nel **proprietà** finestra **My le proprietà dell'oggetto**.  
  
     La didascalia della finestra MyToolWindow cambierà di conseguenza.  
  
## <a name="exposing-tool-window-properties"></a>Che espone proprietà della finestra degli strumenti  
 In questa sezione, aggiungere una finestra degli strumenti e le proprietà corrispondenti. Le modifiche apportate alle proprietà vengono riflesse nel **proprietà** finestra.  
  
#### <a name="to-expose-tool-window-properties"></a>Per esporre le proprietà della finestra degli strumenti  
  
1. Aprire MyToolWindow.cs e aggiungere la proprietà booleana pubblica IsChecked alla classe MyToolWindow.  
  
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
  
     Questa proprietà ottiene lo stato dalla casella di controllo WPF che si creerà in un secondo momento.  
  
2. Aprire MyToolWindowControl.xaml.cs e sostituire il costruttore MyToolWindowControl con il codice seguente.  
  
    ```vb  
    private MyToolWindow pane;  
    public MyToolWindowControl(MyToolWindow pane)  
    {  
        InitializeComponent();  
        this.pane = pane;  
        checkBox.IsChecked = false;  
    }  
    ```  
  
     In questo modo `MyToolWindowControl` l'accesso al `MyToolWindow` riquadro.  
  
3. In MyToolWindow.cs, modificare il `MyToolWindow` costruttore come illustrato di seguito:  
  
    ```csharp  
    base.Content = new MyToolWindowControl(this);  
    ```  
  
4. Modificare la visualizzazione progettazione del MyToolWindowControl.  
  
5. Eliminare il pulsante e aggiungere una casella di controllo dal **casella degli strumenti** nell'angolo superiore sinistro.  
  
6. Aggiungere gli eventi Checked e Unchecked. Selezionare la casella di controllo nella visualizzazione progettazione. Nel **proprietà** finestra, fare clic sul pulsante di gestori di eventi (nella parte superiore destra del **proprietà** finestra). Trovare **Checked** e digitare **checkbox_Checked** nella casella di testo, quindi individuare **Unchecked** e digitare **checkbox_Unchecked** nella casella di testo.  
  
7. Aggiungere i gestori di eventi di casella di controllo:  
  
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
  
9. Nell'istanza sperimentale, aprire il **MyToolWindow** finestra.  
  
     Cercare le proprietà della finestra di **proprietà** finestra. Il **IsChecked** proprietà viene visualizzata nella parte inferiore della finestra, sotto il **My Properties** categoria.  
  
10. Selezionare la casella di controllo nella **MyToolWindow** finestra. **IsChecked** nella **delle proprietà** finestra diventa **True**. Deselezionare la casella di controllo di **MyToolWindow** finestra. **IsChecked** nella **delle proprietà** finestra diventa **False**. Modificare il valore della **IsChecked** nel **proprietà** finestra. La casella di controllo di **MyToolWindow** finestra viene modificata in modo che corrisponda al nuovo valore.  
  
    > [!NOTE]
    >  Se è necessario eliminare l'oggetto che viene visualizzato nei **delle proprietà** finestra, chiamata `OnSelectChange` con un `null` contenitore a selezione prima. Dopo avere eliminato la proprietà o l'oggetto, è possibile modificare in un contenitore di selezione aggiornato <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A> e <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A> Elenca.  
  
## <a name="changing-selection-lists"></a>Modifica gli elenchi di selezione  
 In questa sezione si aggiunge un elenco di selezione per una classe di proprietà di base e consente di scegliere in quale elenco di selezione per visualizzare l'interfaccia della finestra degli strumenti.  
  
#### <a name="to-change-selection-lists"></a>Per modificare gli elenchi di selezione  
  
1. Aprire MyToolWindow.cs e aggiungere una classe pubblica denominata `Simple`.  
  
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
  
2. Aggiungere una proprietà SimpleObject a classe MyToolWindow, oltre a due metodi per passare il **delle proprietà** selezione delle finestre tra il riquadro della finestra e `Simple` oggetto.  
  
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
  
3. In su MyToolWindowControl.cs, sostituire i gestori di casella di controllo con queste righe di codice:  
  
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
  
5. Nell'istanza sperimentale, aprire il **MyToolWindow** finestra.  
  
6. Selezionare la casella di controllo di **MyToolWindow** finestra. Il **delle proprietà** finestra viene visualizzato il `Simple` le proprietà dell'oggetto **SomeText** e **ReadOnly**. Deselezionare la casella di controllo. Le proprietà pubbliche della finestra vengono visualizzati nei **proprietà** finestra.  
  
    > [!NOTE]
    >  Il nome visualizzato del **SomeText** viene **My Text**.  
  
## <a name="best-practice"></a>Procedure consigliate  
 In questa procedura dettagliata, <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> viene implementato in modo che la raccolta di oggetti selezionabili e la raccolta di oggetti selezionati sono nella stessa raccolta. Solo l'oggetto selezionato viene visualizzato nell'elenco Visualizzatore proprietà. Per un'implementazione di ISelectionContainer più completa, vedere gli esempi ToolWindow.  
  
 Finestre degli strumenti di Visual Studio vengono mantenute tra le sessioni di Visual Studio. Per altre informazioni sul salvataggio permanente lo stato della finestra degli strumenti, vedere <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>.  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione delle proprietà e della finestra Proprietà](../extensibility/extending-properties-and-the-property-window.md)
