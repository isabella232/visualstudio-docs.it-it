---
title: Creare un editor del corpo HTTP personalizzato per l'Editor test prestazioni Web
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, custom HTTP body editor
ms.assetid: a0b2d8ff-3e2a-487e-9172-90047174f336
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 30ce24b0cb48e88ddb77cf3576d40f95ed022ba0
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926519"
---
# <a name="how-to-create-a-custom-http-body-editor-for-the-web-performance-test-editor"></a>Procedura: Creare un editor del corpo HTTP personalizzato per l'editor test prestazioni Web

È possibile creare un editor dei contenuti personalizzato per modificare il contenuto del corpo delle stringhe o del corpo binario di una richiesta di servizio Web, ad esempio SOAP, REST, asmx, wcf, RIA e altri tipi di richieste di servizio Web.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

È possibile implementare questi tipi di editor:

- **Editor di contenuto stringa** Questo editor viene implementato usando l'interfaccia <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin>.

- **Editor di contenuto binario** Questo editor viene implementato usando l'interfaccia <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin>.

Queste interfacce sono contenute nello spazio dei nomi <xref:Microsoft.VisualStudio.TestTools.WebTesting>.

## <a name="create-a-windows-control-library-project"></a>Creazione di un progetto di libreria di controlli Windows

1. Creare un nuovo progetto **Libreria di controlli Windows Form** in Visual Studio. Assegnare al progetto il nome **MessageEditors**.

   Il progetto viene aggiunto alla nuova soluzione e un oggetto <xref:System.Windows.Forms.UserControl> denominato *UserControl1.cs* viene presentato nella finestra di progettazione.

1. Dalla **casella degli strumenti**, nella categoria **Controlli comuni** trascinare un oggetto <xref:System.Windows.Forms.RichTextBox> sulla superficie di UserControl1.

1. Scegliere il glifo del tag azioni (![Glifo smart tag](../test/media/vs_winformsmttagglyph.gif)) nell'angolo superiore destro del controllo <xref:System.Windows.Forms.RichTextBox>, quindi selezionare **Ancora nel contenitore padre**.

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto della libreria di controlli Windows Forms e selezionare **Proprietà**.

1. Nella pagina **Proprietà** selezionare la scheda **Applicazione**.

1. Nell'elenco a discesa **Framework di destinazione** selezionare .NET Framework 4 (o versioni successive).

1. Viene visualizzata la finestra di dialogo **Modifica del framework di destinazione**.

1. Scegliere **Sì**.

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo **Riferimenti** e scegliere **Aggiungi riferimento**.

1. Viene visualizzata la finestra di dialogo **Aggiungi riferimento**.

1. Scegliere la scheda .**NET**, scorrere verso il basso, quindi selezionare **Microsoft.VisualStudio.QualityTools.WebTestFramework** e scegliere **OK**.

1. Se la **finestra di progettazione** non è ancora aperta, in **Esplora soluzioni** fare clic con il pulsante destro del mouse su **UserControl1.cs**, quindi selezionare **Visualizza finestra di progettazione**.

1. Fare clic con il pulsante destro del mouse sull'area di progettazione e selezionare **Visualizza codice**.

1. (Facoltativo) Assegnare alla classe e al costruttore denominati UserControl1 un altro nome significativo, ad esempio MessageEditorControl:

    > [!NOTE]
    > Nell'esempio viene utilizzato MessageEditorControl.

    ```csharp
    namespace MessageEditors
    {
        public partial class MessageEditorControl : UserControl
        {
            public MessageEditorControl()
            {
                InitializeComponent();
            }
        }
    }
    ```

1. Aggiungere le proprietà seguenti per abilitare l'ottenimento e l'impostazione del testo in RichTextBox1. L'interfaccia <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> utilizzerà EditString e <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> utilizzerà EditByteArray:

    ```csharp
    public String EditString
    {
       get
       {
           return this.richTextBox1.Text;
       }
       set
       {
           this.richTextBox1.Text = value;
       }
    }

    public byte[] EditByteArray
    {
       get
       {
           return System.Convert.FromBase64String(richTextBox1.Text);
       }
       set
       {
           richTextBox1.Text = System.Convert.ToBase64String(value, 0, value.Length);
       }
    }
    ```

## <a name="add-a-class-to-the-windows-control-library-project"></a>Aggiungere una classe al progetto di libreria di controlli Windows

Aggiungere una classe al progetto. Verrà utilizzata per implementare le interfacce <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> e <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin>.

**Panoramica del codice in questa procedura**

Viene creata un'istanza dell'oggetto MessageEditorControl <xref:System.Windows.Forms.UserControl> creato nella procedura precedente come messageEditorControl:

```csharp
private MessageEditorControl messageEditorControl
```

L'istanza dell'oggetto messageEditorControl è ospitata all'interno della finestra di dialogo del plug-in creata dal metodo <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.CreateEditor*>. Inoltre, l'oggetto <xref:System.Windows.Forms.RichTextBox> di messageEditorControl viene popolato con il contenuto in <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>. Tuttavia, la creazione del plug-in non può aver luogo a meno che <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.SupportsContentType*> non restituisca `true`. Nel caso di questo editor, <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.SupportsContentType*> restituisce `true` se <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody.ContentType*> in <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> contiene "xml".

Quando viene completata la modifica del corpo della stringa e l'utente fa clic su **OK** nella finestra di dialogo del plug-in, viene chiamato <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.GetNewValue*> per ottenere il testo modificato come stringa e aggiornare il **Corpo stringa** nella richiesta nell'Editor test prestazioni Web.

### <a name="create-a-class-and-implement-the-istringhttpbodyeditorplugin-interface"></a>Creare una classe e implementare l'interfaccia IStringHttpBodyEditorPlugin

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto della libreria di controlli Windows Forms e scegliere **Aggiungi nuovo elemento**.

   Verrà visualizzata la finestra di dialogo **Aggiungi nuovo elemento**.

2. Selezionare **Classe**.

3. Nella casella di testo **Nome** digitare un nome significativo per la classe, ad esempio `MessageEditorPlugins`.

4. Scegliere **Aggiungi**.

   L'oggetto Class1 viene aggiunto al progetto e presentato nell'editor di codice.

5. Nell'editor del codice aggiungere l'istruzione `using` seguente:

    ```csharp
    using Microsoft.VisualStudio.TestTools.WebTesting;
    ```

6. Incollare il codice seguente per implementare l'interfaccia:

    ```csharp
    /// <summary>
    /// Editor for generic text based hierarchical messages such as XML and JSON.
    /// </summary>
    public class XmlMessageEditor : IStringHttpBodyEditorPlugin
    {
        public XmlMessageEditor()
        {
        }

        /// <summary>
        /// Determine if this plugin supports the content type.
        /// </summary>
        /// <param name="contentType">The content type to test.</param>
        /// <returns>Returns true if the plugin supports the specified content type.</returns>
        public bool SupportsContentType(string contentType)
        {
            return contentType.ToLower().Contains("xml");
        }

        /// <summary>
        /// Create a UserControl to edit the specified bytes.
        /// This control will be hosted in the
        /// plugin dialog which provides OK and Cancel buttons.
        /// </summary>
        /// <param name="contentType">The content type of the BinaryHttpBody.</param>
        /// <param name="initialValue">The bytes to edit. The bytes are the payload of a BinaryHttpBody.</param>
        /// <returns>A UserControl capable of displaying and editing the byte array value of the specified content type.</returns>
        public object CreateEditor(string contentType, string initialValue)
        {
            messageEditorControl = new MessageEditorControl();
            messageEditorControl.EditString = initialValue;
            return this.messageEditorControl;
        }

        /// <summary>
        /// Gets the edited bytes after the OK button is clicked on the plugin dialog.
        /// </summary>
        public string GetNewValue()
        {
            return messageEditorControl.EditString;
        }

        private MessageEditorControl messageEditorControl;
    }
    ```

## <a name="add-a-ibinaryhttpbodyeditorplugin-to-the-class"></a>Aggiungere un oggetto IBinaryHttpBodyEditorPlugin alla classe

Implementare l'interfaccia <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin>.

**Panoramica del codice in questa procedura**

L'implementazione del codice per l'interfaccia <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> è simile a quella dell'oggetto <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> illustrato nella procedura precedente. Tuttavia, la versione binaria utilizza una matrice di byte per gestire i dati binari anziché una stringa.

Viene creata un'istanza dell'oggetto MessageEditorControl <xref:System.Windows.Forms.UserControl> creato nella prima procedura come messageEditorControl:

```csharp
private MessageEditorControl messageEditorControl
```

L'istanza dell'oggetto messageEditorControl è ospitata all'interno della finestra di dialogo del plug-in creata dal metodo <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.CreateEditor*>. Inoltre, l'oggetto <xref:System.Windows.Forms.RichTextBox> di messageEditorControl viene popolato con il contenuto in <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>. Tuttavia, la creazione del plug-in non può aver luogo a meno che <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.SupportsContentType*> non restituisca `true`. Nel caso di questo editor, <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.SupportsContentType*> restituisce `true` se <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody.ContentType*> in <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> contiene "msbin1".

Quando viene completata la modifica del corpo della stringa e l'utente fa clic su **OK** nella finestra di dialogo del plug-in, viene chiamato <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.GetNewValue*> per ottenere il testo modificato come stringa e aggiornare **BinaryHttpBody.Data** nella richiesta nell'Editor test prestazioni Web.

### <a name="to-add-the-ibinaryhttpbodyeditorplugin-to-the-class"></a>Per aggiungere un oggetto IBinaryHttpBodyEditorPlugin alla classe

- Scrivere o copiare il codice seguente sotto la classe XmlMessageEditor aggiunta nella procedura precedente per creare un'istanza della classe Msbin1MessageEditor dall'interfaccia <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> e implementare i metodi richiesti:

    ```csharp
    /// <summary>
        /// Editor for MSBin1 content type (WCF messages)
        /// </summary>
        public class Msbin1MessageEditor : IBinaryHttpBodyEditorPlugin
        {
            /// <summary>
            ///
            /// </summary>
            public Msbin1MessageEditor()
            {
            }

            /// <summary>
            /// Determine if this plugin supports a content type.
            /// </summary>
            /// <param name="contentType">The content type to test.</param>
            /// <returns>Returns true if the plugin supports the specified content type.</returns>
            public bool SupportsContentType(string contentType)
            {
                return contentType.ToLower().Contains("msbin1");
            }

            /// <summary>
            /// Create a UserControl to edit the specified bytes. This control will be hosted in the
            /// plugin dialog which provides OK and Cancel buttons.
            /// </summary>
            /// <param name="contentType">The content type of the BinaryHttpBody.</param>
            /// <param name="initialValue">The bytes to edit. The bytes are the payload of a BinaryHttpBody.</param>
            /// <returns>A UserControl capable of displaying and editing the byte array value of the specified content type.</returns>
            public object CreateEditor(string contentType, byte[] initialValue)
            {
                messageEditorControl = new MessageEditorControl();
                messageEditorControl.EditByteArray = initialValue;
                return messageEditorControl;
            }

            /// <summary>
            /// Gets the edited bytes after the OK button is clicked on the plugin dialog.
            /// </summary>
            public byte[] GetNewValue()
            {
                return messageEditorControl.EditByteArray;
            }

            private MessageEditorControl messageEditorControl;
            private object originalMessage;
        }
    ```

## <a name="build-and-deploy-the-plug-ins"></a>Compilare e distribuire i plug-in

1. Dal menu **Compila** scegliere **Compila \<nome progetto Libreria di controlli Windows Form>** .

2. Chiudere tutte le istanze di Visual Studio.

   > [!NOTE]
   > La chiusura di Visual Studio consente di assicurarsi che il file con estensione *dll* non sia bloccato prima di provare a copiarlo.

3. Copiare il file con estensione *dll* risultante dalla cartella *bin\debug* del progetto (ad esempio, *MessageEditors.dll*) in *%ProgramFiles%\Microsoft Visual Studio\2017\\\<edizione>\Common7\IDE\PrivateAssemblies\WebTestPlugins*.

4. Aprire Visual Studio.

   Il file con estensione *dll* è ora registrato in Visual Studio.

## <a name="verify-the-plug-ins-using-a-web-performance-test"></a>Verificare i plug-in usando un test prestazioni Web

1. Creare un progetto di test.

2. Creare un test delle prestazioni Web e immettere un URL di servizio Web nel browser.

3. Quando si termina la registrazione, nell'Editor test prestazioni Web espandere la richiesta per il servizio Web e selezionare un **Corpo stringa** o un **Corpo binario**.

4. Nella finestra **Proprietà** selezionare Corpo stringa o Corpo binario e scegliere i puntini di sospensione **(…)** .

   Viene visualizzata la finestra di dialogo **Modifica dati del corpo HTTP**.

5. È ora possibile modificare i dati e scegliere **OK**. In questo modo viene richiamato il metodo GetNewValue per aggiornare il contenuto nell'oggetto <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>.

## <a name="compile-the-code"></a>Compilare il codice

Verificare che il framework di destinazione per il progetto di libreria di controlli Windows sia .NET Framework 4.5. Per impostazione predefinita, i progetti di libreria di controlli Windows sono destinati al framework client .NET Framework 4.5, che impedisce l'inclusione del riferimento Microsoft.VisualStudio.QualityTools.WebTestFramework.

Per altre informazioni, vedere [Pagina Applicazione, Creazione progetti (C#)](../ide/reference/application-page-project-designer-csharp.md).

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>
- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.RichTextBox>
- [Creare codice personalizzato e plug-in per test di carico](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Procedura: Creare un plug-in a livello di richiesta](../test/how-to-create-a-request-level-plug-in.md)
- [Codificare una regola di estrazione personalizzata per un test delle prestazioni Web](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Codificare una regola di convalida personalizzata per un test delle prestazioni Web](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Procedura: Creare un plug-in test di carico](../test/how-to-create-a-load-test-plug-in.md)
- [Generare ed eseguire un test delle prestazioni Web codificato](../test/generate-and-run-a-coded-web-performance-test.md)
- [Procedura: Creare un componente aggiuntivo di Visual Studio per il Visualizzatore risultati test prestazioni Web](../test/how-to-create-an-add-in-for-the-web-performance-test-results-viewer.md)