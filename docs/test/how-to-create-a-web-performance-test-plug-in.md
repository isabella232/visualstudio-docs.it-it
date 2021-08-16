---
title: Creare un plug-in di test delle prestazioni Web
description: Informazioni su come i plug-in dei test delle prestazioni Web consentono di riutilizzare il codice all'esterno delle istruzioni dichiarative principali nel test delle prestazioni Web.
ms.custom: SEO-VS-2020
ms.date: 10/03/2016
ms.topic: how-to
f1_keywords:
- vs.test.web.webtestplugin
helpviewer_keywords:
- Web performance tests, creating plug-ins
- plug-ins, creating in Web performance tests
ms.assetid: a612f2d2-9806-477d-a126-12842f07da6e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: b3134ab644ec378c5c2869c5eb35a40c119e48dabb210a0dbf552c04d51eb8ba
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121395203"
---
# <a name="how-to-create-a-web-performance-test-plug-in"></a>Procedura: Creare un plug-in di test prestazioni Web

I plug-in test delle prestazioni web consentono di isolare e riutilizzare codice al di fuori delle istruzioni dichiarative principali nel test delle prestazioni web. Un plug-in test delle prestazioni web personalizzato consente di chiamare parte del codice durante l'esecuzione del test delle prestazioni web. Il plug-in test delle prestazioni web viene eseguito una sola volta per ogni iterazione di test. Inoltre, se si esegue l'override del metodo PreRequest o PostRequest nel plug-in test, i plug-in di tali richieste verranno eseguiti rispettivamente prima e dopo ciascuna richiesta.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

È possibile creare un plug-in test delle prestazioni web personalizzato derivando la classe personalizzata dalla classe di base <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>.

I plug-in per test delle prestazioni web personalizzati possono essere utilizzati con i test delle prestazioni web registrati, scrivendo una quantità minima di codice che consente di ottenere un elevato livello di controllo sui test. È tuttavia possibile utilizzarli anche con i test delle prestazioni web codificati. Per altre informazioni, vedere [Generare ed eseguire un test delle prestazioni Web codificato](../test/generate-and-run-a-coded-web-performance-test.md).

> [!NOTE]
> È anche possibile creare plug-in di test di carico. Vedere [Procedura: Creare un plug-in test di carico.](../test/how-to-create-a-load-test-plug-in.md)

## <a name="to-create-a-custom-web-performance-test-plug-in"></a>Per creare un plug-in di test prestazioni Web personalizzato

1. Aprire un progetto di test di carico e prestazioni web che contenga un test delle prestazioni web.

2. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sulla soluzione, scegliere **Aggiungi** e quindi nuovo **Project**.

3. Creare un nuovo progetto **Libreria di classi**.

   Il nuovo progetto di libreria di classi viene aggiunto a **Esplora soluzioni** e la nuova classe viene visualizzata nell'**Editor di codice**.

4. In **Esplora soluzioni** fare clic con il pulsante destro del mouse **sulla cartella Riferimenti** nella nuova libreria di classi e scegliere Aggiungi **riferimento.**

   Viene visualizzata la finestra di dialogo **Aggiungi riferimento**.

5. Scegliere la scheda **.NET**, scorrere verso il basso e selezionare **Microsoft.VisualStudio.QualityTools.WebTestFramework**

6. Scegliere **OK**.

     Il riferimento a **Microsoft.VisualStudio.QualityTools.WebTestFramework** viene aggiunto alla cartella **Reference** in **Esplora soluzioni**.

7. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo superiore del progetto di test di carico e prestazioni Web che contiene il test di carico a cui si vuole aggiungere il plug-in test prestazioni Web e selezionare **Aggiungi** riferimento.

8. Verrà **visualizzata la finestra di dialogo Aggiungi riferimento**.

9. Scegliere la **scheda Progetti** e selezionare la libreria di **classi Project**.

10. Scegliere **OK**.

11. Nell'**editor di codice** scrivere il codice del plug-in. Creare innanzitutto una nuova classe pubblica derivata dalla classe <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>.

12. Implementare il codice in uno o più gestori eventi. Per un'implementazione di esempio, vedere la sezione seguente relativa all'esempio.

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestRecordingEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PreRequestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostRequestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PrePageEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostPageEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PreTransactionEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostTransactionEventArgs>

13. Una volta scritto il codice, compilare il nuovo progetto.

14. Aprire un test delle prestazioni web.

15. Per aggiungere il plug-in test prestazioni Web, scegliere **Aggiungi plug-in test Web** sulla barra degli strumenti.

     Viene visualizzata la finestra di dialogo **Aggiungi plug-in test Web**.

16. In **Selezionare un plug-in** selezionare la classe plug-in del test delle prestazioni Web.

17. Nel riquadro **Proprietà per il plug-in selezionato** impostare i valori iniziali per il plug-in da usare in fase di esecuzione.

    > [!NOTE]
    > È possibile esporre il numero di proprietà desiderato dai plug-in; è sufficiente renderle pubbliche, impostabili e di un tipo di base quale Integer, Boolean o String. È anche possibile modificare le proprietà del plug-in di test delle prestazioni web in un secondo momento utilizzando la finestra Proprietà.

18. Scegliere **OK**.

     Il plug-in viene aggiunto alla cartella **Plug-in test Web**.

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

Il codice seguente consente di creare un plug-in test delle prestazioni web personalizzato per l'aggiunta di un elemento a <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestContext> che rappresenta l'iterazione test.

Dopo aver eseguito il test delle prestazioni **Web,** usando questo plug-in è possibile visualizzare  l'elemento aggiunto denominato **TestIteratanionNumber** nella scheda Contesto del Visualizzatore risultati prestazioni Web .

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

## <a name="see-also"></a>Vedi anche

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>
- [Creare codice personalizzato e plug-in per test di carico](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Procedura: Creare un plug-in a livello di richiesta](../test/how-to-create-a-request-level-plug-in.md)
- [Codificare una regola di estrazione personalizzata per un test delle prestazioni Web](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Codificare una regola di convalida personalizzata per un test delle prestazioni Web](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Procedura: Creare un plug-in test di carico](../test/how-to-create-a-load-test-plug-in.md)
- [Generare ed eseguire un test delle prestazioni Web codificato](../test/generate-and-run-a-coded-web-performance-test.md)
