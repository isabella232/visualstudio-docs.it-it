---
title: Creazione di una pagina di opzioni | Microsoft Docs
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], creating
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: be826b73e28a73216ea88ceba8e23eb1e9ea457b
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903813"
---
# <a name="create-an-options-page"></a>Creare una pagina di opzioni

In questa procedura dettagliata viene creata una semplice pagina strumenti/opzioni che utilizza una griglia delle proprietà per esaminare e impostare le proprietà.

 Per salvare queste proprietà e ripristinarle da un file di impostazioni, seguire questa procedura e quindi vedere [creare una categoria di impostazioni](../extensibility/creating-a-settings-category.md).

 MPF fornisce due classi per facilitare la creazione di pagine di opzioni degli strumenti, la <xref:Microsoft.VisualStudio.Shell.Package> classe e la <xref:Microsoft.VisualStudio.Shell.DialogPage> classe. Si crea un pacchetto VSPackage per fornire un contenitore per queste pagine creando una sottoclasse della `Package` classe. Per creare ogni pagina di opzioni degli strumenti, derivare dalla `DialogPage` classe.

## <a name="prerequisites"></a>Prerequisiti

 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. Viene inclusa come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare Visual Studio SDK in un secondo momento. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-tools-options-grid-page"></a>Pagina di creazione della griglia delle opzioni degli strumenti

 In questa sezione viene creata una semplice griglia delle proprietà Opzioni strumenti. Utilizzare questa griglia per visualizzare e modificare il valore di una proprietà.

### <a name="to-create-the-vsix-project-and-add-a-vspackage"></a>Per creare il progetto VSIX e aggiungere un pacchetto VSPackage

1. Ogni estensione di Visual Studio inizia con un progetto di distribuzione VSIX, che conterrà gli asset di estensione. Creare un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] progetto VSIX denominato `MyToolsOptionsExtension` . È possibile trovare il modello di progetto VSIX nella finestra di dialogo **nuovo progetto** cercando "VSIX".

2. Aggiungere un pacchetto VSPackage aggiungendo un modello di elemento del pacchetto di Visual Studio denominato `MyToolsOptionsPackage` . Nella **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Aggiungi**  >  **nuovo elemento**. Nella **finestra di dialogo Aggiungi nuovo elemento**passare a **Visual C# elementi**  >  **estensibilità** e selezionare **pacchetto di Visual Studio**. Nel campo **nome** nella parte inferiore della finestra di dialogo modificare il nome del file in `MyToolsOptionsPackage.cs` . Per altre informazioni su come creare un pacchetto VSPackage, vedere [creare un'estensione con un pacchetto VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md).

### <a name="to-create-the-tools-options-property-grid"></a>Per creare la griglia delle proprietà Opzioni strumenti

1. Aprire il file *MyToolsOptionsPackage* nell'editor di codice.

2. Aggiungere la seguente istruzione using.

   ```csharp
   using System.ComponentModel;
   ```

3. Dichiarare una `OptionPageGrid` classe e derivarla da <xref:Microsoft.VisualStudio.Shell.DialogPage> .

   ```csharp
   public class OptionPageGrid : DialogPage
   {  }
   ```

4. Applicare un <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> alla `VSPackage` classe per assegnare alla classe una categoria di opzioni e il nome della pagina di opzioni per OptionPageGrid. Il risultato dovrebbe essere simile al seguente:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [Guid(GuidList.guidMyToolsOptionsPkgString)]
    [ProvideOptionPage(typeof(OptionPageGrid),
        "My Category", "My Grid Page", 0, 0, true)]
    public sealed class MyToolsOptionsPackage : Package
    ```

5. Aggiungere una `OptionInteger` proprietà alla `OptionPageGrid` classe.

    - Applicare un oggetto <xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName> per assegnare alla proprietà una categoria della griglia delle proprietà.

    - Applicare un oggetto <xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName> per assegnare alla proprietà un nome.

    - Applicare un oggetto <xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName> per assegnare alla proprietà una descrizione.

    ```csharp
    public class OptionPageGrid : DialogPage
    {
        private int optionInt = 256;

        [Category("My Category")]
        [DisplayName("My Integer Option")]
        [Description("My integer option")]
        public int OptionInteger
        {
            get { return optionInt; }
            set { optionInt = value; }
        }
    }
    ```

    > [!NOTE]
    > L'implementazione predefinita di <xref:Microsoft.VisualStudio.Shell.DialogPage> supporta proprietà con convertitori appropriati o strutture o matrici che possono essere espanse in proprietà con convertitori appropriati. Per un elenco dei convertitori, vedere lo <xref:System.ComponentModel> spazio dei nomi.

6. Compilare il progetto e avviare il debug.

7. Nell'istanza sperimentale di Visual Studio scegliere **Opzioni**dal menu **strumenti** .

     Nel riquadro sinistro dovrebbe essere visualizzata la **categoria**. (Le categorie di opzioni sono elencate in ordine alfabetico, quindi dovrebbero apparire a metà dell'elenco). Aprire **la categoria** e quindi fare clic sulla **pagina della griglia**. La griglia opzioni verrà visualizzata nel riquadro destro. La categoria proprietà è **My Options**e il nome della proprietà è l' **opzione Integer**. La descrizione della proprietà, l' **opzione Integer**, viene visualizzata nella parte inferiore del riquadro. Modificare il valore del valore iniziale 256 in un altro. Fare clic su **OK**e quindi riaprire **la pagina della griglia**. È possibile osservare che il nuovo valore è permanente.

     La pagina Opzioni è disponibile anche tramite la casella di ricerca di Visual Studio. Nella casella di ricerca nella parte superiore dell'IDE digitare **My Category** (categoria). verrà visualizzata la **pagina Category-> My Grid** elencata nei risultati.

## <a name="create-a-tools-options-custom-page"></a>Crea una pagina personalizzata delle opzioni degli strumenti

 In questa sezione viene creata una pagina di opzioni degli strumenti con un'interfaccia utente personalizzata. Usare questa pagina per visualizzare e modificare il valore di una proprietà.

1. Aprire il file *MyToolsOptionsPackage* nell'editor di codice.

2. Aggiungere la seguente istruzione using.

    ```csharp
    using System.Windows.Forms;
    ```

3. Aggiungere una `OptionPageCustom` classe, immediatamente prima della `OptionPageGrid` classe. Derivare la nuova classe da `DialogPage` .

    ```csharp
    public class OptionPageCustom : DialogPage
    {
        private string optionValue = "alpha";

        public string OptionString
        {
            get { return optionValue; }
            set { optionValue = value; }
        }
    }
    ```

4. Aggiungere un attributo GUID. Aggiungere una proprietà OptionString:

    ```csharp
    [Guid("00000000-0000-0000-0000-000000000000")]
    public class OptionPageCustom : DialogPage
    {
        private string optionValue = "alpha";

        public string OptionString
        {
            get { return optionValue; }
            set { optionValue = value; }
        }
    }
    ```

5. Applicare un secondo <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> alla classe VSPackage. Questo attributo assegna alla classe una categoria di opzioni e il nome della pagina di opzioni.

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [Guid(GuidList.guidMyToolsOptionsPkgString)]
    [ProvideOptionPage(typeof(OptionPageGrid),
        "My Category", "My Grid Page", 0, 0, true)]
    [ProvideOptionPage(typeof(OptionPageCustom),
        "My Category", "My Custom Page", 0, 0, true)]
    public sealed class MyToolsOptionsPackage : Package
    ```

6. Aggiungere al progetto un nuovo **controllo utente** denominato UserControl.

7. Aggiungere un controllo **TextBox** al controllo utente.

     Nella finestra **Proprietà** fare clic sul pulsante **eventi** sulla barra degli strumenti, quindi fare doppio clic sull'evento **Leave** . Il nuovo gestore eventi viene visualizzato nel codice *MyUserControl.cs* .

8. Aggiungere un `OptionsPage` campo pubblico, un `Initialize` metodo alla classe del controllo e aggiornare il gestore eventi per impostare il valore dell'opzione sul contenuto della casella di testo:

    ```csharp
    public partial class MyUserControl : UserControl
    {
        public MyUserControl()
        {
            InitializeComponent();
        }

        internal OptionPageCustom optionsPage;

        public void Initialize()
        {
            textBox1.Text = optionsPage.OptionString;
        }

        private void textBox1_Leave(object sender, EventArgs e)
        {
            optionsPage.OptionString = textBox1.Text;
        }
    }
    ```

     Il `optionsPage` campo include un riferimento all'istanza padre `OptionPageCustom` . Il `Initialize` metodo viene visualizzato `OptionString` nella **casella di testo**. Il gestore eventi scrive il valore corrente della **casella di testo** in `OptionString` quando lo stato attivo esce dalla **casella di testo**.

9. Nel file di codice del pacchetto, aggiungere una sostituzione per la `OptionPageCustom.Window` proprietà alla `OptionPageCustom` classe per creare, inizializzare e restituire un'istanza di `MyUserControl` . La classe dovrebbe ora essere simile alla seguente:

    ```csharp
    [Guid("00000000-0000-0000-0000-000000000000")]
    public class OptionPageCustom : DialogPage
    {
        private string optionValue = "alpha";

        public string OptionString
        {
            get { return optionValue; }
            set { optionValue = value; }
        }

        protected override IWin32Window Window
        {
            get
            {
                MyUserControl page = new MyUserControl();
                page.optionsPage = this;
                page.Initialize();
                return page;
            }
        }
    }
    ```

10. Compilare ed eseguire il progetto.

11. Nell'istanza sperimentale, fare clic su **strumenti**  >  **Opzioni**.

12. Trovare **la categoria** e quindi **la pagina personalizzata**.

13. Modificare il valore di **OptionString**. Fare clic su **OK**e quindi riaprire **la pagina personalizzata**. È possibile osservare che il nuovo valore è stato reso permanente.

## <a name="access-options"></a>Opzioni di accesso

 In questa sezione si ottiene il valore di un'opzione dal pacchetto VSPackage che ospita la pagina delle opzioni degli strumenti associati. La stessa tecnica può essere usata per ottenere il valore di qualsiasi proprietà pubblica.

1. Nel file di codice del pacchetto aggiungere una proprietà pubblica denominata **OptionInteger** alla classe **MyToolsOptionsPackage** .

    ```csharp
    public int OptionInteger
    {
        get
        {
            OptionPageGrid page = (OptionPageGrid)GetDialogPage(typeof(OptionPageGrid));
            return page.OptionInteger;
        }
    }

    ```

     Questo codice chiama <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> per creare o recuperare un' `OptionPageGrid` istanza di. `OptionPageGrid`chiama <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A> per caricare le opzioni, che sono proprietà pubbliche.

2. A questo punto, aggiungere un modello di elemento di comando personalizzato denominato **MyToolsOptionsCommand** per visualizzare il valore. Nella finestra di dialogo **Aggiungi nuovo elemento** passare a **Visual C#**  >  **estensibilità** di Visual C# e selezionare **comando personalizzato**. Nel campo **nome** nella parte inferiore della finestra modificare il nome del file di comando in *MyToolsOptionsCommand.cs*.

3. Nel file *MyToolsOptionsCommand* sostituire il corpo del metodo del comando `ShowMessageBox` con il codice seguente:

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));
    }

    ```

4. Compilare il progetto e avviare il debug.

5. Nell'istanza sperimentale, scegliere **richiama MyToolsOptionsCommand**dal menu **strumenti** .

     In una finestra di messaggio viene visualizzato il valore corrente di `OptionInteger` .

## <a name="see-also"></a>Vedere anche

- [Pagine opzioni e opzioni](../extensibility/internals/options-and-options-pages.md)
