---
title: Creare un plug-in test di carico
description: Informazioni su come creare un plug-in del test di carico per eseguire codice in momenti diversi durante l'esecuzione del test di carico, che può espandere o modificare la funzionalità del test di carico.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
f1_keywords:
- vs.test.load.loadtestplugin
helpviewer_keywords:
- code, load tests
- plug-ins, load test
- load tests, plug-ins
ms.assetid: 27806972-1b15-4388-833d-6d0632816f1f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 9bb687a250b35a9805dd62eb8008440523d3dd2957d889f0d1a303b07eba8c4a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121384893"
---
# <a name="how-to-create-a-load-test-plug-in"></a>Procedura: Creare un plug-in test di carico

È possibile creare un plug-in test di carico per eseguire il codice in momenti diversi durante l'esecuzione del test di carico. Si crea un plug-in per espandere o modificare le funzioni incorporate del test di carico. È ad esempio possibile scrivere codice per un plug-in test di carico per impostare o modificare il modello del test di carico durante l'esecuzione del test di carico. A tale scopo, è necessario creare una classe che erediti l'interfaccia <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>. Tale classe deve implementare il metodo <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin.Initialize*> dell'interfaccia. Per altre informazioni, vedere <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>.

> [!TIP]
> È anche possibile creare plug-in per i test web. Per altre informazioni, [vedere Procedura: Creare un plug-in test prestazioni Web.](../test/how-to-create-a-web-performance-test-plug-in.md)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

<!-- markdownlint-disable MD003 MD020 -->
## <a name="to-create-a-load-test-plug-in-in-c"></a>Per creare un plug-in test di carico in C#
<!-- markdownlint-enable MD003 MD020 -->

1. Aprire un progetto di test di carico e prestazioni web che contenga un test delle prestazioni web.

2. Aggiungere un test di carico al progetto di test e configurarlo per eseguire un test Web.

     Per altre informazioni, vedere [Avvio rapido: Creare un progetto di test di carico](../test/quickstart-create-a-load-test-project.md).

3. Aggiungere alla soluzione un nuovo progetto **Libreria di classi**. In **Esplora soluzioni** fare clic con il pulsante destro  del mouse sulla soluzione e scegliere **Aggiungi** e quindi Project.

4. In **Esplora soluzioni** fare clic con il pulsante destro del mouse **sulla cartella Riferimenti** nella nuova libreria di classi e scegliere Aggiungi **riferimento.**

   Viene visualizzata la finestra di dialogo **Aggiungi riferimento**.

5. Scegliere la scheda **.NET**, scorrere verso il basso, quindi selezionare **Microsoft.VisualStudio.QualityTools.LoadTestFramework**.

6. Scegliere **OK**.

   Il riferimento a **Microsoft.VisualStudio.QualityTools.LoadTestFramework** viene aggiunto alla cartella **Reference** in **Esplora soluzioni**.

7. In Esplora soluzioni fare clic con il pulsante destro del mouse sul nodo principale del progetto di test di carico e prestazioni Web contenente **il** test di carico a cui si vuole aggiungere il plug-in test di carico e scegliere **Aggiungi riferimento.**

   Verrà **visualizzata la finestra di dialogo Aggiungi riferimento**.

8. Scegliere la scheda **Progetti** e selezionare il progetto di libreria di classi.

9. Scegliere **OK**.

10. Nell'**Editor di codice** aggiungere un'istruzione `using` per lo spazio dei nomi <xref:Microsoft.VisualStudio.TestTools.LoadTesting>.

11. Implementare l'interfaccia <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> per la classe creata nel progetto Libreria di classi. Per un'implementazione di esempio, vedere la sezione seguente relativa all'esempio.

12. Una volta scritto il codice, compilare il nuovo progetto.

13. Fare clic con il pulsante destro del mouse sul nodo principale del test di carico e scegliere **Aggiungi plug-in test di carico**.

     Viene visualizzata la finestra di dialogo **Aggiungi plug-in test di carico**.

14. In **Seleziona un plug-in** selezionare la classe del plug-in del test di carico.

15. Nel riquadro **Proprietà per il plug-in selezionato** impostare i valori iniziali per il plug-in da usare in fase di esecuzione.

    > [!NOTE]
    > È possibile esporre il numero di proprietà desiderato dai plug-in; è sufficiente renderle pubbliche, impostabili e di un tipo di base quale Integer, Boolean o String. È anche possibile modificare le proprietà del plug-in test prestazioni Web in un secondo momento usando la **finestra** Proprietà.

16. Scegliere **OK**.

     Il plug-in viene aggiunto alla cartella **Plug-in test di carico**.

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

Nel codice seguente viene illustrato un plug-in test di carico in cui viene eseguito il codice personalizzato dopo un evento LoadTestFinished. Se questo codice viene eseguito in un agente di test in un computer remoto e l'agente di test non dispone di un servizio SMTP localhost, lo stato del test di carico rimarrà indicato come "In corso" dal momento che verrà visualizzata una casella di messaggio.

> [!NOTE]
> Per il codice seguente è necessaria l'aggiunta di un riferimento a System.Windows.Forms.

```csharp
using System;
using Microsoft.VisualStudio.TestTools.LoadTesting;
using System.Net.Mail;
using System.Windows.Forms;

namespace LoadTestPluginTest
{
    public class MyLoadTestPlugin : ILoadTestPlugin
    {
        LoadTest myLoadTest;

        public void Initialize(LoadTest loadTest)
        {
            myLoadTest = loadTest;
            myLoadTest.LoadTestFinished += new
                EventHandler(myLoadTest_LoadTestFinished);
        }

        void myLoadTest_LoadTestFinished(object sender, EventArgs e)
        {
            try
            {
                // place custom code here
                MailAddress MyAddress = new MailAddress("someone@example.com");
                MailMessage MyMail = new MailMessage(MyAddress, MyAddress);
                MyMail.Subject = "Load Test Finished -- Admin Email";
                MyMail.Body = myLoadTest..Name + " has finished.";

                SmtpClient MySmtpClient = new SmtpClient("localhost");
                MySmtpClient.Send(MyMail);
            }

            catch (SmtpException ex)
            {
                MessageBox.Show(ex.InnerException.Message +
                    ".\r\nMake sure you have a valid SMTP.", "LoadTestPlugin", MessageBoxButtons.OK, MessageBoxIcon.Warning, MessageBoxDefaultButton.Button1);
            }
        }
    }
}
```

A un test di carico sono associati otto eventi che possono essere gestiti nel plug-in test di carico per eseguire il codice personalizzato con il test di carico. Di seguito è riportato un elenco degli eventi che consentono di accedere a stadi diversi dell'esecuzione del test di carico:

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestStarting>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestFinished>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestWarmupComplete>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.TestStarting>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.TestFinished>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.ThresholdExceeded>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.Heartbeat>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestAborted>

## <a name="see-also"></a>Vedi anche

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>
- [Creare codice personalizzato e plug-in per test di carico](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Procedura: Creare un plug-in test prestazioni Web](../test/how-to-create-a-web-performance-test-plug-in.md)
