---
title: Creare un plug-in di registrazione per i test delle prestazioni Web
description: Informazioni su come WebTestRecorderPlugin consente di modificare un test delle prestazioni Web registrato dopo aver scelto Arresta nella barra degli strumenti di Registrazione test prestazioni Web.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, recorder plug-in
ms.assetid: 6fe13be1-aeb5-4927-9bff-35950e194da9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 55a12f6ea6fb342adf3aacc8967f8fc62020696a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122148584"
---
# <a name="how-to-create-a-recorder-plug-in"></a>Procedura: Creare un plug-in di registrazione

Il plug-in <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin> consente di modificare un test delle prestazioni Web registrato. La modifica si  verifica dopo aver scelto Arresta nella barra degli strumenti di Registrazione test prestazioni **Web,** ma prima che il test venga salvato e presentato nel Editor test prestazioni Web.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Un plug-in di registrazione consente di eseguire una correlazione personalizzata nei parametri dinamici. Con la funzionalità di correlazione incorporata, i test delle prestazioni Web rilevano i parametri dinamici nella registrazione Web al completamento o quando si usa Alza di livello parametri dinamici a parametri **di test Web** sulla barra degli strumenti di **Editor test prestazioni Web.** La funzionalità di rilevamento incorporata non è tuttavia sempre in grado di trovare tutti i parametri dinamici. Non troverebbe ad esempio un ID sessione, il cui valore viene in genere modificato ogni 5 - 30 minuti. Il processo di correlazione andrà pertanto eseguito manualmente.

Il plug-in <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin> consente di scrivere il codice per realizzare un plug-in personalizzato, che potrà eseguire la correlazione o modificare il test delle prestazioni Web in vari modi prima del salvataggio e della presentazione nell'Editor test prestazioni Web. Se pertanto si determina che una variabile dinamica specifica deve essere correlata per molte registrazioni, il processo potrà essere automatizzato.

Alcuni altri scopi per i quali è possibile usare un plug-in di registrazione sono l'aggiunta di regole di estrazione e convalida, l'aggiunta di parametri di contesto o la conversione di commenti in transazioni in un test delle prestazioni Web.

Nelle procedure seguenti viene illustrata la creazione di codice rudimentale per la realizzazione, la distribuzione e l'esecuzione di un plug-in di registrazione. Nel codice di esempio che segue le procedure viene dimostrato l'utilizzo di Visual C# per creare un plug-in di registrazione personalizzato per la correlazione di parametri dinamici.

## <a name="create-a-recorder-plug-in"></a>Creare un plug-in di registrazione

### <a name="to-create-a-recorder-plug-in"></a>Per creare un plug-in di registrazione

1. Aprire una soluzione che contenga il progetto di test di carico e prestazioni Web con il test delle prestazioni Web per il quale si vuole creare un plug-in di registrazione.

2. Aggiungere alla soluzione un nuovo progetto **Libreria di classi**.

3. Nella **Esplora soluzioni** progetto libreria di classi fare clic con il pulsante destro del mouse sulla cartella **Riferimenti** e scegliere **Aggiungi riferimento.**

    > [!TIP]
    > Un esempio di una nuova cartella di progetto libreria di classi è **RecorderPlugins**.

     Viene visualizzata la finestra di dialogo **Aggiungi riferimento**.

4. Fare clic sulla scheda **.NET**.

5. Scorrere verso il basso e selezionare **Microsoft.VisualStudio.QualityTools.WebTestFramework**, quindi scegliere **OK**.

     **Microsoft.VisualStudio.QualityTools.WebTestFramework** viene aggiunto nella **cartella Riferimenti** in **Esplora soluzioni**.

6. Scrivere il codice per il plug-in di registrazione. Creare innanzitutto una nuova classe pubblica derivata dalla classe <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin>.

7. Eseguire l'override del metodo <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin.PostWebTestRecording*>.

    ```csharp
    public class Class1 : WebTestRecorderPlugin
        {
            public override void PostWebTestRecording(object sender, PostWebTestRecordingEventArgs e)
            {
                base.PostWebTestRecording(sender, e);
            }
        }
    ```

     Gli argomenti dell'evento forniranno due oggetti da usare: il risultato registrato e il test delle prestazioni Web registrato. Questo consentirà di scorrere il risultato in cerca valori determinati e passare quindi alla stessa richiesta nel test delle prestazioni Web per apportare le modifiche. È anche possibile modificare solo il test delle prestazioni Web per aggiungere un parametro di contesto o per applicare parametri a delle parti dell'URL.

    > [!NOTE]
    > Se si modifica il test delle prestazioni Web, sarà anche necessario impostare la proprietà <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestRecordingEventArgs.RecordedWebTestModified*> su true: `e.RecordedWebTestModified = true;`

8. Aggiungere codice in base a ciò che si vuole che il plug-in di registrazione esegua dopo la registrazione Web. È ad esempio possibile aggiungere codice per gestire la correlazione personalizzata, come mostrato nell'esempio sotto. È anche possibile creare un plug-in di registrazione, ad esempio, per la conversione di commenti in transazioni o per l'aggiunta di regole di convalida al test delle prestazioni Web.

9. Scegliere **Compila** dal menu **Compila. \<class library project name>**

A questo punto, distribuire il plug-in di registrazione per effettuarne la registrazione in Visual Studio.

### <a name="deploy-the-recorder-plug-in"></a>Distribuire il plug-in di registrazione

Dopo avere compilato il plug-in di registrazione, posizionare il file DLL risultante in uno dei due percorsi seguenti:

- *%ProgramFiles(x86)%\Microsoft Visual Studio\\[versione]\\[edizione]\Common7\IDE\PrivateAssemblies\WebTestPlugins*

- *%USERPROFILE%\Documents\Visual Studio [versione]\WebTestPlugins*

> [!WARNING]
> Dopo avere copiato il plug-in di registrazione in uno dei due percorsi, è necessario riavviare Visual Studio per completare la registrazione del plug-in.

### <a name="execute-the-recorder-plug-in"></a>Eseguire il plug-in di registrazione

1. Creare un nuovo test delle prestazioni Web.

     Viene visualizzata la finestra di dialogo **Attiva WebTestRecordPlugins**.

2. Selezionare la casella di controllo per il plug-in di registrazione, quindi scegliere **OK**.

     Una volta che il test delle prestazioni Web ha completato la registrazione, verrà eseguito il nuovo plug-in di registrazione.

    > [!WARNING]
    > Quando si esegue un test delle prestazioni Web o un test di carico in cui viene usato il plug-in, è possibile che venga visualizzato un errore simile a quello seguente:
    >
    > **Richiesta non riuscita: Eccezione nel caso in cui non sia stato possibile caricare il file o \<plug-in> l'assembly \<"Plug-in name".dll file> ', Version= \<n.n.n.n> , Culture=neutral, PublicKeyToken=null' o una delle relative dipendenze. Impossibile trovare il file specificato.**
    >
    > L'errore si verifica se si effettuano modifiche al codice di uno qualsiasi dei plug-in e si crea una nuova versione del file DLL **(Version=0.0.0.0)**, ma il plug-in fa ancora riferimento alla versione originale. Per risolvere il problema, attenersi ai passaggi riportati di seguito:
    >
    > 1. Nei riferimenti del progetto di test di carico e prestazioni web sarà presente un avviso. Rimuovere e aggiungere nuovamente il riferimento alla DLL del plug-in.
    > 2. Rimuovere il plug-in dal test o dal percorso appropriato, quindi aggiungerlo di nuovo.

## <a name="example"></a>Esempio

In questo esempio viene illustrato come creare un plug-in di registrazione del test delle prestazioni Web personalizzato per eseguire la correlazione dei parametri dinamici personalizzata.

> [!NOTE]
> Un listato completo del codice di esempio è riportato alla fine di questo argomento.

### <a name="iterate-through-the-result-to-find-first-page-with-reportsession"></a>Scorrere il risultato per trovare la prima pagina con ReportSession

In questa parte dell'esempio di codice si scorre ogni oggetto registrato e si cerca ReportSession nel corpo della risposta.

```csharp
foreach (WebTestResultUnit unit in e.RecordedWebTestResult.Children)
 {
     WebTestResultPage page = unit as WebTestResultPage;
     if (page != null)
     {
         if (!foundId)
         {
             int indexOfReportSession = page.RequestResult.Response.BodyString.IndexOf("ReportSession");
             if (indexOfReportSession > -1)
             {
```

### <a name="add-an-extraction-rule"></a>Aggiungere una regola di estrazione

Una volta che la risposta è stata trovata, è necessario aggiungere una regola di estrazione. In questa parte dell'esempio di codice viene creata la regola di estrazione usando la classe <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRuleReference>, quindi, nel test delle prestazioni Web, viene trovata la corretta richiesta cui aggiungere la regola di estrazione. Ciascun oggetto risultato dispone di una nuova proprietà aggiunta denominata DeclarativeWebTestItemId, che è quella usata nel codice per ottenere la corretta richiesta dal test delle prestazioni Web.

```csharp
ExtractionRuleReference ruleReference = new ExtractionRuleReference();
     ruleReference.Type = typeof(ExtractText);
     ruleReference.ContextParameterName = "SessionId";
     ruleReference.Properties.Add(new PluginOrRuleProperty("EndsWith", "&ControlID="));
     ruleReference.Properties.Add(new PluginOrRuleProperty("HtmlDecode", "True"));
     ruleReference.Properties.Add(new PluginOrRuleProperty("IgnoreCase", "True"));
     ruleReference.Properties.Add(new PluginOrRuleProperty("Index", "0"));
     ruleReference.Properties.Add(new PluginOrRuleProperty("Required", "True"));
     ruleReference.Properties.Add(new PluginOrRuleProperty("StartsWith", "ReportSession="));
     ruleReference.Properties.Add(new PluginOrRuleProperty("UseRegularExpression", "False"));

     WebTestRequest requestInWebTest = e.RecordedWebTest.GetItem(page.DeclarativeWebTestItemId) as WebTestRequest;
     if (requestInWebTest != null)
     {
         requestInWebTest.ExtractionRuleReferences.Add(ruleReference);
         e.RecordedWebTestModified = true;
     }
```

### <a name="replace-query-string-parameters"></a>Sostituire i parametri della stringa di query

Vengono ora trovati tutti i parametri della stringa di query che presentano il nome ReportSession e il relativo valore viene cambiato in {{SessionId}} come mostrato in questa parte dell'esempio di codice:

```csharp
WebTestRequest requestInWebTest = e.RecordedWebTest.GetItem(page.DeclarativeWebTestItemId) as WebTestRequest;
if (requestInWebTest != null)
{
    foreach (QueryStringParameter param in requestInWebTest.QueryStringParameters)
    {
         if (param.Name.Equals("ReportSession"))
         {
             param.Value = "{{SessionId}}";
         }
     }
 }
```

```csharp
using System.ComponentModel;
using Microsoft.VisualStudio.TestTools.WebTesting;
using Microsoft.VisualStudio.TestTools.WebTesting.Rules;

namespace RecorderPlugin
{
    [DisplayName("Correlate ReportSession")]
    [Description("Adds extraction rule for Report Session and binds this to querystring parameters that use ReportSession")]
    public class CorrelateSessionId : WebTestRecorderPlugin
    {
        public override void PostWebTestRecording(object sender, PostWebTestRecordingEventArgs e)
        {
            //first find the session id
            bool foundId = false;
            foreach (WebTestResultUnit unit in e.RecordedWebTestResult.Children)
            {
                WebTestResultPage page = unit as WebTestResultPage;
                if (page != null)
                {
                    if (!foundId)
                    {
                        int indexOfReportSession = page.RequestResult.Response.BodyString.IndexOf("ReportSession");
                        if (indexOfReportSession > -1)
                        {
                            //add an extraction rule to this request
                            // Get the corresponding request in the Declarative Web performance test
                            ExtractionRuleReference ruleReference = new ExtractionRuleReference();

                            ruleReference.Type = typeof(ExtractText);
                            ruleReference.ContextParameterName = "SessionId";
                            ruleReference.Properties.Add(new PluginOrRuleProperty("EndsWith", "&ControlID="));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("HtmlDecode", "True"));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("IgnoreCase", "True"));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("Index", "0"));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("Required", "True"));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("StartsWith", "ReportSession="));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("UseRegularExpression", "False"));

                            WebTestRequest requestInWebTest = e.RecordedWebTest.GetItem(page.DeclarativeWebTestItemId) as WebTestRequest;
                            if (requestInWebTest != null)
                            {
                                requestInWebTest.ExtractionRuleReferences.Add(ruleReference);
                                e.RecordedWebTestModified = true;
                            }
                            foundId = true;

                        }
                    }
                    else
                    {
                        //now update query string parameters
                        WebTestRequest requestInWebTest = e.RecordedWebTest.GetItem(page.DeclarativeWebTestItemId) as WebTestRequest;
                        if (requestInWebTest != null)
                        {
                            foreach (QueryStringParameter param in requestInWebTest.QueryStringParameters)
                            {
                                if (param.Name.Equals("ReportSession"))
                                {
                                    param.Value = "{{SessionId}}";
                                }
                            }
                        }
                    }
                }
            }
        }
    }
}
```

## <a name="see-also"></a>Vedi anche

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin.PostWebTestRecording*>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRuleReference>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin.PostWebTestRecording*>
- [Creare codice personalizzato e plug-in per test di carico](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Generare ed eseguire un test delle prestazioni Web codificato](../test/generate-and-run-a-coded-web-performance-test.md)
