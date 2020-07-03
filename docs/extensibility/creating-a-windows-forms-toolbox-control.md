---
title: Creazione di un controllo Windows Forms casella degli strumenti | Microsoft Docs
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- winforms
- toolbox
- windows forms
ms.assetid: 0be6ffc1-8afd-4d02-9a5d-e27dde05fde6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d7c4d14f2970f9d77e78fd90dd58efcdac100e4c
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903957"
---
# <a name="create-a-windows-forms-toolbox-control"></a>Creare un controllo della casella degli strumenti Windows Forms

Il modello di elemento di controllo della casella degli strumenti Windows Forms incluso nell'Visual Studio Extensibility Tools (VS SDK) consente di creare un controllo della **casella degli strumenti** che viene aggiunto automaticamente al momento dell'installazione dell'estensione. In questa procedura dettagliata viene illustrato come utilizzare il modello per creare un semplice controllo contatore che è possibile distribuire ad altri utenti.

## <a name="prerequisites"></a>Prerequisiti

A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. Viene inclusa come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare Visual Studio SDK in un secondo momento. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-the-toolbox-control"></a>Creare il controllo della casella degli strumenti

Il modello di controllo della casella degli strumenti Windows Forms crea un controllo utente non definito e fornisce tutte le funzionalità necessarie per aggiungere il controllo alla **casella degli strumenti**.

### <a name="create-an-extension-with-a-windows-forms-toolbox-control"></a>Creare un'estensione con un controllo della casella degli strumenti Windows Forms

1. Creare un progetto VSIX denominato `MyWinFormsControl` . È possibile trovare il modello di progetto VSIX nella finestra di dialogo **nuovo progetto** cercando "VSIX".

2. Quando si apre il progetto, aggiungere un modello di elemento di **controllo della casella degli strumenti Windows Forms** denominato `Counter` . Nella **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Aggiungi**  >  **nuovo elemento**. Nella finestra di dialogo **Aggiungi nuovo elemento** passare a **Visual C#**  >  **estendibilità** di Visual C# e selezionare **Windows Forms controllo della casella degli strumenti**

3. Viene aggiunto un controllo utente, un `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> per inserire il controllo nella **casella degli strumenti**e una voce di asset **Microsoft. VisualStudio. ToolboxControl** nel manifesto VSIX per la distribuzione.

### <a name="build-a-user-interface-for-the-control"></a>Creare un'interfaccia utente per il controllo

Il `Counter` controllo richiede due controlli figlio: un oggetto <xref:System.Windows.Forms.Label> per visualizzare il conteggio corrente e un oggetto <xref:System.Windows.Forms.Button> per reimpostare il conteggio su 0. Non sono necessari altri controlli figlio perché i chiamanti incrementeranno il contatore a livello di codice.

#### <a name="to-build-the-user-interface"></a>Per creare l'interfaccia utente

1. In **Esplora soluzioni**fare doppio clic su *Counter.cs* per aprirlo nella finestra di progettazione.

2. Rimuovere il **clic qui.** pulsante incluso per impostazione predefinita quando si aggiunge il modello di elemento di controllo della casella degli strumenti Windows Forms.

3. Dalla **casella degli strumenti**trascinare un `Label` controllo e quindi un `Button` controllo sotto di esso nell'area di progettazione.

4. Ridimensionare il controllo utente globale a 150, 50 pixel e ridimensionare il controllo Button in 50, 20 pixel.

5. Nella finestra **Proprietà** impostare i valori seguenti per i controlli nell'area di progettazione.

    |Control|Proprietà|valore|
    |-------------|--------------|-----------|
    |`Label1`|**Testo**|""|
    |`Button1`|**Nome**|btnReset|
    |`Button1`|**Testo**|Reset|

### <a name="code-the-user-control"></a>Codificare il controllo utente

Il `Counter` controllo esporrà un metodo per incrementare il contatore, un evento da generare ogni volta che il contatore viene incrementato, un pulsante di **reimpostazione** e tre proprietà per archiviare il conteggio corrente, il testo visualizzato e se mostrare o nascondere il pulsante di **reimpostazione** . L'attributo `ProvideToolboxControl` determina la posizione nella **casella degli strumenti** in cui verrà visualizzato il controllo `Counter` .

#### <a name="to-code-the-user-control"></a>Per codificare il controllo utente

1. Fare doppio clic sul form per aprire il relativo gestore eventi di caricamento nella finestra del codice.

2. Sopra il metodo del gestore dell'evento, nella classe del controllo creare un Integer per archiviare il valore del contatore e una stringa per archiviare il testo visualizzato, come illustrato nell'esempio seguente.

    ```csharp
    int currentValue;
    string displayText;
    ```

3. Creare le seguenti dichiarazioni di proprietà pubbliche.

    ```csharp
    public int Value {
        get { return currentValue; }
    }

    public string Message {
        get { return displayText; }
        set { displayText = value; }
    }

    public bool ShowReset {
        get { return btnReset.Visible; }
        set { btnReset.Visible = value; }
    }

    ```

    I chiamanti possono accedere a queste proprietà per ottenere e impostare il testo visualizzato del contatore e per mostrare o nascondere il pulsante di **reimpostazione** . I chiamanti possono ottenere il valore corrente della proprietà di sola lettura `Value` , ma non possono impostare direttamente il valore.

4. Inserire il codice seguente nell' `Load` evento per il controllo.

    ```csharp
    private void Counter_Load(object sender, EventArgs e)
    {
        currentValue = 0;
        label1.Text = Message + Value;
    }

    ```

    Impostando il testo dell' **etichetta** nell' <xref:System.Windows.Forms.UserControl.Load> evento, è possibile caricare le proprietà di destinazione prima di applicare i relativi valori. Se si imposta il testo dell' **etichetta** nel costruttore, verrà generata un' **etichetta**vuota.

5. Creare il metodo pubblico seguente per incrementare il contatore.

    ```csharp
    public void Increment()
    {
        currentValue++;
        label1.Text = displayText + Value;
        Incremented(this, EventArgs.Empty);
    }

    ```

6. Aggiungere una dichiarazione per l' `Incremented` evento alla classe del controllo.

    ```csharp
    public event EventHandler Incremented;
    ```

    I chiamanti possono aggiungere gestori a questo evento per rispondere alle modifiche nel valore del contatore.

7. Tornare alla visualizzazione progettazione e fare doppio clic sul pulsante **Reimposta** per generare il `btnReset_Click` gestore eventi, quindi compilarlo come illustrato nell'esempio seguente.

    ```csharp
    private void btnReset_Click(object sender, EventArgs e)
    {
        currentValue = 0;
        label1.Text = displayText + Value;
    }

    ```

8. Immediatamente sopra la definizione di classe, nella dichiarazione dell'attributo `ProvideToolboxControl` , modificare il valore del primo parametro da `"MyWinFormsControl.Counter"` a `"General"`. In questo modo si imposta il nome del gruppo di elementi che ospiterà il controllo nella **casella degli strumenti**.

    L'esempio seguente mostra l'attributo `ProvideToolboxControl` e la definizione di classe modificata.

    ```csharp
    [ProvideToolboxControl("General", false)]
    public partial class Counter : UserControl
    ```

### <a name="test-the-control"></a>Testare il controllo

 Per testare un controllo della **casella degli strumenti** , testarlo prima nell'ambiente di sviluppo e quindi testarlo in un'applicazione compilata.

#### <a name="to-test-the-control"></a>Per testare il controllo

1. Premere **F5** per **avviare il debug**.

    Questo comando Compila il progetto e apre una seconda istanza sperimentale di Visual Studio in cui è installato il controllo.

2. Nell'istanza sperimentale di Visual Studio creare un progetto di **applicazione Windows Forms** .

3. In **Esplora soluzioni**fare doppio clic su *Form1.cs* per aprirlo nella finestra di progettazione, se non è già aperto.

4. Nella **casella degli strumenti**il `Counter` controllo deve essere visualizzato nella sezione **generale** .

5. Trascinare un `Counter` controllo nel form, quindi selezionarlo. Le `Value` `Message` proprietà, e `ShowReset` verranno visualizzate nella finestra **Proprietà** , insieme alle proprietà ereditate da <xref:System.Windows.Forms.UserControl> .

6. Impostare la proprietà `Message` su `Count:`.

7. Trascinare un <xref:System.Windows.Forms.Button> controllo nel form, quindi impostare le proprietà nome e testo del pulsante su `Test` .

8. Fare doppio clic sul pulsante per aprire *Form1.cs* nella visualizzazione codice e creare un gestore di clic.

9. Nel gestore di clic chiamare `counter1.Increment()` .

10. Nella funzione del costruttore, dopo la chiamata a `InitializeComponent` , digitare `counter1``.``Incremented +=` e quindi premere **Tab** due volte.

    Visual Studio genera un gestore a livello di form per l' `counter1.Incremented` evento.

11. Evidenziare l' `Throw` istruzione nel gestore eventi, digitare `mbox` , quindi premere due volte **Tab** per generare una finestra di messaggio dal frammento di codice mbox.

12. Nella riga successiva aggiungere il `if` / `else` blocco seguente per impostare la visibilità del pulsante **Reimposta** .

    ```csharp
    if (counter1.Value < 5) counter1.ShowReset = false;
    else counter1.ShowReset = true;
    ```

13. Premere **F5**.

    Verrà visualizzato il modulo. Il `Counter` controllo Visualizza il testo seguente.

    **Conteggio: 0**

14. Fare clic su **Test**.

    Gli incrementi del contatore e Visual Studio visualizzano una finestra di messaggio.

15. Chiudere la finestra di messaggio.

    Il pulsante **Reimposta** viene visualizzato.

16. Fare clic su **test** finché il contatore non raggiunge la fine di **5** chiuse le finestre di messaggio ogni volta.

    Viene visualizzato nuovamente il pulsante **Reimposta** .

17. Fare clic su **Reimposta**.

    Il contatore viene reimpostato su **0**.

## <a name="next-steps"></a>Passaggi successivi

Quando si compila un controllo della **casella degli strumenti** , Visual Studio crea un file denominato *NomeProgetto. vsix* nella cartella \bin\debug\ del progetto. È possibile distribuire il controllo caricando il file *VSIX* in una rete o in un sito Web. Quando un utente apre il file *VSIX* , il controllo viene installato e aggiunto alla **casella degli strumenti** di Visual Studio nel computer dell'utente. In alternativa, è possibile caricare il file *VSIX* in [Visual Studio Marketplace](https://marketplace.visualstudio.com/) in modo che gli utenti possano trovarlo esplorando la finestra di dialogo **strumenti**  >  **estensioni e aggiornamenti** .

## <a name="see-also"></a>Vedere anche

- [Estendi altre parti di Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)
- [Creare un controllo della casella degli strumenti WPF](../extensibility/creating-a-wpf-toolbox-control.md)
- [Estendi altre parti di Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)
- [Nozioni di base sullo sviluppo del controllo Windows Forms](/dotnet/framework/winforms/controls/windows-forms-control-development-basics)
