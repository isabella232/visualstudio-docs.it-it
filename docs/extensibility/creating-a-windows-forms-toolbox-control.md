---
title: Creazione di un controllo della casella degli strumenti di Windows Form . Documenti Microsoft
ms.date: 3/16/2019
ms.topic: conceptual
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
ms.openlocfilehash: d7e7749302252c5d56f21c58de9b6ac23f898572
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739577"
---
# <a name="create-a-windows-forms-toolbox-control"></a>Creare un controllo della casella degli strumenti di Windows FormCreate a Windows Forms Toolbox Control

Il modello di elemento del controllo della casella degli strumenti di Windows Form incluso in Visual Studio Extensibility Tools (VS SDK), consente di creare un controllo **della casella degli strumenti** che viene aggiunto automaticamente quando viene installata l'estensione. In questa procedura dettagliata viene illustrato come utilizzare il modello per creare un semplice controllo contatore che è possibile distribuire ad altri utenti.

## <a name="prerequisites"></a>Prerequisiti

A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio.It is included as an optional feature in Visual Studio setup. È anche possibile installare l'SDK di VISUAL SMI in un secondo momento. Per ulteriori informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-the-toolbox-control"></a>Creare il controllo della casella degli strumentiCreate the Toolbox Control

Il modello di controllo della casella degli strumenti di Windows Form crea un controllo utente non definito e fornisce tutte le funzionalità necessarie per aggiungere il controllo alla **casella degli strumenti**.

### <a name="create-an-extension-with-a-windows-forms-toolbox-control"></a>Creare un'estensione con un controllo della casella degli strumenti di Windows FormCreate an extension with a Windows Forms Toolbox Control

1. Creare un progetto `MyWinFormsControl`VSIX denominato . È possibile trovare il modello di progetto VSIX nella finestra di dialogo **Nuovo progetto,** cercando "vsix".

2. Quando si apre il progetto, aggiungere un modello di elemento **Controllo della casella degli strumenti di Windows Form** denominato `Counter`. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nodo del progetto e **scegliere Aggiungi** > **nuovo elemento**. Nella finestra di dialogo **Aggiungi nuovo elemento,** passare **Windows Forms Toolbox Control** a**Estensibilità** **di Visual C** > 

3. In questo modo viene `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> aggiunto un controllo utente, un oggetto per inserire il controllo nella **casella degli strumenti**e una voce **Microsoft.VisualStudio.ToolboxControl** Asset nel manifesto VSIX per la distribuzione.

### <a name="build-a-user-interface-for-the-control"></a>Creare un'interfaccia utente per il controllo

Il `Counter` controllo richiede due <xref:System.Windows.Forms.Label> controlli figlio: a per <xref:System.Windows.Forms.Button> visualizzare il conteggio corrente e a per reimpostare il conteggio su 0. Non sono necessari altri controlli figlio perché i chiamanti incrementeranno il contatore a livello di codice.

#### <a name="to-build-the-user-interface"></a>Per creare l'interfaccia utente

1. In **Esplora soluzioni**fare doppio clic su *Counter.cs* per aprirlo nella finestra di progettazione.

2. Rimuovere il **Clicca qui !** che è incluso per impostazione predefinita quando si aggiunge il controllo della casella degli strumenti di Windows Form modello di elemento.

3. Dalla **Casella degli** `Label` strumenti trascinare `Button` un controllo e quindi un controllo sottostante nell'area di progettazione.

4. Ridimensiona il controllo utente complessivo a 150, 50 pixel e ridimensiona il controllo pulsante a 50, 20 pixel.

5. Nella finestra **Proprietà** impostare i valori seguenti per i controlli nell'area di progettazione.

    |Controllo|Proprietà|valore|
    |-------------|--------------|-----------|
    |`Label1`|**Testo**|""|
    |`Button1`|**Nome**|btnReset (informazioni in questo base opzioni)|
    |`Button1`|**Testo**|Reset|

### <a name="code-the-user-control"></a>Codificare il controllo utente

Il `Counter` controllo esporrà un metodo per incrementare il contatore, un evento da generare ogni volta che il contatore viene incrementato, un pulsante **Reimposta** e tre proprietà per archiviare il conteggio corrente, il testo visualizzato e se visualizzare o nascondere il pulsante **Reimposta.** L'attributo `ProvideToolboxControl` determina la posizione nella **casella degli strumenti** in cui verrà visualizzato il controllo `Counter` .

#### <a name="to-code-the-user-control"></a>Per codificare il controllo utente

1. Fare doppio clic sul form per aprire il relativo gestore eventi load nella finestra del codice.

2. Sopra il metodo del gestore eventi, nella classe del controllo creare un numero intero per archiviare il valore del contatore e una stringa per archiviare il testo visualizzato, come illustrato nell'esempio seguente.

    ```csharp
    int currentValue;
    string displayText;
    ```

3. Creare le seguenti dichiarazioni di proprietà pubblica.

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

    I chiamanti possono accedere a queste proprietà per ottenere e impostare il testo visualizzato del contatore e per visualizzare o nascondere il pulsante **Reimposta.** I chiamanti possono ottenere il valore `Value` corrente della proprietà di sola lettura, ma non possono impostare direttamente il valore.

4. Inserire il codice `Load` seguente nell'evento per il controllo.

    ```csharp
    private void Counter_Load(object sender, EventArgs e)
    {
        currentValue = 0;
        label1.Text = Message + Value;
    }

    ```

    L'impostazione del <xref:System.Windows.Forms.UserControl.Load> testo **Label** nell'evento consente alle proprietà di destinazione di essere caricate prima che i relativi valori vengano applicati. L'impostazione del testo **Label** nel costruttore comporterebbe un **oggetto Label**vuoto.

5. Creare il seguente metodo pubblico per incrementare il contatore.

    ```csharp
    public void Increment()
    {
        currentValue++;
        label1.Text = displayText + Value;
        Incremented(this, EventArgs.Empty);
    }

    ```

6. Aggiungere una dichiarazione per l'evento `Incremented` alla classe del controllo.

    ```csharp
    public event EventHandler Incremented;
    ```

    I chiamanti possono aggiungere gestori a questo evento per rispondere alle modifiche nel valore del contatore.

7. Tornare alla visualizzazione Progettazione e fare doppio `btnReset_Click` clic sul pulsante **Reimposta** per generare il gestore eventi, quindi compilarlo come illustrato nell'esempio seguente.

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

 Per testare un controllo **della casella degli strumenti,** testarlo prima nell'ambiente di sviluppo e quindi testarlo in un'applicazione compilata.

#### <a name="to-test-the-control"></a>Per testare il controllo

1. Premere **F5** per **avviare il debug**.

    Questo comando compila il progetto e apre una seconda istanza sperimentale di Visual Studio in cui è installato il controllo.

2. Nell'istanza sperimentale di Visual Studio creare un progetto **applicazione Windows Form.In** the Experimental instance of Visual Studio, create a Windows Forms Application project.

3. In **Esplora soluzioni**fare doppio clic su *Form1.cs* per aprirla nella finestra di progettazione, se non è già aperta.

4. Nella **Casella**degli `Counter` strumenti , il controllo deve essere visualizzato nella sezione **Generale** .

5. Trascinare `Counter` un controllo nel form e quindi selezionarlo. Le `Value` `Message`proprietà `ShowReset` , e verranno visualizzate nella finestra **Proprietà** insieme alle <xref:System.Windows.Forms.UserControl>proprietà ereditate da .

6. Impostare la proprietà `Message` su `Count:`.

7. Trascinare <xref:System.Windows.Forms.Button> un controllo nel form, quindi impostare il `Test`nome e le proprietà di testo del pulsante su .

8. Fare doppio clic sul pulsante per aprire *Form1.cs* nella visualizzazione codice e creare un gestore di clic.

9. Nel gestore clic `counter1.Increment()`chiamare .

10. Nella funzione costruttore, dopo `InitializeComponent`la `counter1``.``Incremented +=` chiamata a , digitare e quindi premere **TAB** due volte.

    Visual Studio genera un gestore `counter1.Incremented` a livello di form per l'evento.

11. Evidenziare `Throw` l'istruzione nel gestore eventi, digitare `mbox`, quindi premere **TAB** due volte per generare una finestra di messaggio dal frammento di codice mbox.

12. Nella riga successiva, aggiungere `if` / `else` il blocco seguente per impostare la visibilità del pulsante **Reimposta.**

    ```csharp
    if (counter1.Value < 5) counter1.ShowReset = false;
    else counter1.ShowReset = true;
    ```

13. Premere **F5**.

    Verrà aperto il modulo. Il `Counter` controllo visualizza il testo seguente.

    **Conteggio: 0Count: 0**

14. Fare clic su **Prova**.

    Il contatore aumenta e Visual Studio visualizza una finestra di messaggio.

15. Chiudere la finestra di messaggio.

    Il pulsante **Reimposta** scompare.

16. Fare clic su **Test** finché il contatore non raggiunge **5** chiudendo ogni volta le finestre di messaggio.

    Viene nuovamente visualizzato il pulsante **Reimposta.**

17. Fare clic su **Reimposta**.

    Il contatore viene reimpostato su **0**.

## <a name="next-steps"></a>Passaggi successivi

Quando si compila un controllo **della casella degli strumenti,** Visual Studio crea un file denominato *NomeProgetto.vsix* nella cartella del progetto. È possibile distribuire il controllo caricando il file *VSIX* in una rete o in un sito Web. Quando un utente apre il file *VSIX,* il controllo viene installato e aggiunto alla **casella degli strumenti** di Visual Studio nel computer dell'utente. In alternativa, è possibile caricare il file *Con estensione vsix* in [Visual Studio Marketplace](https://marketplace.visualstudio.com/) in modo che gli utenti possano trovarlo sfogliando nella finestra di dialogo**Estensioni e aggiornamenti** degli **strumenti.** > 

## <a name="see-also"></a>Vedere anche

- [Estendere altre parti di Visual StudioExtend other parts of Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)
- [Creare un controllo della casella degli strumenti WPFCreate a WPF Toolbox Control](../extensibility/creating-a-wpf-toolbox-control.md)
- [Estendere altre parti di Visual StudioExtend other parts of Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)
- [Nozioni di base sullo sviluppo di controlli Windows FormWindows Forms control development basics](/dotnet/framework/winforms/controls/windows-forms-control-development-basics)
