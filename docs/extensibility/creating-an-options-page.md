---
title: Creazione di una pagina di opzioni | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], creating
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6100f6b0a793b138712250ac5451454784bc877a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49876750"
---
# <a name="create-an-options-page"></a>Creare una pagina di opzioni
Questa procedura dettagliata crea una pagina di strumenti/opzioni semplice che utilizza una griglia delle proprietà per esaminare e impostare le proprietà.  
  
 Per salvare queste proprietà a e il ripristino da un file di impostazioni, seguire questa procedura e quindi [creare una categoria di impostazioni](../extensibility/creating-a-settings-category.md).  
  
 MPF fornisce due classi per la creazione di pagine Opzioni del menu Strumenti, il <xref:Microsoft.VisualStudio.Shell.Package> classi e <xref:Microsoft.VisualStudio.Shell.DialogPage> classe. Si crea un pacchetto VSPackage per fornire un contenitore per queste pagine creando sottoclassi di `Package` classe. Si crea ogni pagina di opzioni degli strumenti mediante la derivazione da di `DialogPage` classe.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-tools-options-grid-page"></a>Creare una pagina della griglia di opzioni del menu Strumenti  
 In questa sezione è creare una griglia delle proprietà di semplice opzioni del menu Strumenti. Utilizzare questa griglia per visualizzare e modificare il valore di una proprietà.  
  
### <a name="to-create-the-vsix-project-and-add-a-vspackage"></a>Per creare il progetto VSIX e aggiungere un pacchetto VSPackage  
  
1. Ogni estensione di Visual Studio inizia con un progetto di distribuzione VSIX che contiene gli asset di estensione. Creare un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] progetto VSIX denominato `MyToolsOptionsExtension`. È possibile trovare il modello di progetto VSIX nel **nuovo progetto** nella finestra di dialogo **Visual c#** > **estendibilità**.  
  
2. Aggiungere un pacchetto VSPackage mediante l'aggiunta di un modello di elemento di pacchetto di Visual Studio denominato `MyToolsOptionsPackage`. Nel **Esplora soluzioni**, fare doppio clic sul nodo del progetto e selezionare **Add** > **nuovo elemento**. Nel **finestra di dialogo Aggiungi nuovo elemento**, passare a **elementi di Visual c#** > **Extensibility** e selezionare **pacchetto di Visual Studio**. Nel **Name** campo nella parte inferiore della finestra di dialogo, modificare il nome del file per `MyToolsOptionsPackage.cs`. Per altre informazioni su come creare un pacchetto VSPackage, vedere [creare un'estensione con un pacchetto VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md).  
  
### <a name="to-create-the-tools-options-property-grid"></a>Per creare la griglia delle proprietà di opzioni del menu Strumenti  
  
1.  Aprire il *MyToolsOptionsPackage* file nell'editor del codice.  
  
2.  Aggiungere la seguente istruzione using.  
  
    ```csharp  
    using System.ComponentModel;  
    ```  
  
3.  Dichiarare un `OptionPageGrid` classe eccezione e derivarla dalla <xref:Microsoft.VisualStudio.Shell.DialogPage>.  
  
    ```csharp  
    public class OptionPageGrid : DialogPage  
    {  }  
    ```  
  
4.  Applicare una <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> per il `VSPackage` classe da assegnare alla classe, una categoria di opzioni e il nome di pagina Opzioni per il OptionPageGrid. Il risultato dovrebbe essere simile al seguente:  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [Guid(GuidList.guidMyToolsOptionsPkgString)]  
    [ProvideOptionPage(typeof(OptionPageGrid),  
        "My Category", "My Grid Page", 0, 0, true)]  
    public sealed class MyToolsOptionsPackage : Package  
    ```  
  
5.  Aggiungere un `OptionInteger` proprietà per il `OptionPageGrid` classe.  
  
    -   Applicare un <xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName> da assegnare alla proprietà di una categoria di griglia di proprietà.  
  
    -   Applicare un <xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName> assegnare alla proprietà un nome.  
  
    -   Applicare un <xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName> da assegnare alla proprietà di una descrizione.  
  
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
    >  L'implementazione predefinita di <xref:Microsoft.VisualStudio.Shell.DialogPage> supporta le proprietà che dispongono di convertitori appropriati o che sono strutture o matrici che possono essere espansi all'interno delle proprietà che dispongono di convertitori appropriati. Per un elenco dei convertitori di tipi, vedere il <xref:System.ComponentModel> dello spazio dei nomi.  
  
6.  Compilare il progetto e avviare il debug.  
  
7.  Nell'istanza sperimentale di Visual Studio, sul **degli strumenti** menu fare clic su **opzioni**.  
  
     Nel riquadro di sinistra dovrebbe **My Category**. (Opzioni categorie sono elencate in ordine alfabetico, pertanto dovrebbe essere presente sulla metà l'elenco a discesa.) Aprire **My Category** e quindi fare clic su **My pagina della griglia**. Nel riquadro di destra viene visualizzata la griglia di opzioni. La categoria della proprietà viene **My Options**, e il nome della proprietà viene **My opzione Integer**. La descrizione della proprietà, **l'opzione integer**, viene visualizzato nella parte inferiore del riquadro. Modificare il valore dal valore iniziale pari a 256 per qualcos'altro. Fare clic su **OK**e quindi riaprire **My pagina della griglia**. È possibile vedere che il nuovo valore viene mantenuto.  
  
     La pagina delle opzioni è disponibile anche tramite avvio veloce di Visual Studio. Nella finestra avvio veloce nell'angolo superiore destro dell'IDE, digitare **My Category** e verrà visualizzato **My Category -> pagina della griglia My** elencati nell'elenco a discesa.  
  
## <a name="create-a-tools-options-custom-page"></a>Creare una pagina di opzioni del menu strumenti personalizzata  
 In questa sezione è creare una pagina di opzioni degli strumenti con un'interfaccia utente personalizzata. Utilizzare questa pagina per visualizzare e modificare il valore di una proprietà.  
  
1.  Aprire il *MyToolsOptionsPackage* file nell'editor del codice.  
  
2.  Aggiungere la seguente istruzione using.  
  
    ```vb  
    using System.Windows.Forms;  
    ```  
  
3.  Aggiungere un `OptionPageCustom` classe, appena prima di `OptionPageGrid` classe. La nuova classe da derivare `DialogPage`.  
  
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
  
4.  Aggiungere un attributo GUID. Aggiungere una proprietà OptionString:  
  
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
  
5.  Applicare un secondo <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> alla classe VSPackage. Questo attributo assegna la classe di una categoria di opzioni e il nome di pagina di opzioni.  
  
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
  
6.  Aggiungere un nuovo **controllo utente** denominato MyUserControl al progetto.  
  
7.  Aggiungere un **casella di testo** nel controllo utente.  
  
     Nel **proprietà** finestra, sulla barra degli strumenti fare clic sulla **eventi** pulsante e quindi fare doppio clic il **lasciare** evento. Il nuovo gestore eventi viene visualizzato nei *MyUserControl.cs* codice.  
  
8.  Aggiungere un pubblico `OptionsPage` campo, un `Initialize` metodo alla classe di controllo, e aggiornare il gestore eventi per impostare l'opzione valore per il contenuto della casella di testo:  
  
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
  
     Il `optionsPage` campo contiene un riferimento all'elemento padre `OptionPageCustom` istanza. Il `Initialize` metodo consente di visualizzare `OptionString` nel **nella casella di testo**. Il gestore eventi scrive il valore corrente del **casella di testo** per il `OptionString` quando lo stato attivo lascia il **casella di testo**.  
  
9. Nel file di codice del pacchetto, aggiungere una sostituzione per il `OptionPageCustom.Window` proprietà per il `OptionPageCustom` per creare, inizializzare e restituire un'istanza della classe `MyUserControl`. La classe dovrebbe ora essere simile al seguente:  
  
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
  
11. Nell'istanza sperimentale, fare clic su **degli strumenti** > **opzioni**.  
  
12. Trovare **del nome della categoria** e quindi **My Custom pagina**.  
  
13. Modificare il valore della **OptionString**. Fare clic su **OK**e quindi riaprire **My Custom pagina**. È possibile vedere che il nuovo valore è resa persistente.  
  
## <a name="access-options"></a>Opzioni di accesso  
 In questa sezione ottenere il valore di un'opzione dal pacchetto VSPackage che ospita la pagina di opzioni degli strumenti associata. La stessa tecnica è utilizzabile per ottenere il valore di qualsiasi proprietà pubblica.  
  
1.  Nel file di codice del pacchetto, aggiungere una proprietà pubblica denominata **OptionInteger** per il **MyToolsOptionsPackage** classe.  
  
    ```  
    public int OptionInteger  
    {  
        get  
        {  
            OptionPageGrid page = (OptionPageGrid)GetDialogPage(typeof(OptionPageGrid));  
            return page.OptionInteger;  
        }  
    }  
  
    ```  
  
     Questo codice viene chiamato <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> per creare o recuperare un `OptionPageGrid` istanza. `OptionPageGrid` le chiamate <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A> per caricare le relative opzioni, che sono proprietà pubbliche.  
  
2.  A questo punto aggiungere un modello di elemento di comando personalizzato denominato **MyToolsOptionsCommand** per visualizzare il valore. Nel **Aggiungi nuovo elemento** finestra di dialogo passa alla **Visual c#** > **Extensibility** e selezionare **comando personalizzato**. Nel **Name** campo nella parte inferiore della finestra, modificare il nome di file di comando da *MyToolsOptionsCommand.cs*.  
  
3.  Nel *MyToolsOptionsCommand* del file, sostituire il corpo del comando `ShowMessageBox` metodo con il codice seguente:  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;  
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));  
    }  
  
    ```  
  
4.  Compilare il progetto e avviare il debug.  
  
5.  Nell'istanza sperimentale, sul **degli strumenti** menu, fare clic su **MyToolsOptionsCommand richiamare**.  
  
     Una finestra di messaggio Visualizza il valore corrente di `OptionInteger`.  
  
## <a name="see-also"></a>Vedere anche  
 [Opzioni e le pagine di opzioni](../extensibility/internals/options-and-options-pages.md)