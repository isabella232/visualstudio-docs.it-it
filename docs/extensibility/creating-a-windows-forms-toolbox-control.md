---
title: Creazione di un controllo Windows form della casella degli strumenti | Microsoft Docs
description: Questa procedura dettagliata illustra come usare il modello Windows Form Toolbox Control per creare un semplice controllo contatore usando Visual Studio SDK.
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- winforms
- toolbox
- windows forms
ms.assetid: 0be6ffc1-8afd-4d02-9a5d-e27dde05fde6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: f7937c3e78a9f9d113fa3394a7d7be948a22059e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122089719"
---
# <a name="create-a-windows-forms-toolbox-control"></a>Creare un controllo della casella Windows Form

Il modello di elemento Windows Forms Toolbox Control incluso negli strumenti di estendibilità  di Visual Studio (VS SDK) consente di creare un controllo della casella degli strumenti che viene aggiunto automaticamente quando viene installata l'estensione. Questa procedura dettagliata illustra come usare il modello per creare un semplice controllo contatore che è possibile distribuire ad altri utenti.

## <a name="prerequisites"></a>Prerequisiti

A partire Visual Studio 2015, non si installa Visual Studio SDK dall'Area download. È incluso come funzionalità facoltativa nella configurazione Visual Studio configurazione. È anche possibile installare VS SDK in un secondo momento. Per altre informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-the-toolbox-control"></a>Creare il controllo della casella degli strumenti

Il modello Windows Form Toolbox Control crea un controllo utente non definito e fornisce tutte le funzionalità necessarie per aggiungere il controllo alla casella **degli strumenti**.

### <a name="create-an-extension-with-a-windows-forms-toolbox-control"></a>Creare un'estensione con un controllo della casella Windows Form

1. Creare un progetto VSIX denominato `MyWinFormsControl` . È possibile trovare il modello di progetto VSIX nella finestra **di dialogo Nuovo Project,** cercando "vsix".

2. Quando si apre il progetto, aggiungere un modello di **elemento Windows Form Toolbox Control** denominato `Counter` . Nella finestra **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo del progetto e **scegliere Aggiungi**  >  **nuovo elemento**. Nella finestra **di dialogo Aggiungi nuovo elemento** passare a **Estendibilità di Visual C#** e selezionare Windows  >   Controllo casella degli **strumenti Form**

3. Vengono aggiunti un controllo utente, un oggetto per inserire il controllo nella casella degli strumenti e una voce `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> **asset Microsoft.VisualStudio.ToolboxControl** nel manifesto VSIX per la distribuzione.

### <a name="build-a-user-interface-for-the-control"></a>Creare un'interfaccia utente per il controllo

Il controllo richiede due controlli figlio: un per visualizzare il conteggio corrente e un oggetto per `Counter` <xref:System.Windows.Forms.Label> reimpostare il <xref:System.Windows.Forms.Button> conteggio su 0. Non sono necessari altri controlli figlio perché i chiamanti incrementeranno il contatore a livello di codice.

#### <a name="to-build-the-user-interface"></a>Per creare l'interfaccia utente

1. In **Esplora soluzioni** fare doppio clic su *Counter.cs* per aprirlo nella finestra di progettazione.

2. Rimuovere **l'elemento Click Here !** pulsante incluso per impostazione predefinita quando si aggiunge il modello di elemento Windows Form Toolbox Control.

3. Dalla Casella **degli strumenti** trascinare un controllo e quindi un controllo sotto di `Label` esso `Button` nell'area di progettazione.

4. Ridimensionare il controllo utente complessivo a 150, 50 pixel e ridimensionare il controllo pulsante a 50, 20 pixel.

5. Nella finestra **Proprietà** impostare i valori seguenti per i controlli nell'area di progettazione.

    |Controllo|Proprietà|Valore|
    |-------------|--------------|-----------|
    |`Label1`|**Text**|""|
    |`Button1`|**Nome**|btnReset|
    |`Button1`|**Text**|Reset|

### <a name="code-the-user-control"></a>Codificare il controllo utente

Il controllo esporrà un metodo per incrementare il contatore, un evento da generato ogni volta che il contatore viene incrementato, un pulsante Reimposta e tre proprietà per archiviare il conteggio corrente, il testo visualizzato e se visualizzare o nascondere il `Counter` **pulsante Reimposta.**  L'attributo `ProvideToolboxControl` determina la posizione nella **casella degli strumenti** in cui verrà visualizzato il controllo `Counter` .

#### <a name="to-code-the-user-control"></a>Per codificare il controllo utente

1. Fare doppio clic sul form per aprire il relativo gestore eventi di caricamento nella finestra del codice.

2. Sopra il metodo del gestore eventi, nella classe di controllo creare un numero intero per archiviare il valore del contatore e una stringa per archiviare il testo visualizzato, come illustrato nell'esempio seguente.

    ```csharp
    int currentValue;
    string displayText;
    ```

3. Creare le dichiarazioni di proprietà pubbliche seguenti.

    ```csharp
    public int Value {
        get { return currentValue; }
    }

    public string Message {
        get { return displayText; }
        set { displayText = value; }
    }

    public bool ShowReset {
        get { return btnReset.Visible; }
        set { btnReset.Visible = value; }
    }

    ```

    I chiamanti possono accedere a queste proprietà per ottenere e impostare il testo visualizzato del contatore e per visualizzare o nascondere il **pulsante** Reimposta. I chiamanti possono ottenere il valore corrente della proprietà di sola `Value` lettura, ma non possono impostare direttamente il valore.

4. Inserire il codice seguente `Load` nell'evento per il controllo .

    ```csharp
    private void Counter_Load(object sender, EventArgs e)
    {
        currentValue = 0;
        label1.Text = Message + Value;
    }

    ```

    **L'impostazione del testo** etichetta nell'evento consente il caricamento delle proprietà di destinazione prima <xref:System.Windows.Forms.UserControl.Load> dell'applicazione dei relativi valori. **L'impostazione del** testo Etichetta nel costruttore comporta un'etichetta **vuota.**

5. Creare il metodo pubblico seguente per incrementare il contatore.

    ```csharp
    public void Increment()
    {
        currentValue++;
        label1.Text = displayText + Value;
        Incremented(this, EventArgs.Empty);
    }

    ```

6. Aggiungere una dichiarazione per `Incremented` l'evento alla classe del controllo.

    ```csharp
    public event EventHandler Incremented;
    ```

    I chiamanti possono aggiungere gestori a questo evento per rispondere alle modifiche nel valore del contatore.

7. Tornare alla visualizzazione Progettazione e fare doppio clic sul **pulsante Reimposta** per generare il `btnReset_Click` gestore eventi. Quindi, compilarlo come illustrato nell'esempio seguente.

    ```csharp
    private void btnReset_Click(object sender, EventArgs e)
    {
        currentValue = 0;
        label1.Text = displayText + Value;
    }

    ```

8. Immediatamente sopra la definizione di classe, nella dichiarazione dell'attributo `ProvideToolboxControl` , modificare il valore del primo parametro da `"MyWinFormsControl.Counter"` a `"General"`. In questo modo si imposta il nome del gruppo di elementi che ospiterà il controllo nella **casella degli strumenti**.

    L'esempio seguente mostra l'attributo `ProvideToolboxControl` e la definizione di classe modificata.

    ```csharp
    [ProvideToolboxControl("General", false)]
    public partial class Counter : UserControl
    ```

### <a name="test-the-control"></a>Testare il controllo

 Per testare un **controllo della casella** degli strumenti, testarlo prima nell'ambiente di sviluppo e quindi testarlo in un'applicazione compilata.

#### <a name="to-test-the-control"></a>Per testare il controllo

1. Premere **F5 per** **avviare il debug.**

    Questo comando compila il progetto e apre una seconda istanza sperimentale di Visual Studio in cui è installato il controllo .

2. Nell'istanza sperimentale di Visual Studio creare un **progetto Windows'applicazione Form.**

3. In **Esplora soluzioni** fare doppio clic su *Form1.cs* per aprirlo nella finestra di progettazione, se non è già aperto.

4. Nella casella **degli strumenti** il controllo deve essere visualizzato `Counter` nella **sezione** Generale.

5. Trascinare `Counter` un controllo nel form e quindi selezionarlo. Le proprietà , e verranno visualizzate nella finestra Proprietà , insieme alle proprietà `Value` `Message` `ShowReset` ereditate da  <xref:System.Windows.Forms.UserControl> .

6. Impostare la proprietà `Message` su `Count:`.

7. Trascinare un controllo nel form e quindi impostare le proprietà del nome e <xref:System.Windows.Forms.Button> del testo del pulsante su `Test` .

8. Fare doppio clic sul pulsante per aprire *Form1.cs* nella visualizzazione codice e creare un gestore clic.

9. Nel gestore di clic chiamare `counter1.Increment()` .

10. Nella funzione costruttore, dopo la chiamata a `InitializeComponent` , digitare e quindi premere TAB `counter1``.``Incremented +=` **due** volte.

    Visual Studio genera un gestore a livello di form per `counter1.Incremented` l'evento .

11. Evidenziare l'istruzione nel gestore eventi, digitare e quindi premere TAB due volte per generare una finestra di messaggio dal frammento di codice `Throw` `mbox` mbox. 

12. Nella riga successiva aggiungere il blocco seguente `if` / `else` per impostare la visibilità del **pulsante** Reimposta.

    ```csharp
    if (counter1.Value < 5) counter1.ShowReset = false;
    else counter1.ShowReset = true;
    ```

13. Premere **F5**.

    Verrà aperto il modulo. Il `Counter` controllo visualizza il testo seguente.

    **Conteggio: 0**

14. Selezionare **Test**.

    Il contatore incrementa e Visual Studio viene visualizzata una finestra di messaggio.

15. Chiudere la finestra di messaggio.

    Il **pulsante** Reimposta scompare.

16. Selezionare **Test** fino a quando il contatore non raggiunge **5** chiudendo ogni volta le finestre di messaggio.

    Viene **nuovamente** fatto clic sul pulsante Reimposta.

17. Selezionare **Reimposta**.

    Il contatore viene reimpostato su **0.**

## <a name="next-steps"></a>Passaggi successivi

Quando si compila **un** controllo della casella Visual Studio crea un file denominato *ProjectName.vsix* nella cartella \bin\debug\ del progetto. È possibile distribuire il controllo caricando il file *vsix* in una rete o in un sito Web. Quando un utente apre il file *vsix,* il controllo viene installato e aggiunto alla casella degli strumenti Visual Studio **nel** computer dell'utente. In alternativa, è possibile caricare il file *vsix* [in Visual Studio Marketplace](https://marketplace.visualstudio.com/) in modo che gli utenti possano trovarlo esplorando la finestra di dialogo Estensioni e  >  **aggiornamenti degli** strumenti.

## <a name="see-also"></a>Vedi anche

- [Estendere altre parti di Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)
- [Creare un controllo della casella degli strumenti WPF](../extensibility/creating-a-wpf-toolbox-control.md)
- [Estendere altre parti di Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)
- [Windows Nozioni di base sullo sviluppo di controlli Form](/dotnet/framework/winforms/controls/windows-forms-control-development-basics)
