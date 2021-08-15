---
title: Testare un'app UWP con un test codificato dell'interfaccia utente
description: Informazioni su come creare un test codificato dell'interfaccia utente per un'app UWP (Universal Windows Platform) creando un'app UWP per testare e creare un test codificato dell'interfaccia utente.
ms.custom: SEO-VS-2020
ms.date: 05/31/2018
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
dev_langs:
- CSharp
- VB
ms.workload:
- uwp
ms.openlocfilehash: 7ba7ad4bb74d67f6ffd3c3c83c43c6c7fe5da2bddca7dde3e82df66f5190b0f1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121352596"
---
# <a name="create-a-coded-ui-test-to-test-a-uwp-app"></a>Creare un test codificato dell'interfaccia utente per testare un'app UWP

In questo articolo viene illustrato come creare un test codificato dell'interfaccia utente per un'app UWP (Universal Windows Platform).

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="create-a-uwp-app-to-test"></a>Creare un'app UWP da testare

Il primo passaggio consiste nel creare una semplice app UWP da testare.

1. Creare un nuovo progetto in Visual Studio usando il modello **App vuota (Windows universale)** per Visual C# o Visual Basic.

   ::: moniker range="vs-2017"

   ![Modello App vuota (Windows universale)](../test/media/blank-uwp-app-template.png)

   ::: moniker-end

1. Nella finestra di dialogo **Nuovo progetto della piattaforma UWP (Universal Windows Platform)** selezionare **OK** per accettare le versioni della piattaforma predefinite.

1. In **Esplora soluzioni** aprire il file *MainPage.xaml*.

   Il file verrà aperto nella **finestra di progettazione XAML**.

1. Dalla **Casella degli strumenti** trascinare un pulsante e una casella di testo nell'area di progettazione.

     ![Progettare l'app UWP](../test/media/toolbox-controls.png)

1. Assegnare nomi ai controlli. Selezionare il controllo della casella di testo e nella finestra **Proprietà** immettere **casella di testo** nel campo **Nome**. Selezionare il pulsante e nella finestra **Proprietà** immettere **pulsante** nel campo **Nome**.

1. Fare doppio clic sul controllo pulsante e aggiungere il codice seguente al metodo `Button_Click`. Questo codice non fa altro che impostare il testo nella casella di testo con il nome del pulsante, in modo da consentirne la verifica con il test codificato dell'interfaccia utente che verrà creato successivamente.

   ```csharp
   this.textBox.Text = this.button.Name;
   ```

   ```vb
   Me.textBox.Text = Me.button.Name
   ```

1. Premere **CTRL** + **F5 per** eseguire l'app. Verrà visualizzata una schermata simile alla seguente:

   ![App UWP con casella di testo e pulsante](media/uwp-app.png)

## <a name="create-a-coded-ui-test"></a>Crea test codificato dell'interfaccia utente

1. Per aggiungere un progetto di test a una soluzione, fare clic con il pulsante destro del mouse sulla soluzione in **Esplora soluzioni** e scegliere **Aggiungi** > **Nuovo progetto**.

1. Cercare e selezionare il modello **Progetto di test codificato dell'interfaccia utente (Windows universale)**.

   ::: moniker range="vs-2017"

   ![Nuovo progetto di test codificato dell'interfaccia utente](../test/media/coded-ui-test-project-uwp-template.png)

   ::: moniker-end

   > [!NOTE]
   > Se il modello **Progetto di test codificato dell'interfaccia utente (Windows universale)** non viene visualizzato, è necessario [installare il componente di test codificato dell'interfaccia utente](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component).

1. Nella finestra di dialogo **Genera codice per test codificato dell'interfaccia utente** selezionare **Modifica manualmente il test**.

   ![Finestra di dialogo Genera codice per test codificato dell'interfaccia utente](../test/media/manually-edit-the-test.png)

1. Se l'app UWP non è già in esecuzione, avviarla premendo **CTRL** + **F5.**

1. Aprire la finestra di dialogo **Generatore di test codificati dell'interfaccia utente** posizionando il cursore nel metodo `CodedUITestMethod1` e scegliendo **Test** > **Genera codice per test codificato dell'interfaccia utente** > **Usa il generatore di test codificati dell'interfaccia utente**.

1. Aggiungere i controlli alla mappa dei controlli dell'interfaccia utente. Usare lo strumento selettore di precisione **Generatore di test codificati dell'interfaccia utente** per selezionare il pulsante nell'app UWP. Nella finestra di dialogo **Aggiungi asserzione** espandere il riquadro **Mappa del controllo dell'interfaccia utente** se necessario e quindi selezionare **Aggiungi controllo alla mappa del controllo dell'interfaccia utente**.

     ![Aggiungere un controllo al mapping dell'interfaccia utente](../test/media/add-control-to-ui-control-map.png)

1. Per aggiungere il controllo della casella di testo alla mappa del controllo dell'interfaccia utente, ripetere il passaggio precedente.

1. Nella finestra di dialogo **Generatore di test codificati dell'interfaccia utente** selezionare **Genera codice** o premere **CTRL**+**G**. In seguito selezionare **Genera** per creare il codice per le modifiche alla mappa del controllo dell'interfaccia utente.

     ![Generare il codice per il mapping dell'interfaccia utente](../test/media/generate-code-dialog.png)

1. Provare a fare clic sul pulsante per verificare che, quando si fa clic, il testo nella casella di testo diventi **pulsante**.

     ![Fare clic sul controllo Button per impostare il valore della casella di testo](../test/media/uwp-app-button-textbox.png)

1. Aggiungere un'asserzione per verificare il testo nel controllo della casella di testo. Usare lo strumento selettore di precisione per selezionare il controllo della casella di testo e selezionare la proprietà **Text** nella finestra di dialogo **Aggiungi asserzione**. Quindi, selezionare **Aggiungi asserzione** o premere **ALT**+**A**. Nella casella **Messaggio su errore asserzione** immettere **Valore casella di testo imprevisto.** e quindi selezionare **OK.**

     ![Scegliere la casella di testo con lo strumento selettore di precisione e aggiungere un'asserzione](../test/media/add-assertion-for-text.png)

1. Generare il codice di test per l'asserzione. Nella finestra di dialogo **Generatore di test codificati dell'interfaccia utente** selezionare **Genera codice**. Nella finestra di dialogo **Genera codice** selezionare **Add and Generate** (Aggiungi e genera).

     ![Generare il codice per l'asserzione della casella di testo](../test/media/add-and-generate-assert-method.png)

   In **Esplora soluzioni** aprire il file *UIMap.Designer.cs* per visualizzare il codice aggiunto per il metodo dell'asserzione e i controlli.

   > [!TIP]
   > Se si usa Visual Basic, aprire *CodedUITest1.vb*. In seguito, nel codice del metodo di test `CodedUITestMethod1()` fare clic con il pulsante destro del mouse sulla chiamata del metodo di asserzione `Me.UIMap.AssertMethod1()` e scegliere **Vai a definizione**. Il file *UIMap.Designer.vb* si apre nell'editor del codice ed è possibile visualizzare il codice aggiunto per il metodo dell'asserzione e i controlli.

    > [!WARNING]
    > Non modificare direttamente il file *UIMap.designer.cs* o *UIMap.Designer.vb*. perché in tal caso, quando il test viene generato, le modifiche verrebbero sovrascritte.

    Il metodo di asserzione è simile al seguente:

    ```csharp
    public void AssertMethod1()
    {
        #region Variable Declarations
        XamlEdit uITextBoxEdit = this.UIUWPAppWindow.UITextBoxEdit;
        #endregion

        // Verify that the 'Text' property of 'textBox' text box equals 'button'
        Assert.AreEqual(this.AssertMethod1ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text, "Textbox value is unexpected.");
    }
    ```

    ```vb
    Public Sub AssertMethod1()
        Dim uITextBoxEdit As XamlEdit = Me.UIApp2Window.UITextBoxEdit

        'Verify that the 'Text' property of 'textBox' text box equals 'button'
        Assert.AreEqual(Me.AssertMethod1ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text, "Textbox value is unexpected.")
    End Sub
    ```

1. Successivamente, è necessario ottenere l'elemento **AutomationId** dell'[app](#create-a-uwp-app-to-test) UWP che si vuole testare. Aprire il menu **Start** di Windows per visualizzare il riquadro per l'app. In seguito, trascinare lo strumento selettore di precisione con l'![icona del bersaglio](media/target-icon.png) dalla finestra di dialogo **Generatore di test codificati dell'interfaccia utente** al riquadro dell'app. Quando una casella blu circonda il riquadro, rilasciare il mouse.

   ![Strumento selettore di precisione](media/cross-hair-tool.png)

   Si apre la finestra di dialogo **Aggiungi asserzioni** e viene visualizzato l'elemento **AutomationId** per l'app. Fare clic con il pulsante destro del mouse su **AutomationId** e scegliere **Copia valore negli Appunti**.

   ![AutomationID nella finestra di dialogo Aggiungi asserzioni](../test/media/automation-id.png)

1. Aggiungere codice al metodo di test per avviare l'app UWP. In **Esplora soluzioni** aprire il file *CodedUITest1.cs* o *CodedUITest1.vb*. Sopra alla chiamata al metodo `AssertMethod1`, aggiungere codice per avviare l'app UWP:

   ```csharp
   XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App")
   ```

   ```vb
   XamlWindow myAppWindow = XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App");
   ```

   Sostituire l'ID di automazione nel codice di esempio con il valore copiato negli Appunti nel passaggio precedente.

   > [!IMPORTANT]
   > Tagliare l'inizio dell'ID di automazione per rimuovere i caratteri come ad esempio **P~**. Se si non tagliano questi caratteri, il test genera un'eccezione `Microsoft.VisualStudio.TestTools.UITest.Extension.PlaybackFailureException` quando tenta di avviare l'app.

1. Successivamente, aggiungere codice al metodo di test per fare clic sul pulsante. Nella riga successiva a `XamlWindow.Launch` aggiungere un movimento per toccare il pulsante:

   ```csharp
   Gesture.Tap(this.UIMap.UIUWPAppWindow.UIButtonButton);
   ```

   ```vb
   Gesture.Tap(Me.UIMap.UIUWPAppWindow.UIButtonButton)
   ```

   Dopo avere aggiunto il codice, il metodo di test `CodedUITestMethod1` completo dovrebbe avere un aspetto simile al seguente:

   ```csharp
   [TestMethod]
   public void CodedUITestMethod1()
   {
       XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App");

       Gesture.Tap(this.UIMap.UIUWPAppWindow.UIButtonButton);

       // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.
       this.UIMap.AssertMethod1();
   }
   ```

   ```vb
   <CodedUITest(CodedUITestType.WindowsStore)>
   Public Class CodedUITest1

       <TestMethod()>
       Public Sub CodedUITestMethod1()

           ' Launch the app.
           XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App")

           '// Tap the button.
           Gesture.Tap(Me.UIMap.UIUWPAppWindow.UIButtonButton)

           Me.UIMap.AssertMethod1()
       End Sub
   ```

1. Compilare il progetto di test e aprire **Esplora test** selezionando **Test** > **Windows** > **Esplora test**.

1. Scegliere **Esegui tutti** per eseguire il test.

   Si apre l'app, il pulsante viene toccato e la proprietà **Text** della casella di testo viene popolata. Il metodo di asserzione convalida la proprietà **Text** della casella di testo.

   Al termine dell'esecuzione del test, **Esplora test** indica che il test è stato superato.

   ![Il test superato viene visualizzato in Esplora test](../test/media/test-explorer-coded-ui-test-passed.png)

## <a name="q--a"></a>Domande e risposte

### <a name="q-why-dont-i-see-the-option-to-record-my-coded-ui-test-in-the-generate-code-for-a-coded-ui-test-dialog"></a>D: Perché nella finestra di dialogo Genera codice per un test codificato dell'interfaccia utente non è presente un'opzione per registrare un test codificato dell'interfaccia utente personalizzato?

**R**: L'opzione per la registrazione non è supportata per le app UWP.

### <a name="q-can-i-create-a-coded-ui-test-for-my-uwp-apps-based-on-winjs"></a>D: È possibile creare un test codificato dell'interfaccia utente per le app UWP basate su WinJS?

**R**: No, sono supportate solo le app basate su XAML.

### <a name="q-why-cant-i-modify-the-code-in-the-uimapdesigner-file"></a>D: Perché non è possibile modificare il codice nel file UIMap.Designer?

**R**: Qualsiasi modifica del codice apportata nel file *UIMapDesigner.cs* viene sovrascritta ogni volta che si genera codice usando **Generatore di test codificati dell'interfaccia utente**. Se è necessario modificare un metodo registrato, copiarlo nel file *UIMap.cs* e rinominarlo. Il file *UIMap.cs* può essere usato per eseguire l'override di metodi e proprietà nel file *UIMapDesigner.cs.* Rimuovere il riferimento al metodo originale nel file *Coded UITest.cs* e sostituirlo con il nome del metodo rinominato.

## <a name="see-also"></a>Vedi anche

- [Usare l'automazione dell'interfaccia utente per testare il codice](../test/use-ui-automation-to-test-your-code.md)
- [Impostare una proprietà di automazione univoca dei controlli UWP per il test](../test/set-a-unique-automation-property-for-windows-store-controls-for-testing.md)
