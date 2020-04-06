---
title: Creazione di una pagina delle opzioni Documenti Microsoft
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], creating
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1607af2a6f68bd5593f9a185188b25b364926fe4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739523"
---
# <a name="create-an-options-page"></a>Creare una pagina delle opzioni

In questa procedura dettagliata viene creata una semplice pagina Strumenti/Opzioni che utilizza una griglia delle proprietà per esaminare e impostare le proprietà.

 Per salvare queste proprietà e ripristinarle da un file di impostazioni, attenersi alla seguente procedura e quindi vedere [Creare una categoria](../extensibility/creating-a-settings-category.md)di impostazioni .

 In MPF sono disponibili due classi che <xref:Microsoft.VisualStudio.Shell.Package> consentono di <xref:Microsoft.VisualStudio.Shell.DialogPage> creare le pagine Opzioni degli strumenti, la classe e la classe. Creare un pacchetto VSPackage per fornire un contenitore `Package` per queste pagine sottoclassando la classe. È possibile creare ogni pagina delle `DialogPage` opzioni degli strumenti derivando dalla classe.

## <a name="prerequisites"></a>Prerequisiti

 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio.It is included as an optional feature in Visual Studio setup. È anche possibile installare l'SDK di VISUAL SMI in un secondo momento. Per ulteriori informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-tools-options-grid-page"></a>Creare una pagina della griglia Opzioni di Strumenti

 In questa sezione viene creata una semplice griglia delle proprietà Opzioni degli strumenti. Utilizzare questa griglia per visualizzare e modificare il valore di una proprietà.

### <a name="to-create-the-vsix-project-and-add-a-vspackage"></a>Per creare il progetto VSIX e aggiungere un pacchetto VSPackageTo create the VSIX project and add a VSPackage

1. Ogni estensione di Visual Studio inizia con un progetto di distribuzione VSIX, che conterrà gli asset di estensione. Creare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] un progetto `MyToolsOptionsExtension`VSIX denominato . È possibile trovare il modello di progetto VSIX nella finestra di dialogo **Nuovo progetto** cercando "vsix".

2. Aggiungere un pacchetto VSPackage aggiungendo un `MyToolsOptionsPackage`modello di elemento pacchetto di Visual Studio denominato . In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nodo del progetto e **scegliere Aggiungi** > **nuovo elemento**. Nella finestra di **dialogo Aggiungi nuovo elemento**, passare a**Estensibilità** degli elementi > di **Visual C,** quindi selezionare **Pacchetto di Visual Studio**. Nel campo **Nome** nella parte inferiore della finestra `MyToolsOptionsPackage.cs`di dialogo, modificare il nome del file in . Per ulteriori informazioni su come creare un pacchetto VSPackage, vedere [creare un'estensione con un VSPackage.For](../extensibility/creating-an-extension-with-a-vspackage.md)more information about how to create a VSPackage, see Create an extension with a VSPackage.

### <a name="to-create-the-tools-options-property-grid"></a>Per creare la griglia delle proprietà Opzioni degli strumenti

1. Aprire il file *MyToolsOptionsPackage* nell'editor di codice.

2. Aggiungere l'istruzione using seguente.

   ```csharp
   using System.ComponentModel;
   ```

3. Dichiarare `OptionPageGrid` una classe e <xref:Microsoft.VisualStudio.Shell.DialogPage>derivarla da .

   ```csharp
   public class OptionPageGrid : DialogPage
   {  }
   ```

4. Applicare <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> un `VSPackage` alla classe da assegnare alla classe una categoria di opzioni e il nome della pagina delle opzioni per il OptionPageGrid. Il risultato dovrebbe essere simile al seguente:The result should look like this:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [Guid(GuidList.guidMyToolsOptionsPkgString)]
    [ProvideOptionPage(typeof(OptionPageGrid),
        "My Category", "My Grid Page", 0, 0, true)]
    public sealed class MyToolsOptionsPackage : Package
    ```

5. Aggiungere `OptionInteger` una proprietà `OptionPageGrid` alla classe.

    - Applicare <xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName> un per assegnare alla proprietà una categoria della griglia delle proprietà.

    - Applicare <xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName> un per assegnare alla proprietà un nome.

    - Applicare <xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName> un per assegnare alla proprietà una descrizione.

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
    > L'implementazione <xref:Microsoft.VisualStudio.Shell.DialogPage> predefinita di supporta le proprietà che dispongono di convertitori appropriati o che sono strutture o matrici che possono essere espanse in proprietà che dispongono di convertitori appropriati. Per un elenco dei convertitori, vedere lo <xref:System.ComponentModel> spazio dei nomi.

6. Compilare il progetto e avviare il debug.

7. Nell'istanza sperimentale di Visual Studio scegliere **Opzioni**dal menu **Strumenti** .

     Nel riquadro sinistro dovrebbe essere visualizzato **Categoria personale**. Le categorie di opzioni sono elencate in ordine alfabetico, pertanto dovrebbero essere visualizzate a metà dell'elenco. Aprire **Categoria personale** e quindi fare clic su Pagina **griglia**personale . La griglia delle opzioni viene visualizzata nel riquadro di destra. La categoria di proprietà è **Opzioni personali**e il nome della proprietà è My **Integer Option**. La descrizione della proprietà, **opzione My integer**, viene visualizzata nella parte inferiore del riquadro. Modificare il valore dal valore iniziale di 256 a qualcos'altro. Fare clic **su OK**e quindi riaprire **Pagina griglia**personale . Si può vedere che il nuovo valore persiste.

     La pagina delle opzioni è disponibile anche tramite la casella di ricerca di Visual Studio.Your options page is also available through Visual Studio's search box. Nella casella di ricerca nella parte superiore dell'IDE digitare **Categoria personale** e nei risultati verrà visualizzata la **pagina Categoria-> pagina griglia** personale.

## <a name="create-a-tools-options-custom-page"></a>Creare una pagina personalizzata Opzioni strumenti

 In questa sezione viene creata una pagina Opzioni degli strumenti con un'interfaccia utente personalizzata. Utilizzare questa pagina per visualizzare e modificare il valore di una proprietà.

1. Aprire il file *MyToolsOptionsPackage* nell'editor di codice.

2. Aggiungere l'istruzione using seguente.

    ```csharp
    using System.Windows.Forms;
    ```

3. Aggiungere `OptionPageCustom` una classe, `OptionPageGrid` appena prima della classe. Derivare la `DialogPage`nuova classe da .

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

4. Aggiungere un attributo GUID. Aggiungere una proprietà OptionString:Add an OptionString property:

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

5. Applicare un <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> secondo alla classe VSPackage.Apply a second to the VSPackage class. Questo attributo assegna alla classe una categoria di opzioni e il nome della pagina delle opzioni.

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

6. Aggiungere un nuovo **controllo utente** denominato MyUserControl al progetto.

7. Aggiungere un controllo **TextBox** al controllo utente.

     Nella barra degli strumenti della finestra **Proprietà** fare clic sul pulsante **Eventi** e quindi fare doppio clic sull'evento **Leave.** Il nuovo gestore eventi viene visualizzato nel codice *MyUserControl.cs.*

8. Aggiungere un `OptionsPage` campo `Initialize` pubblico, un metodo alla classe del controllo e aggiornare il gestore eventi per impostare il valore dell'opzione sul contenuto della casella di testo:

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

     Il `optionsPage` campo contiene un `OptionPageCustom` riferimento all'istanza padre. Il `Initialize` metodo `OptionString` viene visualizzato nella casella **di testo**. Il gestore eventi scrive il valore `OptionString` corrente di **TextBox** al quando lo stato attivo lascia il **TextBox**.

9. Nel file di codice del pacchetto `OptionPageCustom.Window` aggiungere `OptionPageCustom` un override per la proprietà alla `MyUserControl`classe per creare, inizializzare e restituire un'istanza di . La classe dovrebbe essere simile alla seguente:The class should now look like this:

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

11. Nell'istanza sperimentale, fare clic su**Opzioni** **strumenti** > .

12. Trova **la mia categoria** e poi La mia pagina **personalizzata**.

13. Modificare il valore di **OptionString**. Fare clic su **OK**e quindi riaprire **Pagina personalizzata**. Si può vedere che il nuovo valore è stato mantenuto.

## <a name="access-options"></a>Opzioni di accesso

 In questa sezione, si ottiene il valore di un'opzione dal pacchetto VSPackage che ospita la pagina opzioni degli strumenti associata. La stessa tecnica può essere utilizzata per ottenere il valore di qualsiasi proprietà pubblica.

1. Nel file di codice del pacchetto aggiungere una proprietà pubblica denominata OptionInteger alla classe **MyToolsOptionsPackage.In** the package code file, add a public property called **OptionInteger** to the MyToolsOptionsPackage class.

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

     Questo codice <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> chiama per `OptionPageGrid` creare o recuperare un'istanza. `OptionPageGrid`chiamate <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A> per caricare le relative opzioni, che sono proprietà pubbliche.

2. Aggiungere ora un modello di elemento di comando personalizzato denominato **MyToolsOptionsCommand** per visualizzare il valore. Nella finestra di dialogo **Aggiungi nuovo elemento** passare a**Estensibilità** **di Visual C,** > quindi selezionare **Comando personalizzato**. Nel campo **Nome** nella parte inferiore della finestra modificare il nome del file di comando in *MyToolsOptionsCommand.cs*.

3. Nel file *MyToolsOptionsCommand* sostituire il corpo del `ShowMessageBox` metodo del comando con quanto segue:

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));
    }

    ```

4. Compilare il progetto e avviare il debug.

5. Nell'istanza sperimentale scegliere Richiama **MyToolsOptionsCommand**dal menu **Strumenti** .

     In una finestra di `OptionInteger`messaggio viene visualizzato il valore corrente di .

## <a name="see-also"></a>Vedere anche

- [Pagine opzioni e opzioni](../extensibility/internals/options-and-options-pages.md)
