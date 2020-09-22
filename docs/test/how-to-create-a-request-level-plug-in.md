---
title: Creazione di un plug-in a livello di richiesta (test delle prestazioni Web)
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- request-level plug-in, creating
- Web performance tests, requests
ms.assetid: d0b5b23c-7e94-4637-be6c-2620a5442d46
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5f136214b787820396fdbcff37f9f3b78574e9c8
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810272"
---
# <a name="how-to-create-a-request-level-plug-in"></a>Procedura: Creare un plug-in a livello di richiesta

Le *richieste* sono istruzioni dichiarative che costituiscono test delle prestazioni Web. I plug-in test delle prestazioni web consentono di isolare e riutilizzare codice al di fuori delle istruzioni dichiarative principali nel test delle prestazioni web. È possibile creare plug-in e aggiungerli a una singola richiesta, nonché al test delle prestazioni web che la contiene. Un *plug-in richiesta* personalizzato consente di chiamare il codice durante l'esecuzione di una determinata richiesta in un test delle prestazioni web.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Ogni plug-in delle richieste test prestazioni web dispone di un metodo PreRequest e di un metodo PostRequest. Dopo avere allegato un plug-in delle richieste a una determinata richiesta HTTP, l'evento PreRequest viene generato prima dell'invio della richiesta, mentre l'evento PostRequest viene generato dopo la ricezione della risposta.

È possibile creare un plug-in delle richieste test delle prestazioni web personalizzato derivando la classe personalizzata dalla classe di base <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>.

È possibile utilizzare i plug-in delle richieste test delle prestazioni web personalizzati con i test web registrati. I plug-in delle richieste test delle prestazioni web personalizzati consentono di scrivere una quantità minima di codice per ottenere un elevato livello di controllo sui test web. È tuttavia possibile utilizzarli anche con i test delle prestazioni web codificati. Vedere [Generare ed eseguire un test delle prestazioni Web codificato](../test/generate-and-run-a-coded-web-performance-test.md).

## <a name="to-create-a-request-level-plug-in"></a>Per creare un plug-in a livello di richiesta

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sulla soluzione, scegliere **Aggiungi** , quindi **nuovo progetto**.

2. Creare un nuovo progetto **Libreria di classi**.

3. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sulla cartella **riferimenti** nella nuova libreria di classi e selezionare **Aggiungi riferimento**.

     Viene visualizzata la finestra di dialogo **Aggiungi riferimento**.

4. Fare clic sulla scheda **.NET**, scorrere verso il basso, selezionare **Microsoft.VisualStudio.QualityTools.WebTestFramework**, quindi scegliere **OK**.

     Il riferimento a **Microsoft. VisualStudio. QualityTools. WebTestFramework** viene aggiunto alla cartella **riferimenti** in **Esplora soluzioni**.

5. In **Esplora soluzioni**, fare clic con il pulsante destro del mouse sul nodo principale del progetto di test di carico e prestazioni Web contenente il test di carico al quale si desidera aggiungere il plug-in test delle prestazioni Web. Selezionare **Aggiungi riferimento**.

     Verrà visualizzata la finestra di **dialogo Aggiungi riferimento**.

6. Scegliere la scheda **progetti** , selezionare il **progetto libreria di classi** , quindi scegliere **OK** .

7. Nell'**editor di codice** scrivere il codice del plug-in. Creare innanzitutto una nuova classe pubblica derivata dalla classe <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>.

8. Implementare il codice in uno o in entrambi i gestori di evento <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin.PreRequest*> e <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin.PostRequest*>. Per un'implementazione di esempio, vedere la sezione seguente relativa all'esempio.

9. Una volta scritto il codice, compilare il nuovo progetto.

10. Aprire il test delle prestazioni web in cui si desidera aggiungere il plug-in delle richieste.

11. Fare clic con il pulsante destro del mouse sulla richiesta alla quale si vuole aggiungere il plug-in della richiesta, quindi selezionare **Aggiungi plug-in richiesta**.

     Viene visualizzata la finestra di dialogo **Aggiungi plug-in richiesta test Web**.

12. In **Seleziona un plug-in** selezionare il nuovo plug-in.

13. Nel riquadro **Proprietà per il plug-in selezionato** impostare i valori iniziali per il plug-in da usare in fase di esecuzione.

    > [!NOTE]
    > È possibile esporre il numero di proprietà desiderato dai plug-in; è sufficiente renderle pubbliche, impostabili e di un tipo di base quale Integer, Boolean o String. È anche possibile modificare le proprietà del plug-in di test delle prestazioni web in un secondo momento utilizzando la finestra Proprietà.

14. Scegliere **OK**.

     Il plug-in viene aggiunto alla cartella **Plug-in richieste** che è una cartella figlio della richiesta HTTP.

    > [!WARNING]
    > Quando si esegue un test delle prestazioni Web o un test di carico in cui viene usato il plug-in, è possibile che venga visualizzato un errore simile a quello seguente:
    >
    > **Richiesta non riuscita: eccezione nell' \<plug-in> evento: Impossibile caricare il file o l'assembly ' \<"Plug-in name".dll file> , Version = \<n.n.n.n> , Culture = neutral, PublicKeyToken = null ' o una delle relative dipendenze. Il sistema non è in grado di trovare il file specificato.**
    >
    > L'errore si verifica se si effettuano modifiche al codice di uno qualsiasi dei plug-in e si crea una nuova versione del file DLL **(Version=0.0.0.0)**, ma il plug-in fa ancora riferimento alla versione originale. Per risolvere il problema, attenersi ai passaggi riportati di seguito:
    >
    > 1. Nei riferimenti del progetto di test di carico e prestazioni web sarà presente un avviso. Rimuovere e aggiungere nuovamente il riferimento alla DLL del plug-in.
    > 2. Rimuovere il plug-in dal test o dal percorso appropriato, quindi aggiungerlo di nuovo.

## <a name="example"></a>Esempio

È possibile utilizzare il codice seguente per creare un plug-in di test delle prestazioni web che visualizza due finestre di dialogo. In una finestra di dialogo viene visualizzato l'URL associato alla richiesta alla quale si allega il componente aggiuntivo della richiesta. Nella seconda finestra di dialogo viene visualizzato il nome computer dell'agente.

> [!NOTE]
> Per il codice seguente è necessaria l'aggiunta di un riferimento a System.Windows.Forms.

```csharp
using System;
using System.Collections.Generic;
using System.Windows.Forms;
using Microsoft.VisualStudio.TestTools.WebTesting;

namespace RequestPluginNamespace
{
    public class MyWebRequestPlugin : WebTestRequestPlugin
    {
        public override void PostRequest(object sender, PostRequestEventArgs e)
        {
            MessageBox.Show(e.WebTest.Context.AgentName);
        }
        public override void PreRequest(object sender, PreRequestEventArgs e)
        {
            MessageBox.Show(e.Request.Url);
        }
    }
}
```

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>
- [Creare codice personalizzato e plug-in per test di carico](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Codificare una regola di estrazione personalizzata per un test delle prestazioni Web](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Codificare una regola di convalida personalizzata per un test delle prestazioni Web](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Procedura: creare un plug-in test di carico](../test/how-to-create-a-load-test-plug-in.md)
- [Generare ed eseguire un test delle prestazioni Web codificato](../test/generate-and-run-a-coded-web-performance-test.md)
