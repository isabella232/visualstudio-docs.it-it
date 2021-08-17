---
title: 'Procedura: utilizzare procedure guidate con modelli di progetto'
description: Informazioni su come usare l'interfaccia IWizard in Visual Studio SDK, che consente di eseguire codice personalizzato quando un utente crea un progetto da un modello.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- project templates [Visual Studio], wizards
- Visual Studio templates, wizards
- wizards [Visual Studio], project templates
- templates [Visual Studio], wizards
- IWizard interface
ms.assetid: 47ee26cf-67b7-4ff1-8a9d-ab11a725405c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: cc023655c42ea63db5015d00a33ce140275f6ee0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122095062"
---
# <a name="how-to-use-wizards-with-project-templates"></a>Procedura: Usare le procedure guidate con i modelli di progetto

In Visual Studio è disponibile l'interfaccia <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> che, se implementata, consente di eseguire il codice personalizzato quando un utente crea un progetto da un modello.

Project personalizzazione del modello può essere usata per visualizzare l'interfaccia utente personalizzata che raccoglie l'input dell'utente per personalizzare il modello, aggiungere altri file al modello o qualsiasi altra azione consentita in un progetto.

I metodi di interfaccia vengono chiamati in diversi momenti durante la creazione del progetto, a partire dal momento in cui un utente fa clic su OK nella finestra <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> **di dialogo Project** nuova finestra di dialogo.  Ogni metodo dell'interfaccia viene denominato per descrivere il punto in cui viene chiamato. Ad esempio, Visual Studio chiama immediatamente quando inizia a creare il progetto, rendendo la posizione più utile per scrivere codice personalizzato per raccogliere <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> l'input dell'utente.

## <a name="create-a-project-template-project-with-a-vsix-project"></a>Creare un progetto modello di progetto con un progetto VSIX

Si inizia a creare un modello personalizzato con il progetto di modello di progetto, che fa parte di Visual Studio SDK. In questa procedura si userà un progetto di modello di progetto C#, ma è disponibile anche un progetto Visual Basic modello di progetto. Aggiungere quindi un progetto VSIX alla soluzione che contiene il progetto modello di progetto.

1. Creare un progetto modello di progetto C# (in Visual Studio selezionare **File**  >    >  **Nuovo Project** e cercare "modello di progetto". Assegnare al **progetto il nome MyProjectTemplate**.

   > [!NOTE]
   > Potrebbe essere richiesto di installare Visual Studio SDK. Per altre informazioni, vedere [Installazione di Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

2. Aggiungere un nuovo progetto VSIX nella stessa soluzione del progetto modello di progetto **(in Esplora soluzioni** selezionare il nodo della soluzione, fare clic con il pulsante destro del mouse e scegliere Aggiungi nuovo Project e cercare  >   "vsix"). Assegnare il **nome MyProjectWizard.**

3. Impostare il progetto VSIX come progetto di avvio. In **Esplora soluzioni** selezionare il nodo del progetto VSIX, fare clic con il pulsante destro del mouse e scegliere Imposta **come** Project .

4. Aggiungere il progetto modello come asset del progetto VSIX. In **Esplora soluzioni**, nel nodo del progetto VSIX, trovare il file *source.extension.vsixmanifest.* Fare doppio clic per aprirlo nell'editor manifesto.

5. Nell'editor del manifesto selezionare **la scheda Asset** sul lato sinistro della finestra.

6. Nella **scheda Asset** selezionare **Nuovo.** Nella finestra **Aggiungi nuovo asset** selezionare **Microsoft.VisualStudio.ProjectTemplate** nel campo Tipo. Nel campo **Origine** selezionare **Un progetto nella soluzione corrente.** Nel campo **Project** selezionare **MyProjectTemplate.** Quindi fare clic su **OK**.

7. Compilare la soluzione e avviare il debug. Verrà visualizzata una seconda istanza di Visual Studio. L'operazione potrebbe richiedere alcuni minuti.

8. Nella seconda istanza di Visual Studio, provare a creare un nuovo progetto con il nuovo modello (**File** Nuovo Project , cercare  >    >  "myproject". Il nuovo progetto dovrebbe essere visualizzato con una classe denominata **Class1.** A questo punto è stato creato un modello di progetto personalizzato. Arresta ora il debug.

## <a name="create-a-custom-template-wizard"></a>Creazione guidata modello personalizzato

Questa procedura illustra come creare una procedura guidata personalizzata che apre un form Windows prima della creazione del progetto. Il modulo consente agli utenti di aggiungere un valore di parametro personalizzato che viene aggiunto al codice sorgente durante la creazione del progetto.

1. Configurare il progetto VSIX per consentire la creazione di un assembly.

2. Nella **Esplora soluzioni** selezionare il nodo del progetto VSIX. Sotto **Esplora soluzioni** verrà visualizzata la **finestra** Proprietà. In caso contrario, selezionare **Visualizza**  >  **finestra Proprietà** o premere **F4.** Nella finestra **Proprietà** selezionare i campi seguenti per `true` :

   - **Includi assembly nel contenitore VSIX**

   - **Includere simboli di debug nel contenitore VSIX**

   - **Includere simboli di debug nella distribuzione VSIX locale**

3. Aggiungere l'assembly come asset al progetto VSIX. Aprire il file *source.extension.vsixmanifest* e selezionare la **scheda Asset.** Nella finestra Aggiungi nuovo  **asset,** per **Tipo** selezionare **Microsoft.VisualStudio.Assembly**, per Origine selezionare Un progetto nella soluzione corrente e per Project **selezionare MyProjectWizard.**  

4. Aggiungere i riferimenti seguenti al progetto VSIX. In **Esplora soluzioni**, nel nodo del progetto VSIX, selezionare **Riferimenti**, fare clic con il pulsante destro del mouse e **scegliere Aggiungi** riferimento. Nella scheda **Framework della**  finestra di dialogo Aggiungi riferimento individuare l'assembly **System.Windows Forms** e selezionarlo. Trovare e selezionare anche gli **assembly System** e **System.Drawing.** Selezionare ora la **scheda** Estensioni. Trovare **l'assembly EnvDTE** e selezionarlo. Trovare anche **l'assembly Microsoft.VisualStudio.TemplateWizardInterface** e selezionarlo. Fare clic su **OK**.

5. Aggiungere una classe per l'implementazione della procedura guidata al progetto VSIX. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo del progetto VSIX e scegliere **Aggiungi**, Quindi Nuovo **elemento** e **infine Classe.** Assegnare alla classe **il nome WizardImplementation**.

6. Sostituire il codice nel file *WizardImplementationClass.cs* con il codice seguente:

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

    **L'elemento UserInputForm** a cui si fa riferimento in questo codice verrà implementato in un secondo momento.

    La `WizardImplementation` classe contiene implementazioni del metodo per ogni membro di <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> . In questo esempio solo il <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> metodo esegue un'attività. Tutti gli altri metodi non eseranno alcuna operazione o restituiranno `true` .

    Il <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> metodo accetta quattro parametri:

   - Parametro <xref:System.Object> di cui è possibile eseguire il cast all'oggetto <xref:EnvDTE._DTE> radice, per consentire la personalizzazione del progetto.

   - Parametro <xref:System.Collections.Generic.Dictionary%602> che contiene una raccolta di tutti i parametri predefiniti nel modello. Per altre informazioni sui parametri del modello, vedere [Parametri del modello.](../ide/template-parameters.md)

   - Parametro <xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind> che contiene informazioni sul tipo di modello in uso.

   - Matrice <xref:System.Object> che contiene un set di parametri passati alla procedura guidata Visual Studio.

     In questo esempio viene aggiunto un valore di parametro dal form di input dell'utente al <xref:System.Collections.Generic.Dictionary%602> parametro . Ogni istanza del `$custommessage$` parametro nel progetto verrà sostituita con il testo immesso dall'utente.

7. Creare ora **l'oggetto UserInputForm.** Nel file *WizardImplementation.cs* aggiungere il codice seguente dopo la fine della `WizardImplementation` classe .

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

    Il modulo di input dell'utente fornisce un modulo semplice per l'immissione di un parametro personalizzato. Il form contiene una casella di testo denominata `textBox1` e un pulsante denominato `button1` . Quando si fa clic sul pulsante, il testo della casella di testo viene archiviato nel `customMessage` parametro .

## <a name="connect-the-wizard-to-the-custom-template"></a>Connessione la procedura guidata al modello personalizzato

Per consentire al modello di progetto personalizzato di usare la procedura guidata personalizzata, è necessario firmare l'assembly della procedura guidata e aggiungere alcune righe al modello di progetto personalizzato per sapere dove trovare l'implementazione della procedura guidata quando viene creato un nuovo progetto.

1. Firmare l'assembly. Nella finestra **Esplora soluzioni** selezionare il progetto VSIX, fare clic con il pulsante destro del mouse e **Project proprietà**.

2. Nella finestra **Project proprietà** selezionare la scheda **Firma.** Nella scheda **Firma** selezionare **Firma dell'assembly.** Nel campo **Scegliere un file di chiave con nome** sicuro selezionare **\<New>** . Nel campo Nome **file** **chiave della** finestra Crea chiave con nome sicuro digitare **key.snk**. Deselezionare il **campo Proteggi il file di chiave con una password.**

3. Nella finestra **Esplora soluzioni** selezionare il progetto VSIX e individuare la **finestra** Proprietà.

4. Impostare il **campo Copy Build Output to Output Directory (Copia output** compilazione nella directory di output) su **true.** In questo modo l'assembly può essere copiato nella directory di output quando la soluzione viene ricompilata. È ancora contenuto nel `.vsix` file . È necessario visualizzare l'assembly per individuarne la chiave di firma.

5. Ricompilare la soluzione.

6. È ora possibile trovare il file key.snk nella directory del progetto MyProjectWizard (*\<your disk location> \MyProjectTemplate\MyProjectWizard\key.snk*). Copiare il file *key.snk.*

7. Passare alla directory di output e trovare l'assembly (*\<your disk location> \MyProjectTemplate/MyProjectWizard\bin\Debug\MyProjectWizard.dll*). Incollare il file *key.snk* qui. Questa operazione non è assolutamente necessaria, ma semplifica i passaggi seguenti.

8. Aprire una finestra di comando e passare alla directory in cui è stato creato l'assembly.

9. Trovare lo *strumentosn.exe* firma del certificato. In un sistema operativo Windows 10 a 64 bit, ad esempio, un percorso tipico è il seguente:

     *C:\Programmi (x86)\Microsoft SDKs\Windows\v10.0A\bin\NETFX 4.6.1 Tools*

     Se non è possibile trovare lo strumento, provare a eseguire **dove /R . sn.exe** nella finestra di comando. Prendere nota del percorso.

10. Estrarre la chiave pubblica dal file *key.snk.* Nella finestra di comando digitare

     **\<location of sn.exe>\sn.exe -p key.snk outfile.key.**

     Non dimenticare di racchiudere il percorso del *sn.exe* tra virgolette se sono presenti spazi nei nomi di directory.

11. Ottenere il token di chiave pubblica dal file out:

     **\<location of sn.exe>\sn.exe -t outfile.key.**

     Anche in questo caso, non dimenticare le virgolette. Nell'output dovrebbe essere visualizzata una riga simile alla seguente

     **Il token di chiave pubblica è \<token>**

     Prendere nota di questo valore.

12. Aggiungere il riferimento alla procedura guidata personalizzata al file *con estensione vstemplate* del modello di progetto. Nel **Esplora soluzioni** trovare il file *denominato MyProjectTemplate.vstemplate* e aprirlo. Dopo la fine della \<TemplateContent> sezione aggiungere la sezione seguente:

    ```xml
    <WizardExtension>
        <Assembly>MyProjectWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=token</Assembly>
        <FullClassName>MyProjectWizard.WizardImplementation</FullClassName>
    </WizardExtension>
    ```

     Dove **MyProjectWizard** è il nome dell'assembly e **token** è il token copiato nel passaggio precedente.

13. Salvare tutti i file nel progetto e ricompilare.

## <a name="add-the-custom-parameter-to-the-template"></a>Aggiungere il parametro personalizzato al modello

In questo esempio il progetto utilizzato come modello visualizza il messaggio specificato nel modulo di input utente della procedura guidata personalizzata.

1. Nel **Esplora soluzioni** passare al progetto **MyProjectTemplate** e aprire *Class1.cs.*

2. Nel metodo `Main` dell'applicazione aggiungere la riga di codice seguente.

   ```csharp
   Console.WriteLine("$custommessage$");
   ```

    Il parametro `$custommessage$` viene sostituito con il testo immesso nel modulo di input dell'utente quando viene creato un progetto dal modello.

Ecco il file di codice completo prima che sia stato esportato in un modello.

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

## <a name="use-the-custom-wizard"></a>Usare la procedura guidata personalizzata

È ora possibile creare un progetto dal modello e usare la procedura guidata personalizzata.

1. Ricompilare la soluzione e avviare il debug. Verrà visualizzata una seconda istanza di Visual Studio.

2. Creare un nuovo progetto MyProjectTemplate. (**File**  >  **Nuovo**  >  **Project**).

3. Nella finestra **di dialogo Nuovo Project** cercare "myproject" per individuare il modello, digitare un nome e fare clic su **OK.**

     Verrà aperto il modulo di input dell'utente della procedura guidata.

4. Digitare un valore per il parametro personalizzato e fare clic sul pulsante .

     Il modulo di input utente della procedura guidata viene chiuso e viene creato un progetto dal modello.

5. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul file di codice sorgente e scegliere **Visualizza codice**.

     Si noti che `$custommessage$` è stato sostituito con il testo immesso nel modulo di input utente della procedura guidata.

## <a name="see-also"></a>Vedi anche

- <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>
- [Personalizzare i modelli](../ide/customizing-project-and-item-templates.md)
- [Elemento WizardExtension (Visual Studio modelli)](../extensibility/wizardextension-element-visual-studio-templates.md)
- [Pacchetti NuGet nei modelli di Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)
