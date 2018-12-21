---
title: Creare un plug-in di test delle prestazioni Web
ms.date: 10/03/2016
ms.topic: conceptual
f1_keywords:
- vs.test.web.webtestplugin
helpviewer_keywords:
- Web performance tests, creating plug-ins
- plug-ins, creating in Web performance tests
ms.assetid: a612f2d2-9806-477d-a126-12842f07da6e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: f4848fbaed6df9817cd9f0ddf16f388d855f5cd9
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/07/2018
ms.locfileid: "53067654"
---
# <a name="how-to-create-a-web-performance-test-plug-in"></a>Procedura: Creare un plug-in di test delle prestazioni Web

I plug-in test delle prestazioni web consentono di isolare e riutilizzare codice al di fuori delle istruzioni dichiarative principali nel test delle prestazioni web. Un plug-in test delle prestazioni web personalizzato consente di chiamare parte del codice durante l'esecuzione del test delle prestazioni web. Il plug-in test delle prestazioni web viene eseguito una sola volta per ogni iterazione di test. Inoltre, se si esegue l'override del metodo PreRequest o PostRequest nel plug-in test, i plug-in di tali richieste verranno eseguiti rispettivamente prima e dopo ciascuna richiesta.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

È possibile creare un plug-in test delle prestazioni web personalizzato derivando la classe personalizzata dalla classe di base <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>.

I plug-in per test delle prestazioni web personalizzati possono essere utilizzati con i test delle prestazioni web registrati, scrivendo una quantità minima di codice che consente di ottenere un elevato livello di controllo sui test. È tuttavia possibile utilizzarli anche con i test delle prestazioni web codificati. Per altre informazioni, vedere [Generare ed eseguire un test delle prestazioni Web codificato](../test/generate-and-run-a-coded-web-performance-test.md).

> [!NOTE]
> È possibile creare anche plug-in test di carico. Vedere [Procedura: Creare un plug-in test di carico](../test/how-to-create-a-load-test-plug-in.md).

## <a name="to-create-a-custom-web-performance-test-plug-in"></a>Per creare un plug-in di test prestazioni Web personalizzato

1.  Aprire un progetto di test di carico e prestazioni web che contenga un test delle prestazioni web.

2.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse sulla soluzione, selezionare **Aggiungi**, quindi scegliere **Nuovo progetto**.

     Viene visualizzata la finestra di dialogo **Aggiungi nuovo progetto**.

3.  In **Modelli installati** selezionare **Visual C#**.

4.  Nell'elenco dei modelli selezionare **Libreria di classi**.

5.  Nella casella di testo **Nome** digitare un nome per la classe.

6.  Scegliere **OK**.

7.  Il nuovo progetto di libreria di classi viene aggiunto a **Esplora soluzioni** e la nuova classe viene visualizzata nell'**Editor di codice**.

8.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse sulla cartella **Riferimenti** nella nuova libreria di classi e selezionare **Aggiungi riferimento**.

9. Viene visualizzata la finestra di dialogo **Aggiungi riferimento**.

10. Scegliere la scheda **.NET**, scorrere verso il basso e selezionare **Microsoft.VisualStudio.QualityTools.WebTestFramework**

11. Scegliere **OK**.

     Il riferimento a **Microsoft.VisualStudio.QualityTools.WebTestFramework** viene aggiunto alla cartella **Riferimenti** in **Esplora soluzioni**.

12. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo principale del progetto di test di carico e prestazioni Web in cui è contenuto il test di carico al quale si vuole aggiungere il plug-in di test delle prestazioni Web e selezionare **Aggiungi riferimento**.

13. Viene visualizzata la finestra di dialogo **Aggiungi riferimento**.

14. Scegliere la scheda **Progetti** e selezionare il **progetto di libreria di classi**.

15. Scegliere **OK**.

16. Nell'**editor di codice** scrivere il codice del plug-in. Creare innanzitutto una nuova classe pubblica derivata dalla classe <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>.

17. Implementare il codice in uno o più gestori eventi. Per un'implementazione di esempio, vedere la sezione seguente relativa all'esempio.

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestRecordingEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PreRequestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostRequestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PrePageEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostPageEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PreTransactionEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostTransactionEventArgs>

18. Una volta scritto il codice, compilare il nuovo progetto.

19. Aprire un test delle prestazioni web.

20. Per aggiungere il plug-in del test delle prestazioni web, scegliere **Aggiungi plug-in test Web** nella barra degli strumenti.

     Viene visualizzata la finestra di dialogo **Aggiungi plug-in test Web**.

21. In **Seleziona un plug-in** selezionare la classe del plug-in del test delle prestazioni web.

22. Nel riquadro **Proprietà per il plug-in selezionato** impostare i valori iniziali per il plug-in da usare in fase di esecuzione.

    > [!NOTE]
    > È possibile esporre il numero di proprietà desiderato dai plug-in; è sufficiente renderle pubbliche, impostabili e di un tipo di base quale Integer, Boolean o String. È anche possibile modificare le proprietà del plug-in di test delle prestazioni web in un secondo momento utilizzando la finestra Proprietà.

23. Scegliere **OK**.

     Il plug-in viene aggiunto alla cartella **Plug-in test Web**.

    > [!WARNING]
    > Quando si esegue un test delle prestazioni web o un test di carico in cui viene utilizzato il plug-in, è possibile che venga visualizzato un errore simile a quello seguente:
    >
    > **Richiesta non riuscita: Eccezione nell'evento \<plug-in>: Non è stato possibile caricare il file o l'assembly '\<"file .dll Nome plug-in" Version=\<n.n.n.n>, Culture=neutral, PublicKeyToken=null' o una delle relative dipendenze. Il sistema non riesce a trovare il file specificato.**
    >
    > L'errore si verifica se si effettuano modifiche al codice di uno qualsiasi dei plug-in e si crea una nuova versione del file DLL **(Version=0.0.0.0)**, ma il plug-in fa ancora riferimento alla versione originale. Per risolvere il problema, attenersi ai passaggi riportati di seguito:
    >
    > 1.  Nei riferimenti del progetto di test di carico e prestazioni web sarà presente un avviso. Rimuovere e aggiungere nuovamente il riferimento alla DLL del plug-in.
    > 2.  Rimuovere il plug-in dal test o dal percorso appropriato, quindi aggiungerlo di nuovo.

## <a name="example"></a>Esempio

Il codice seguente consente di creare un plug-in test delle prestazioni web personalizzato per l'aggiunta di un elemento a <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestContext> che rappresenta l'iterazione test.

Dopo aver eseguito il test delle prestazioni web, tramite questo plug-in è possibile visualizzare l'elemento aggiunto denominato **TestIteratnionNumber** nella scheda **Contesto** del **Visualizzatore risultati test prestazioni Web**.

```csharp
using System;
using System.Collections.Generic;
using System.Text;
using System.ComponentModel;
using Microsoft.VisualStudio.TestTools.WebTesting;

namespace SampleRules
{
    [Description("This plugin can be used to set the ParseDependentsRequests property for each request")]
    public class SampleWebTestPlugin : WebTestPlugin
    {
        private bool m_parseDependents = true;

        public override void PreWebTest(object sender, PreWebTestEventArgs e)
        {
            // TODO: Add code to execute before the test.
        }

        public override void PostWebTest(object sender, PostWebTestEventArgs e)
        {
            // TODO: Add code to execute after the test.
        }

        public override void PreRequest(object sender, PreRequestEventArgs e)
        {
            // Code to execute before each request.
            // Set the ParseDependentsRequests value on the request
            e.Request.ParseDependentRequests = m_parseDependents;
        }

        // Properties for the plugin.
        [DefaultValue(true)]
        [Description("All requests will have their ParseDependentsRequests property set to this value")]
        public bool ParseDependents
        {
            get
            {
                return m_parseDependents;
            }
            set
            {
                m_parseDependents = value;
            }
        }
    }
}
```

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>
- [Creare codice personalizzato e plug-in per test di carico](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Procedura: Creare un plug-in a livello di richiesta](../test/how-to-create-a-request-level-plug-in.md)
- [Codificare una regola di estrazione personalizzata per un test delle prestazioni Web](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Codificare una regola di convalida personalizzata per un test delle prestazioni Web](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Procedura: Creare un plug-in test di carico](../test/how-to-create-a-load-test-plug-in.md)
- [Generare ed eseguire un test delle prestazioni Web codificato](../test/generate-and-run-a-coded-web-performance-test.md)