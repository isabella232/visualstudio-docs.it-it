---
title: Creazione di una pagina opzioni | Microsoft Docs
description: Informazioni su come creare una semplice pagina Strumenti/Opzioni che usa una griglia delle proprietà per esaminare e impostare le proprietà.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], creating
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: e8ca8233495fd6db2d7a238483ef81a83b1ff28a5e59cb51f9075584bdcf9e27
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121434776"
---
# <a name="create-an-options-page"></a>Creare una pagina di opzioni

Questa procedura dettagliata crea una semplice pagina Strumenti/Opzioni che usa una griglia delle proprietà per esaminare e impostare le proprietà.

 Per salvare queste proprietà in e ripristinarle da un file di impostazioni, seguire questa procedura e quindi vedere [Creare una categoria di impostazioni.](../extensibility/creating-a-settings-category.md)

 MPF fornisce due classi che consentono di creare pagine opzioni degli strumenti, <xref:Microsoft.VisualStudio.Shell.Package> la classe e la classe <xref:Microsoft.VisualStudio.Shell.DialogPage> . Per creare un VSPackage per fornire un contenitore per queste pagine, creare una sottoclasse della `Package` classe . È possibile creare ogni pagina di opzioni degli strumenti derivando dalla `DialogPage` classe .

## <a name="prerequisites"></a>Prerequisiti

 A partire Visual Studio 2015, non si installa Visual Studio SDK dall'Area download. È incluso come funzionalità facoltativa nella configurazione Visual Studio configurazione. È anche possibile installare VS SDK in un secondo momento. Per altre informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-tools-options-grid-page"></a>Creare una pagina della griglia Opzioni strumenti

 In questa sezione viene creata una semplice griglia delle proprietà Opzioni strumenti. Questa griglia viene utilizzata per visualizzare e modificare il valore di una proprietà.

### <a name="to-create-the-vsix-project-and-add-a-vspackage"></a>Per creare il progetto VSIX e aggiungere un VSPackage

1. Ogni Visual Studio'estensione inizia con un progetto di distribuzione VSIX, che conterrà gli asset di estensione. Creare un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] progetto VSIX denominato `MyToolsOptionsExtension` . È possibile trovare il modello di progetto VSIX nella finestra **di dialogo Project** nuovo progetto cercando "vsix".

2. Aggiungere un VSPackage aggiungendo un modello di Visual Studio pacchetto denominato `MyToolsOptionsPackage` . Nella finestra **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo del progetto e **scegliere Aggiungi**  >  **nuovo elemento.** Nella finestra **di dialogo Aggiungi nuovo elemento** passare a Estendibilità degli elementi di **Visual C#** e selezionare Visual Studio  >   **pacchetto.** Nel campo **Nome** nella parte inferiore della finestra di dialogo modificare il nome del file in `MyToolsOptionsPackage.cs` . Per altre informazioni su come creare un VSPackage, vedere [Creare un'estensione con un VSPackage.](../extensibility/creating-an-extension-with-a-vspackage.md)

### <a name="to-create-the-tools-options-property-grid"></a>Per creare la griglia delle proprietà Opzioni strumenti

1. Aprire il file *MyToolsOptionsPackage nell'editor* del codice.

2. Aggiungere l'istruzione using seguente.

   ```csharp
   using System.ComponentModel;
   ```

3. Dichiarare una `OptionPageGrid` classe e derivarla da <xref:Microsoft.VisualStudio.Shell.DialogPage> .

   ```csharp
   public class OptionPageGrid : DialogPage
   {  }
   ```

4. Applicare un oggetto alla classe per assegnare alla classe una categoria di opzioni e il nome della <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> pagina delle opzioni per `VSPackage` OptionPageGrid. Il risultato dovrebbe essere simile al seguente:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [Guid(GuidList.guidMyToolsOptionsPkgString)]
    [ProvideOptionPage(typeof(OptionPageGrid),
        "My Category", "My Grid Page", 0, 0, true)]
    public sealed class MyToolsOptionsPackage : Package
    ```

5. Aggiungere `OptionInteger` una proprietà alla `OptionPageGrid` classe .

    - Applicare un <xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName> oggetto per assegnare alla proprietà una categoria della griglia delle proprietà.

    - Applicare un <xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName> oggetto per assegnare un nome alla proprietà.

    - Applicare un <xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName> oggetto per assegnare alla proprietà una descrizione.

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
    > L'implementazione predefinita di supporta proprietà che dispongono di convertitori appropriati o che sono strutture o matrici che possono essere espanse in proprietà <xref:Microsoft.VisualStudio.Shell.DialogPage> con convertitori appropriati. Per un elenco dei convertitori, vedere lo spazio dei <xref:System.ComponentModel> nomi .

6. Compilare il progetto e avviare il debug.

7. Nell'istanza sperimentale di Visual Studio scegliere Opzioni **dal** menu **Strumenti.**

     Nel riquadro sinistro dovrebbe essere visualizzato **Categoria.** Le categorie di opzioni sono elencate in ordine alfabetico, quindi dovrebbero essere visualizzate a metà dell'elenco. Aprire **My Category e** quindi fare clic su My Grid **Page**. La griglia delle opzioni viene visualizzata nel riquadro destro. La categoria di proprietà **è My Options** e il nome della proprietà è My Integer **Option**. La descrizione della **proprietà, Opzione Numero intero,** viene visualizzata nella parte inferiore del riquadro. Modificare il valore iniziale di 256 in un altro valore. Fare **clic su OK** e quindi **riaprire My Grid Page**. Come si può vedere, il nuovo valore viene mantenuto.

     La pagina delle opzioni è disponibile anche Visual Studio casella di ricerca della pagina. Nella casella di ricerca nella parte superiore dell'IDE digitare **Categoria.** Nei risultati verrà visualizzato My **Category -> My Grid Page** (Categoria -> Pagina griglia).

## <a name="create-a-tools-options-custom-page"></a>Creare una pagina personalizzata di Opzioni degli strumenti

 In questa sezione viene creata una pagina Opzioni strumenti con un'interfaccia utente personalizzata. Usare questa pagina per visualizzare e modificare il valore di una proprietà.

1. Aprire il file *MyToolsOptionsPackage nell'editor* del codice.

2. Aggiungere l'istruzione using seguente.

    ```csharp
    using System.Windows.Forms;
    ```

3. Aggiungere una `OptionPageCustom` classe , subito prima della classe `OptionPageGrid` . Derivare la nuova classe da `DialogPage` .

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

5. Applicare un secondo <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> alla classe VSPackage. Questo attributo assegna alla classe una categoria di opzioni e un nome di pagina delle opzioni.

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

6. Aggiungere un **nuovo controllo utente** denominato MyUserControl al progetto.

7. Aggiungere un **controllo TextBox** al controllo utente.

     Nella finestra **Proprietà** fare clic sul pulsante **Eventi** sulla barra degli strumenti e quindi fare doppio clic sull'evento **Leave.** Il nuovo gestore eventi viene visualizzato nel *codice MyUserControl.cs.*

8. Aggiungere un campo pubblico, un metodo alla classe del controllo e aggiornare il gestore eventi per impostare il valore dell'opzione `OptionsPage` sul contenuto della casella di `Initialize` testo:

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

     Il `optionsPage` campo contiene un riferimento all'istanza `OptionPageCustom` padre. Il `Initialize` metodo viene visualizzato `OptionString` nell'oggetto **TextBox.** Il gestore eventi scrive il valore corrente dell'oggetto **TextBox** nell'oggetto quando `OptionString` lo stato attivo lascia **l'oggetto TextBox.**

9. Nel file di codice del pacchetto aggiungere un override per la proprietà alla classe per `OptionPageCustom.Window` `OptionPageCustom` creare, inizializzare e restituire un'istanza di `MyUserControl` . La classe dovrebbe ora essere simile alla seguente:

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

11. Nell'istanza sperimentale fare clic **su Strumenti**  >  **Opzioni**.

12. Trovare **Categoria e** quindi Pagina **personalizzata.**

13. Modificare il valore di **OptionString**. Fare **clic su OK** e quindi **riaprire Pagina personalizzata.** È possibile vedere che il nuovo valore è persistente.

## <a name="access-options"></a>Opzioni di accesso

 In questa sezione si ottiene il valore di un'opzione dal pacchetto VSPackage che ospita la pagina Opzioni strumenti associata. La stessa tecnica può essere usata per ottenere il valore di qualsiasi proprietà pubblica.

1. Nel file di codice del pacchetto aggiungere una proprietà pubblica denominata **OptionInteger** alla **classe MyToolsOptionsPackage.**

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

     Questo codice chiama <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> per creare o recuperare un'istanza di `OptionPageGrid` . `OptionPageGrid` chiama <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A> per caricare le opzioni, che sono proprietà pubbliche.

2. Aggiungere ora un modello di elemento di comando personalizzato **denominato MyToolsOptionsCommand per** visualizzare il valore. Nella finestra **di dialogo Aggiungi nuovo** elemento passare a **Estendibilità di Visual C#**  >   e selezionare **Comando personalizzato.** Nel campo **Nome** nella parte inferiore della finestra modificare il nome del file di comando in *MyToolsOptionsCommand.cs*.

3. Nel file *MyToolsOptionsCommand* sostituire il corpo del metodo del `ShowMessageBox` comando con il codice seguente:

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));
    }

    ```

4. Compilare il progetto e avviare il debug.

5. Nell'istanza sperimentale scegliere Richiama **MyToolsOptionsCommand** dal menu Strumenti. 

     In una finestra di messaggio viene visualizzato il valore corrente di `OptionInteger` .

## <a name="see-also"></a>Vedi anche

- [Opzioni e pagine di opzioni](../extensibility/internals/options-and-options-pages.md)
