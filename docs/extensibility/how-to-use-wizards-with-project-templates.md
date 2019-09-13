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
ms.openlocfilehash: 51c89fb82985d37b106f352047bfce74503f3c48
ms.sourcegitcommit: b60a00ac3165364ee0e53f7f6faef8e9fe59ec4a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/11/2019
ms.locfileid: "70913109"
---
# <a name="how-to-use-wizards-with-project-templates"></a>Procedura: Usare procedure guidate con modelli di progetto

In Visual Studio è disponibile l'interfaccia <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> che, se implementata, consente di eseguire il codice personalizzato quando un utente crea un progetto da un modello.

La personalizzazione del modello di progetto può essere usata per visualizzare un'interfaccia utente personalizzata che raccoglie l'input dell'utente per personalizzare il modello, aggiungere altri file al modello o qualsiasi altra azione consentita su un progetto.

I <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> metodi di interfaccia vengono chiamati in diversi momenti durante la creazione del progetto, a partire dal momento in cui un utente fa clic su **OK** nella finestra di dialogo **nuovo progetto** . Ogni metodo dell'interfaccia è denominato per descrivere il punto in cui viene chiamato. Ad esempio, Visual Studio chiama <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> immediatamente quando inizia a creare il progetto, rendendolo un percorso valido per la scrittura di codice personalizzato per raccogliere l'input dell'utente.

## <a name="create-a-project-template-project-with-a-vsix-project"></a>Creare un progetto di modello di progetto con un progetto VSIX

Si inizia a creare un modello personalizzato con il progetto di modello di progetto, che fa parte di Visual Studio SDK. In questa procedura verrà usato un C# progetto di modello di progetto, ma è disponibile anche un progetto di modello di progetto Visual Basic. Aggiungere quindi un progetto VSIX alla soluzione che contiene il progetto di modello di progetto.

1. Creare un C# progetto di modello di progetto (in Visual Studio, selezionare **file** > **nuovo** > **progetto** e cercare "modello progetto"). Denominarlo **MyProjectTemplate**.

   > [!NOTE]
   > Potrebbe essere richiesto di installare Visual Studio SDK. Per ulteriori informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

2. Aggiungere un nuovo progetto VSIX nella stessa soluzione del progetto di modello di progetto (in **Esplora soluzioni**, selezionare il nodo della soluzione, fare clic con il pulsante destro del mouse e scegliere **Aggiungi** > **nuovo progetto** e cercare "VSIX"). Denominarlo **MyProjectWizard.**

3. Impostare il progetto VSIX come progetto di avvio. In **Esplora soluzioni**selezionare il nodo progetto VSIX, fare clic con il pulsante destro del mouse e scegliere **Imposta come progetto di avvio**.

4. Aggiungere il progetto modello come asset del progetto VSIX. In **Esplora soluzioni**, nel nodo progetto VSIX, trovare il file *source. Extension. vsixmanifest* . Fare doppio clic su di esso per aprirlo nell'editor manifesto.

5. Nell'editor del manifesto selezionare la scheda **Asset** sul lato sinistro della finestra.

6. Nella scheda **Asset** selezionare **nuovo**. Nella finestra **Aggiungi nuovo asset** selezionare **Microsoft. VisualStudio. ProjectTemplate**per il campo tipo. Nel campo **origine** selezionare **un progetto nella soluzione corrente**. Nel campo **progetto** selezionare **MyProjectTemplate**. Fare quindi clic su **OK**.

7. Compilare la soluzione e avviare il debug. Verrà visualizzata una seconda istanza di Visual Studio. (L'operazione potrebbe richiedere alcuni minuti).

8. Nella seconda istanza di Visual Studio, provare a creare un nuovo progetto con il nuovo modello (**file** > **nuovo** > **progetto**, cercare "MyProject"). Il nuovo progetto dovrebbe essere visualizzato con una classe denominata **Class1**. A questo punto è stato creato un modello di progetto personalizzato. Arrestare il debug adesso.

## <a name="create-a-custom-template-wizard"></a>Creazione guidata modello personalizzato

Questa procedura illustra come creare una procedura guidata personalizzata che apre un Windows Form prima della creazione del progetto. Il modulo consente agli utenti di aggiungere un valore di parametro personalizzato che viene aggiunto al codice sorgente durante la creazione del progetto.

1. Configurare il progetto VSIX per consentire la creazione di un assembly.

2. In **Esplora soluzioni**selezionare il nodo progetto VSIX. Sotto **Esplora soluzioni**verrà visualizzata la finestra **Proprietà** . In caso contrario, selezionare **Visualizza** > **finestra Proprietà**o premere **F4**. Nella finestra **Proprietà** selezionare i campi seguenti per `true`:

   - **Includi assembly nel contenitore VSIX**

   - **Includere i simboli di debug nel contenitore VSIX**

   - **Includere i simboli di debug nella distribuzione VSIX locale**

3. Aggiungere l'assembly come asset al progetto VSIX. Aprire il file *source. Extension. vsixmanifest* e selezionare la scheda **Asset** . Nella finestra **Aggiungi nuovo asset** , per **tipo** selezionare **Microsoft. VisualStudio. assembly**, per **origine** selezionare **un progetto nella soluzione corrente**e per **progetto** selezionare **MyProjectWizard**.

4. Aggiungere i riferimenti seguenti al progetto VSIX. (In **Esplora soluzioni**, nel nodo progetto VSIX selezionare **riferimenti**, fare clic con il pulsante destro del mouse e scegliere **Aggiungi riferimento**. Nella scheda **Framework** della finestra di dialogo **Aggiungi riferimento** individuare l'assembly **System. Windows Forms** e selezionarlo. Trovare e selezionare anche gli assembly **System** e **System. Drawing** . A questo punto, selezionare la scheda **estensioni** . Individuare l'assembly **EnvDTE** e selezionarlo. Trovare anche l'assembly **Microsoft. VisualStudio. TemplateWizardInterface** e selezionarlo. Fare clic su **OK**.

5. Aggiungere una classe per l'implementazione della procedura guidata al progetto VSIX. (In **Esplora soluzioni**, fare clic con il pulsante destro del mouse sul nodo del progetto VSIX e scegliere **Aggiungi**, quindi **nuovo elemento**, quindi **classe**). Denominare la classe **WizardImplementation**.

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

    Il **UserInputForm** a cui si fa riferimento in questo codice verrà implementato in un secondo momento.

    La `WizardImplementation` classe contiene implementazioni del metodo per ogni membro <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>di. In questo esempio solo il <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> metodo esegue un'attività. Tutti gli altri metodi non eseguono alcuna operazione `true`o restituiscono.

    Il <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> metodo accetta quattro parametri:

   - Parametro di cui è possibile eseguire il cast all' <xref:EnvDTE._DTE> oggetto radice per consentire la personalizzazione del progetto. <xref:System.Object>

   - <xref:System.Collections.Generic.Dictionary%602> Parametro che contiene una raccolta di tutti i parametri predefiniti nel modello. Per ulteriori informazioni sui parametri di modello, vedere [parametri di modello](../ide/template-parameters.md).

   - <xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind> Parametro che contiene informazioni sul tipo di modello utilizzato.

   - <xref:System.Object> Matrice che contiene un set di parametri passati alla procedura guidata da Visual Studio.

     Questo esempio aggiunge un valore di parametro dal modulo di input dell'utente <xref:System.Collections.Generic.Dictionary%602> al parametro. Ogni istanza del `$custommessage$` parametro nel progetto verrà sostituita con il testo immesso dall'utente.

7. A questo punto, creare il **UserInputForm**. Nel file *WizardImplementation.cs* aggiungere il codice seguente dopo la fine della `WizardImplementation` classe.

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

    Il modulo di input dell'utente fornisce un modulo semplice per l'immissione di un parametro personalizzato. Il modulo contiene una casella di testo `textBox1` denominata e un pulsante `button1`denominato. Quando si fa clic sul pulsante, il testo della casella di testo viene archiviato nel `customMessage` parametro.

## <a name="connect-the-wizard-to-the-custom-template"></a>Connettere la procedura guidata al modello personalizzato

Per fare in modo che il modello di progetto personalizzato usi la procedura guidata personalizzata, è necessario firmare l'assembly della procedura guidata e aggiungere alcune righe al modello di progetto personalizzato per indicare dove trovare l'implementazione della procedura guidata quando viene creato un nuovo progetto.

1. Firmare l'assembly. Nella **Esplora soluzioni**selezionare il progetto VSIX, fare clic con il pulsante destro del mouse e scegliere **Proprietà progetto**.

2. Nella finestra delle **proprietà del progetto** selezionare la scheda **firma** . nella scheda **firma** selezionare **Firma assembly**. Nel campo **Scegli un file chiave con nome sicuro** selezionare  **\<nuovo >** . Nella finestra **Crea chiave con nome sicuro** Digitare **Key. snk**nel campo **nome file di chiave** . Deselezionare il campo **Proteggi file di chiave con una password** .

3. Nella **Esplora soluzioni**selezionare il progetto VSIX e trovare la finestra **Proprietà** .

4. Impostare il campo **Copia output di compilazione in directory di output** su **true**. Ciò consente di copiare l'assembly nella directory di output quando la soluzione viene ricompilata. È ancora incluso nel `.vsix` file. Per individuare la chiave di firma, è necessario visualizzare l'assembly.

5. Ricompilare la soluzione.

6. È ora possibile trovare il file Key. snk nella directory del progetto MyProjectWizard ( *\<percorso del disco > \MyProjectTemplate\MyProjectWizard\key.snk*). Copiare il file *Key. snk* .

7. Passare alla directory di output e trovare l'assembly ( *\<percorso del disco > \ MyProjectTemplate/MyProjectWizard \ bin \ debug \ MyProjectWizard. dll*). Incollare il file *Key. snk* qui. (Questo non è assolutamente necessario, ma renderà più semplice la procedura seguente).

8. Aprire una finestra di comando e passare alla directory in cui è stato creato l'assembly.

9. Trovare lo strumento di firma *sn. exe* . Ad esempio, in un sistema operativo Windows a 10 64 bit, un percorso tipico è il seguente:

     *C:\Programmi (x86) \Microsoft SDKs\Windows\v10.0A\bin\NETFX 4.6.1 Tools*

     Se non si riesce a trovare lo strumento, provare a eseguire **where/r. sn. exe** nella finestra di comando. Prendere nota del percorso.

10. Estrarre la chiave pubblica dal file *Key. snk* . Nella finestra di comando digitare

     **\<percorso di sn. exe > \sn.exe-p Key. snk outfile. Key.**

     Non dimenticare di racchiudere il percorso di *sn. exe* con virgolette se sono presenti spazi nei nomi di directory.

11. Ottenere il token di chiave pubblica dal file outfile:

     **\<percorso di sn. exe > \sn.exe-t outfile. Key.**

     Anche in questo caso, non dimenticare le virgolette. Nell'output dovrebbe essere visualizzata una riga simile alla seguente.

     **Il token di chiave \<pubblica è token >**

     Prendere nota di questo valore.

12. Aggiungere il riferimento alla procedura guidata personalizzata al file con *estensione vstemplate* del modello di progetto. Nella **Esplora soluzioni**individuare il file denominato *MyProjectTemplate. vstemplate*e aprirlo. Al termine della \<sezione > TemplateContent aggiungere la sezione seguente:

    ```xml
    <WizardExtension>
        <Assembly>MyProjectWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=token</Assembly>
        <FullClassName>MyProjectWizard.WizardImplementation</FullClassName>
    </WizardExtension>
    ```

     Dove **MyProjectWizard** è il nome dell'assembly e **token** è il token copiato nel passaggio precedente.

13. Salvare tutti i file nel progetto e ricompilare.

## <a name="add-the-custom-parameter-to-the-template"></a>Aggiungere il parametro personalizzato al modello

In questo esempio, il progetto utilizzato come modello Visualizza il messaggio specificato nel modulo di input dell'utente della procedura guidata personalizzata.

1. Nel **Esplora soluzioni**passare al progetto **MyProjectTemplate** e aprire *Class1.cs*.

2. `Main` Nel metodo dell'applicazione aggiungere la riga di codice seguente.

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

A questo punto è possibile creare un progetto dal modello e utilizzare la procedura guidata personalizzata.

1. Ricompilare la soluzione e avviare il debug. Verrà visualizzata una seconda istanza di Visual Studio.

2. Creare un nuovo progetto MyProjectTemplate. (**File** > nuovoprogetto > ).

3. Nella finestra di dialogo **nuovo progetto** cercare "MyProject" per individuare il modello, digitare un nome e fare clic su **OK**.

     Verrà visualizzato il modulo di input dell'utente della procedura guidata.

4. Digitare un valore per il parametro personalizzato e fare clic sul pulsante.

     Il modulo di input utente della procedura guidata viene chiuso e viene creato un progetto dal modello.

5. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul file del codice sorgente e scegliere **Visualizza codice**.

     Si noti `$custommessage$` che è stato sostituito con il testo immesso nel modulo di input dell'utente della procedura guidata.

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>
- [Personalizzare i modelli](../ide/customizing-project-and-item-templates.md)
- [Elemento WizardExtension (modelli di Visual Studio)](../extensibility/wizardextension-element-visual-studio-templates.md)
- [Pacchetti NuGet nei modelli di Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)
