---
title: 'Procedura: utilizzare procedure guidate con modelli di progetto'
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- project templates [Visual Studio], wizards
- Visual Studio templates, wizards
- wizards [Visual Studio], project templates
- templates [Visual Studio], wizards
- IWizard interface
ms.assetid: 47ee26cf-67b7-4ff1-8a9d-ab11a725405c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4d2dc057dfa518bb52c6ba4d30cd0f3e0a822cfd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710539"
---
# <a name="how-to-use-wizards-with-project-templates"></a>Procedura: utilizzare procedure guidate con modelli di progettoHow to: Use wizards with project templates

In Visual Studio è disponibile l'interfaccia <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> che, se implementata, consente di eseguire il codice personalizzato quando un utente crea un progetto da un modello.

La personalizzazione del modello di progetto può essere usata per visualizzare un'interfaccia utente personalizzata che raccoglie l'input dell'utente per personalizzare il modello, aggiungere file aggiuntivi al modello o qualsiasi altra azione consentita in un progetto.

I <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> metodi di interfaccia vengono chiamati in momenti diversi durante la creazione del progetto, a partire dal momento in cui un utente fa clic **su OK** nella finestra di dialogo **Nuovo progetto** . Ogni metodo dell'interfaccia è denominato per descrivere il punto in cui viene chiamato. Ad esempio, Visual <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> Studio chiama immediatamente quando inizia a creare il progetto, rendendolo una buona posizione per scrivere codice personalizzato per raccogliere l'input dell'utente.

## <a name="create-a-project-template-project-with-a-vsix-project"></a>Creare un progetto di modello di progetto con un progetto VSIXCreate a project template project with a VSIX project

Si inizia a creare un modello personalizzato con il progetto di modello di progetto, che fa parte di Visual Studio SDK. In this procedure, we'll use a C# project template project, but there is also a Visual Basic project template project. Quindi si aggiunge un progetto VSIX alla soluzione che contiene il progetto di modello di progetto.

1. Creare un progetto di modello di progetto c'è (in Visual Studio, selezionare **File** > **nuovo** > **progetto** e cercare "modello di progetto"). Denominarlo **MyProjectTemplate**.

   > [!NOTE]
   > Potrebbe essere richiesto di installare Visual Studio SDK. Per ulteriori informazioni, vedere [Installazione di Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

2. Aggiungere un nuovo progetto VSIX nella stessa soluzione del progetto di modello di progetto (in **Esplora soluzioni**, selezionare il nodo della soluzione, fare clic con il pulsante destro del mouse e scegliere **Aggiungi** > **nuovo progetto** e cercare "vsix"). Denominarlo **MyProjectWizard.Name it MyProjectWizard.**

3. Impostare il progetto VSIX come progetto di avvio. In **Esplora soluzioni**selezionare il nodo del progetto VSIX , fare clic con il pulsante destro del mouse e scegliere Imposta come progetto di **avvio**.

4. Aggiungere il progetto di modello come risorsa del progetto VSIX. In **Esplora soluzioni**, nel nodo del progetto VSIX, individuare il file *source.extension.vsixmanifest.* Fare doppio clic su di esso per aprirlo nell'editor del manifesto.

5. Nell'editor del manifesto, seleziona la scheda **Asset** sul lato sinistro della finestra.

6. Nella scheda **Risorse,** selezionare **Nuovo.** Nella finestra **Aggiungi nuovo asset** selezionare **Microsoft.VisualStudio.ProjectTemplate**per il campo Tipo . Nel campo **Origine** selezionare **Un progetto nella soluzione corrente.** Nel campo **Progetto** selezionare **MyProjectTemplate**. Fare quindi clic su **OK**.

7. Compilare la soluzione e avviare il debug. Verrà visualizzata una seconda istanza di Visual Studio. L'operazione potrebbe richiedere alcuni minuti.

8. Nella seconda istanza di Visual Studio, provare a creare un nuovo progetto con il nuovo modello (**File** > **nuovo** > **progetto**, cercare "myproject"). Il nuovo progetto dovrebbe essere visualizzato con una classe denominata **Class1**. È stato creato un modello di progetto personalizzato. Interrompere il debug ora.

## <a name="create-a-custom-template-wizard"></a>Creazione guidata modello personalizzato

In questa procedura viene illustrato come creare una procedura guidata personalizzata che apre un Windows Form prima della creazione del progetto. Il modulo consente agli utenti di aggiungere un valore di parametro personalizzato che viene aggiunto al codice sorgente durante la creazione del progetto.

1. Impostare il progetto VSIX per consentire la creazione di un assembly.

2. In **Esplora soluzioni**selezionare il nodo del progetto VSIX. Sotto **Esplora soluzioni**, verrà visualizzata la finestra **Proprietà** . In caso contrario, selezionare **Visualizza** > **finestra Proprietà**oppure premere **F4**. Nella finestra **Proprietà,** selezionare `true`i seguenti campi per:

   - **Includi assembly nel contenitore VSIX**

   - **Includere simboli di debug nel contenitore VSIX**

   - **Includi simboli di debug nella distribuzione VSIX locale**

3. Aggiungere l'assembly come risorsa al progetto VSIX. Aprire il file *source.extension.vsixmanifest* e selezionare la scheda **Asset.** Nella finestra **Aggiungi nuovo asset,** per **Tipo** selezionare **Microsoft.VisualStudio.Assembly**, per **Origine** selezionare **Un progetto nella soluzione corrente**e per **Progetto** selezionare **CreazioneguidataProgetto**.

4. Aggiungere i riferimenti seguenti al progetto VSIX. In **Esplora soluzioni**, nel nodo del progetto VSIX selezionare **Riferimenti**, fare clic con il pulsante destro del mouse e scegliere **Aggiungi riferimento**. Nella scheda **Framework** della finestra di dialogo **Aggiungi riferimento** individuare l'assembly **System.Windows Forms** e selezionarlo. Individuare e selezionare anche gli assiemi **System** e **System.Drawing.** Selezionare ora la scheda **Estensioni.** Individuare l'assembly **EnvDTE** e selezionarlo. Individuare anche l'assembly **Microsoft.VisualStudio.TemplateWizardInterface** e selezionarlo. Fare clic su **OK**.

5. Aggiungere una classe per l'implementazione della procedura guidata al progetto VSIX. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nodo del progetto VSIX e scegliere **Aggiungi**, quindi **Nuovo elemento**, quindi **Classe**. Denominare la classe **WizardImplementation**.

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

    **UserInputForm** a cui si fa riferimento in questo codice verrà implementato in un secondo momento.

    La `WizardImplementation` classe contiene implementazioni di <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>metodi per ogni membro di . In questo esempio, <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> solo il metodo esegue un'attività. Tutti gli altri metodi `true`non eseguono alcuna operazione o restituiscono .

    Il <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> metodo accetta quattro parametri:

   - Parametro <xref:System.Object> di cui è <xref:EnvDTE._DTE> possibile eseguire il cast all'oggetto radice, per consentire di personalizzare il progetto.

   - Parametro <xref:System.Collections.Generic.Dictionary%602> che contiene una raccolta di tutti i parametri predefiniti nel modello. Per ulteriori informazioni sui parametri di modello, vedere [Parametri modello](../ide/template-parameters.md).

   - Parametro <xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind> che contiene informazioni sul tipo di modello in uso.

   - Matrice <xref:System.Object> che contiene un set di parametri passati alla procedura guidata da Visual Studio.

     In questo esempio viene aggiunto un valore <xref:System.Collections.Generic.Dictionary%602> di parametro dal form di input dell'utente al parametro. Ogni istanza `$custommessage$` del parametro nel progetto verrà sostituita con il testo immesso dall'utente.

7. Creare ora **UserInputForm**. Nel *file WizardImplementation.cs* aggiungere il codice seguente `WizardImplementation` dopo la fine della classe.

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

    Il modulo di input dell'utente fornisce un modulo semplice per l'immissione di un parametro personalizzato. Il modulo contiene una `textBox1` casella di `button1`testo denominata e un pulsante denominato . Quando si fa clic sul pulsante, il testo `customMessage` della casella di testo viene memorizzato nel parametro.

## <a name="connect-the-wizard-to-the-custom-template"></a>Connettere la procedura guidata al modello personalizzato

Affinché il modello di progetto personalizzato utilizzi la procedura guidata personalizzata, è necessario firmare l'assembly della procedura guidata e aggiungere alcune righe al modello di progetto personalizzato per sapere dove trovare l'implementazione della procedura guidata quando viene creato un nuovo progetto.

1. Firma l'assemblea. In **Esplora soluzioni**selezionare il progetto VSIX, fare clic con il pulsante destro del mouse e scegliere **Proprietà progetto**.

2. Nella finestra **Proprietà progetto** selezionare la scheda **Firma** nella scheda **Firma,** selezionare **Firma assembly**. Nel campo **Scegliere un file** di chiave con nome sicuro selezionare ** \<Nuovo>**. Nel campo **Nome file** di chiave della finestra Crea chiave **con nome** sicuro **digitare key.snk**. Deselezionare il campo **Proteggi il file di chiave con una password.**

3. In **Esplora soluzioni**selezionare il progetto VSIX e individuare la finestra **Proprietà.In** the Solution Explorer , select the VSIX project and find the Properties window.

4. Impostare il campo **Copia output di compilazione in directory di output** su **true**. Ciò consente all'assembly di essere copiato nella directory di output quando la soluzione viene ricompilata. È ancora contenuto `.vsix` nel file. È necessario visualizzare l'assembly per scoprirne la chiave di firma.

5. Ricompilare la soluzione.

6. È ora possibile trovare il file key.snk nella directory del progetto MyProjectWizard*\<(percorso su disco> , MyProjectTemplate , MyProjectWizard , key.snk*). Copiare il file *key.snk.*

7. Passare alla directory di output e individuare l'assembly*\<(percorso del disco> , MyProjectTemplate/MyProjectWizard , bin , Debug , MyProjectWizard.dll*). Incollare il file *key.snk* qui. (Questo non è assolutamente necessario, ma renderà i seguenti passaggi più facili.)

8. Aprire una finestra di comando e passare alla directory in cui è stato creato l'assembly.

9. Individuare lo strumento di firma *sn.exe.* Ad esempio, in un sistema operativo Windows 10 a 64 bit, un percorso tipico sarebbe il seguente:

     *Strumenti di C: (x86) file di programma (x86) Microsoft SDKs*

     Se non è possibile trovare lo strumento, provare a eseguire **where /R . sn.exe** nella finestra di comando. Prendere nota del percorso.

10. Estrarre la chiave pubblica dal file *key.snk.* Nella finestra di comando, digitare

     **\<percorso di sn.exe>sn.exe -p key.snk outfile.key.**

     Non dimenticare di racchiudere il percorso di *sn.exe* tra virgolette se ci sono spazi nei nomi delle directory!

11. Ottenere il token di chiave pubblica dal file outfile:

     **\<percorso di sn.exe>sn.exe -t outfile.key.**

     Anche in questo caso, non dimenticare le virgolette. Si dovrebbe vedere una linea nell'output come questo

     **Il token \<di chiave pubblica è token>**

     Prendere nota di questo valore.

12. Aggiungere il riferimento alla procedura guidata personalizzata al file *.vstemplate* del modello di progetto. In **Esplora soluzioni**individuare il file denominato *MyProjectTemplate.vstemplate*e aprirlo. Dopo la fine \<della sezione> TemplateContent, aggiungere la sezione seguente:

    ```xml
    <WizardExtension>
        <Assembly>MyProjectWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=token</Assembly>
        <FullClassName>MyProjectWizard.WizardImplementation</FullClassName>
    </WizardExtension>
    ```

     Dove **MyProjectWizard** è il nome dell'assembly e **token** è il token copiato nel passaggio precedente.

13. Salvare tutti i file nel progetto e ricompilare.

## <a name="add-the-custom-parameter-to-the-template"></a>Aggiungere il parametro personalizzato al modello

In questo esempio, il progetto utilizzato come modello visualizza il messaggio specificato nel modulo di input dell'utente della procedura guidata personalizzata.

1. In **Esplora soluzioni**passare al progetto **MyProjectTemplate** e *aprire Class1.cs*.

2. Nel `Main` metodo dell'applicazione aggiungere la riga di codice seguente.

   ```csharp
   Console.WriteLine("$custommessage$");
   ```

    Il `$custommessage$` parametro viene sostituito con il testo immesso nel modulo di input dell'utente quando viene creato un progetto dal modello.

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

## <a name="use-the-custom-wizard"></a>Utilizzare la procedura guidata personalizzata

A questo punto è possibile creare un progetto dal modello e utilizzare la procedura guidata personalizzata.

1. Ricompilare la soluzione e avviare il debug. Verrà visualizzata una seconda istanza di Visual Studio.

2. Creare un nuovo progetto MyProjectTemplate.Create a new MyProjectTemplate project. (**File** > **nuovo** > **progetto**).

3. Nella finestra di dialogo **Nuovo progetto** cercare "myproject" per individuare il modello, digitare un nome e fare clic su **OK**.

     Verrà aperto il modulo di input dell'utente della procedura guidata.

4. Digitare un valore per il parametro personalizzato e fare clic sul pulsante.

     Il modulo di input dell'utente della procedura guidata viene chiuso e viene creato un progetto dal modello.

5. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul file del codice sorgente e **scegliere Visualizza codice**.

     Si `$custommessage$` noti che è stato sostituito con il testo immesso nel modulo di input dell'utente della procedura guidata.

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>
- [Personalizzare i modelli](../ide/customizing-project-and-item-templates.md)
- [Elemento WizardExtension (modelli di Visual Studio)](../extensibility/wizardextension-element-visual-studio-templates.md)
- [Pacchetti NuGet nei modelli di Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)
