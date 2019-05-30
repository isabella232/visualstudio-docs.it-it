---
title: 'Procedura: Usare procedure guidate con modelli di progetto'
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- project templates [Visual Studio], wizards
- Visual Studio templates, wizards
- wizards [Visual Studio], project templates
- templates [Visual Studio], wizards
- IWizard interface
ms.assetid: 47ee26cf-67b7-4ff1-8a9d-ab11a725405c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 366244285892820039a5a0f7950a709d170b4527
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352038"
---
# <a name="how-to-use-wizards-with-project-templates"></a>Procedura: Usare le procedure guidate con modelli di progetto

In Visual Studio è disponibile l'interfaccia <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> che, se implementata, consente di eseguire il codice personalizzato quando un utente crea un progetto da un modello.

Personalizzazione di modelli di progetto è utilizzabile per visualizzare l'interfaccia utente personalizzata che raccoglie l'input per personalizzare il modello, aggiungere ulteriori file al modello dell'utente, o qualsiasi altra azione consentita in un progetto.

Il <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> metodi di interfaccia vengono chiamati in vari momenti durante il progetto viene creato, avvio, non appena un utente fa clic su **OK** sul **nuovo progetto** nella finestra di dialogo. Ogni metodo dell'interfaccia è denominato per descrivere il punto in cui viene chiamato. Ad esempio, Visual Studio chiama <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> non appena viene avviata creare il progetto, rendendola una posizione ideale per scrivere codice personalizzato per raccogliere l'input dell'utente.

## <a name="create-a-project-template-project-with-a-vsix-project"></a>Creare un progetto di modello di progetto con un progetto VSIX

Iniziare a creare un modello personalizzato con il progetto di modello di progetto, che fa parte di Visual Studio SDK. In questa procedura si userà un C# progetto di modello di progetto, ma è inoltre disponibile un progetto di modello di progetto Visual Basic. Quindi si aggiunge un progetto VSIX per la soluzione che contiene il progetto di modello di progetto.

1. Creare un C# progetto di modello di progetto (in Visual Studio, selezionare **File** > **New** > **progetto** e cercare "modello di progetto" ). Denominarlo **MyProjectTemplate**.

   > [!NOTE]
   > Potrebbe essere necessario installare Visual Studio SDK. Per altre informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

2. Aggiungere un nuovo progetto VSIX nella stessa soluzione come progetto di modello di progetto (in **Esplora soluzioni**, selezionare il nodo della soluzione, pulsante destro del mouse e selezionare **Add** > **nuovo progetto**  e cercare "vsix"). Denominarla **MyProjectWizard.**

3. Impostare il progetto VSIX come progetto di avvio. Nelle **Esplora soluzioni**, selezionare il nodo del progetto VSIX, pulsante destro del mouse e selezionare **imposta come progetto di avvio**.

4. Aggiungere il progetto di modello come un asset del progetto VSIX. Nelle **Esplora soluzioni**, nel nodo del progetto VSIX, trovare il *vsixmanifest* file. Fare doppio clic su esso per aprirlo nell'editor del manifesto.

5. Nell'editor del manifesto, selezionare la **asset** scheda sul lato sinistro della finestra.

6. Nel **Assets** scheda, seleziona **New**. Nel **Aggiungi nuovo Asset** finestra, per il campo di tipo, seleziona **Microsoft.VisualStudio.ProjectTemplate**. Nel **origine** campi, selezionare **un progetto nella soluzione corrente**. Nel **Project** campi, selezionare **MyProjectTemplate**. Fare quindi clic su **OK**.

7. Compilare la soluzione e avviare il debug. Verrà visualizzata una seconda istanza di Visual Studio. (L'operazione potrebbe richiedere alcuni minuti).

8. Nella seconda istanza di Visual Studio, provare a creare un nuovo progetto con il nuovo modello (**File** > **New** > **progetto**, cercare " MyProject"). Il nuovo progetto verrà visualizzato con una classe denominata **Class1**. È stato creato un modello di progetto personalizzato. Arrestare il debug.

## <a name="create-a-custom-template-wizard"></a>Creazione guidata di un modello personalizzato

Questa procedura viene illustrato come creare una procedura guidata personalizzata che consente di aprire un modulo di Windows prima che venga creato il progetto. Il form consente agli utenti di aggiungere un valore del parametro personalizzato che viene aggiunto al codice sorgente durante la creazione del progetto.

1. Configurare il progetto VSIX per consentirgli di creare un assembly.

2. Nelle **Esplora soluzioni**, selezionare il nodo del progetto VSIX. Di seguito **Esplora soluzioni**, verrà visualizzato il **proprietà** finestra. In caso contrario, selezionare **View** > **finestra delle proprietà**, oppure premere **F4**. Nel **delle proprietà** finestra, seleziona i seguenti campi per `true`:

   - **IncludeAssemblyInVSIXContainer**

   - **IncludeDebugSymbolsInVSIXContainer**

   - **IncludeDebugSymbolsInLocalVSIXDeployment**

3. Aggiungere l'assembly come un asset per il progetto VSIX. Aprire il *vsixmanifest* del file e selezionare il **asset** scheda. Nel **Aggiungi nuovo Asset** finestra, per **tipo** seleziona **Microsoft.VisualStudio.Assembly**, per **origine** selezionare **A progetto nella soluzione corrente**e per **Project** seleziona **MyProjectWizard**.

4. Aggiungere i riferimenti seguenti al progetto VSIX. (In **Esplora soluzioni**, nel nodo del progetto VSIX, selezionare **riferimenti**, pulsante destro del mouse e selezionare **Aggiungi riferimento**.) Nel **Aggiungi riferimento** finestra di dialogo, nella **Framework** scheda, trovare il **System. Windows Forms** assembly e selezionarlo. A questo punto selezionare i **estensioni** scheda. Trovare il **EnvDTE** assembly e selezionarlo. Individuare anche il **Microsoft.VisualStudio.TemplateWizardInterface** assembly e selezionarlo. Fare clic su **OK**.

5. Aggiungere una classe per l'implementazione della procedura guidata per il progetto VSIX. (In **Esplora soluzioni**, fare doppio clic sul nodo del progetto VSIX e selezionare **Add**, quindi **nuovo elemento**, quindi **classe**.) Denominare la classe **WizardImplementation**.

6. Sostituire il codice nel *WizardImplementationClass.cs* file con il codice seguente:

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.VisualStudio.TemplateWizard;
   using System.Windows.Forms;
   using EnvDTE;

   namespace MyProjectWizard
   {
       public class WizardImplementation:IWizard
       {
           private UserInputForm inputForm;
           private string customMessage;

           // This method is called before opening any item that
           // has the OpenInEditor attribute.
           public void BeforeOpeningFile(ProjectItem projectItem)
           {
           }

           public void ProjectFinishedGenerating(Project project)
           {
           }

           // This method is only called for item templates,
           // not for project templates.
           public void ProjectItemFinishedGenerating(ProjectItem
               projectItem)
           {
           }

           // This method is called after the project is created.
           public void RunFinished()
           {
           }

           public void RunStarted(object automationObject,
               Dictionary<string, string> replacementsDictionary,
               WizardRunKind runKind, object[] customParams)
           {
               try
               {
                   // Display a form to the user. The form collects
                   // input for the custom message.
                   inputForm = new UserInputForm();
                   inputForm.ShowDialog();

                   customMessage = UserInputForm.CustomMessage;

                   // Add custom parameters.
                   replacementsDictionary.Add("$custommessage$",
                       customMessage);
               }
               catch (Exception ex)
               {
                   MessageBox.Show(ex.ToString());
               }
           }

           // This method is only called for item templates,
           // not for project templates.
           public bool ShouldAddProjectItem(string filePath)
           {
               return true;
           }
       }
   }
   ```

    Il **UserInputForm** cui viene fatto riferimento in questo codice verrà implementato in un secondo momento.

    Il `WizardImplementation` classe contiene le implementazioni del metodo per ogni membro del <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>. In questo esempio, solo il <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> metodo esegue un'attività. Tutti gli altri metodi non esegue alcuna operazione o restituiscono `true`.

    Il <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> metodo accetta quattro parametri:

   - Un' <xref:System.Object> parametro che può essere convertito in radice <xref:EnvDTE._DTE> oggetto, che consentono di personalizzare il progetto.

   - Oggetto <xref:System.Collections.Generic.Dictionary%602> parametro contenente una raccolta di tutti i parametri predefiniti nel modello. Per altre informazioni sui parametri dei modelli, vedere [parametri di modello](../ide/template-parameters.md).

   - Oggetto <xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind> parametro che contiene informazioni sul tipo di modello è in uso.

   - Un <xref:System.Object> matrice che contiene un set di parametri passati alla procedura guidata da Visual Studio.

     Questo esempio viene aggiunto un valore del parametro di input dell'utente per il <xref:System.Collections.Generic.Dictionary%602> parametro. Tutte le istanze del `$custommessage$` parametro del progetto verrà sostituito con il testo immesso dall'utente. Aggiungere al progetto gli assembly seguenti: **System** e **System. Drawing**.

7. A questo punto creare il **UserInputForm**. Nel *WizardImplementation.cs* , aggiungere il codice seguente dopo la fine del `WizardImplementation` classe.

   ```csharp
   public partial class UserInputForm : Form
       {
           private static string customMessage;
           private TextBox textBox1;
           private Button button1;

           public UserInputForm()
           {
               this.Size = new System.Drawing.Size(155, 265);

               button1 = new Button();
               button1.Location = new System.Drawing.Point(90, 25);
               button1.Size = new System.Drawing.Size(50, 25);
               button1.Click += button1_Click;
               this.Controls.Add(button1);

               textBox1 = new TextBox();
               textBox1.Location = new System.Drawing.Point(10, 25);
               textBox1.Size = new System.Drawing.Size(70, 20);
               this.Controls.Add(textBox1);
           }
           public static string CustomMessage
           {
               get
               {
                   return customMessage;
               }
               set
               {
                   customMessage = value;
               }
           }
           private void button1_Click(object sender, EventArgs e)
           {
               customMessage = textBox1.Text;
               this.Close();
           }
       }
   ```

    Il modulo di input utente fornisce un semplice modulo per l'immissione di un parametro personalizzato. Il form contiene una casella di testo denominata `textBox1` e un pulsante denominato `button1`. Quando si fa clic sul pulsante, il testo dalla casella di testo viene archiviato nel `customMessage` parametro.

## <a name="connect-the-wizard-to-the-custom-template"></a>Connettere la procedura guidata per il modello personalizzato

Affinché il modello di progetto personalizzati da usare della procedura guidata, è necessario firmare l'assembly della procedura guidata e aggiungere alcune righe al modello di progetto personalizzati per consentire a saprà dove trovare l'implementazione della procedura guidata quando viene creato un nuovo progetto.

1. Firmare l'assembly. Nel **Esplora soluzioni**, selezionare il progetto VSIX, pulsante destro del mouse e selezionare **proprietà progetto**.

2. Nel **le proprietà del progetto** finestra, seleziona la **Signing** scheda. nel **firma** scheda **firmare l'assembly**. Nel **Scegli un file chiave con nome sicuro** campi, selezionare  **\<New >** . Nel **Crea chiave con nome sicuro** finestra, nelle **nome file di chiave** digitare **snk**. Deselezionare i **Proteggi file di chiave con una password** campo.

3. Nel **Esplora soluzioni**, selezionare il progetto VSIX e trovare il **proprietà** finestra.

4. Impostare il **Directory di Output nell'Output di compilazione copia** campo **true**. In questo modo l'assembly deve essere copiato nella directory di output quando viene ricompilata la soluzione. È ancora inclusa nel `.vsix` file. È necessario visualizzare l'assembly per stabilire la relativa chiave di firma.

5. Ricompilare la soluzione.

6. È ora possibile trovare il file Key. snk nella directory del progetto MyProjectWizard ( *\<il percorso del disco > \MyProjectTemplate\MyProjectWizard\key.snk*). Copia il *snk* file.

7. Passare alla directory di output e trovare l'assembly ( *\<il percorso del disco > \MyProjectTemplate/MyProjectWizard\bin\Debug\MyProjectWizard.dll*). Incollare il *snk* file qui. (Questo non è assolutamente necessario, ma per facilitare la procedura seguente).

8. Aprire una finestra di comando e passare alla directory in cui è stato creato l'assembly.

9. Trovare il *sn.exe* strumento firma digitale. Ad esempio, in un sistema operativo a 64 bit di Windows 10, un tipico percorso sarà il seguente:

     *C:\Programmi (x86) \Microsoft SDKs\Windows\v10.0A\bin\NETFX 4.6.1 Tools*

     Se non si trova lo strumento, provare a eseguire **in cui /R. sn.exe** nella finestra di comando. Prendere nota del percorso.

10. Estrarre la chiave pubblica dal *snk* file. Nella finestra di comando, digitare

     **\<posizione del sn.exe > \sn.exe -p snk outfile.key.**

     Non dimenticare di racchiudere il percorso del *sn.exe* tra virgolette se sono presenti spazi nei nomi di directory.

11. Ottenere il token di chiave pubblica dal file di output:

     **\<posizione del sn.exe > \sn.exe -t outfile.key.**

     Anche in questo caso, non dimenticare le virgolette. Si dovrebbe essere visualizzata una riga nell'output simile al seguente

     **Token di chiave pubblica è \<token >**

     Prendere nota di questo valore.

12. Aggiungere il riferimento per la creazione guidata personalizzata per il *vstemplate* file del modello di progetto. Nel **Esplora soluzioni**, trovare il file denominato *MyProjectTemplate.vstemplate*e aprirlo. Dopo la fine del \<TemplateContent >, quindi aggiungere la sezione seguente:

    ```xml
    <WizardExtension>
        <Assembly>MyProjectWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=token</Assembly>
        <FullClassName>MyProjectWizard.WizardImplementation</FullClassName>
    </WizardExtension>
    ```

     In cui **MyProjectWizard** è il nome dell'assembly, e **token** è il token è stato copiato nel passaggio precedente.

13. Salvare tutti i file nel progetto e ricompilare.

## <a name="add-the-custom-parameter-to-the-template"></a>Aggiungere il parametro personalizzato per il modello

In questo esempio, il progetto usato come modello viene visualizzato il messaggio specificato nell'input dell'utente della procedura guidata personalizzata.

1. Nel **Esplora soluzioni**, visitare il **MyProjectTemplate** del progetto e aprire *Class1.cs*.

2. Nel `Main` metodo dell'applicazione, aggiungere la riga di codice seguente.

   ```csharp
   Console.WriteLine("$custommessage$");
   ```

    Il parametro `$custommessage$` viene sostituito con il testo immesso negli input dell'utente quando viene creato un progetto dal modello.

Ecco il file di codice completo prima che è stato esportato in un modello.

```csharp
using System;
using System.Collections.Generic;
$if$ ($targetframeworkversion$ >= 3.5)using System.Linq;
$endif$using System.Text;

namespace $safeprojectname$
{
    public class Class1
    {
          static void Main(string[] args)
          {
               Console.WriteLine("$custommessage$");
          }
    }
}
```

## <a name="use-the-custom-wizard"></a>Utilizzare la procedura guidata personalizzata

A questo punto è possibile creare un progetto dal modello e utilizzare la procedura guidata personalizzata.

1. Ricompilare la soluzione e avviare il debug. Verrà visualizzata una seconda istanza di Visual Studio.

2. Creare un nuovo progetto MyProjectTemplate. (**File** > **nuova** > **progetto**).

3. Nel **nuovo progetto** finestra di dialogo, cercare "myproject" individuare il modello, digitare un nome e fare clic su **OK**.

     Verrà visualizzata la procedura guidata input dell'utente.

4. Digitare un valore per il parametro personalizzato e fare clic sul pulsante.

     Il modulo di input utente guidata si chiude e viene creato un progetto dal modello.

5. Nelle **Esplora soluzioni**, fare clic sul file del codice sorgente e fare clic su **Visualizza codice**.

     Si noti che `$custommessage$` è stata sostituita con il testo immesso nella procedura guidata input dell'utente.

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>
- [Personalizzare i modelli](../ide/customizing-project-and-item-templates.md)
- [Elemento WizardExtension (modelli di Visual Studio)](../extensibility/wizardextension-element-visual-studio-templates.md)
- [Pacchetti NuGet nei modelli di Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)