---
title: Creare un test del servizio Web
ms.date: 06/30/2020
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, creating Web service tests
- Web services [Visual Studio ALM], creating
- service tests, Web
ms.assetid: fbcd57ee-06ad-4260-8694-09f8e0f93e39
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9934f48e6d5900a418995eb96d357b4ea1ea532f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85814759"
---
# <a name="how-to-create-a-web-service-test"></a>Procedura: Creare un test di servizio Web

I test web consentono di testare i servizi web. Utilizzando le opzioni **Inserisci richiesta** e **Inserisci servizio Web** , è possibile personalizzare le singole richieste nell' **Editor test prestazioni Web** per individuare le pagine del servizio Web. Solitamente queste pagine non vengono visualizzate nell'applicazione Web. Pertanto, per poter accedere alle pagine è necessario personalizzare la richiesta.

>[!NOTE]
> La funzionalità del test di carico e delle prestazioni Web è deprecata in Visual Studio 2019. Per Application Insights, i test Web in più passaggi dipendono dai file di test Web di Visual Studio. È stato [annunciato](https://devblogs.microsoft.com/devops/cloud-based-load-testing-service-eol/) che Visual Studio 2019 sarà l'ultima versione con la funzionalità test Web. È importante comprendere che, anche se non vengono aggiunte nuove funzionalità, la funzionalità test Web in Visual Studio 2019 è ancora attualmente supportata e continuerà a esserlo durante il ciclo di vita del prodotto. Il team del prodotto Monitoraggio di Azure ha affrontato le domande relative al futuro dei test di disponibilità in più passi [qui](https://github.com/MicrosoftDocs/azure-docs/issues/26050#issuecomment-468814101).

**Requisiti**

Visual Studio Enterprise

## <a name="to-create-a-simple-web-service"></a>Per creare un servizio Web semplice

Per eseguire il test, è possibile usare il proprio servizio Web o usare il modello di base del servizio Web (ASMX) incluso in Visual Studio. Per creare un servizio Web semplice utilizzando questo modello:

1. In Visual Studio creare un nuovo progetto usando il modello applicazione Web ASP.NET (.NET Framework) e selezionare il modello **vuoto** quando richiesto. Digitare un nome e creare il progetto.

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul nodo del progetto, scegliere **Aggiungi**  >  **nuovo elemento**, quindi scegliere **servizio Web (asmx)**. Aggiungere il servizio Web.

1. Aprire *WebService1. asmx* e sostituire il `HelloWorld` metodo Web predefinito con il codice seguente.

   ```csharp
   public string HelloWorld(string str)
   {
      return "Hello, " + str;
   }
   ```

## <a name="install-the-load-testing-component"></a>Installare il componente di test di carico

Se il componente degli strumenti per test di carico e delle prestazioni Web non è già installato, è necessario installarlo tramite il programma di installazione di Visual Studio.

1. Aprire **programma di installazione di Visual Studio** dal menu **Start** di Windows. È anche possibile accedervi in Visual Studio dalla finestra di dialogo nuovo progetto oppure scegliendo **strumenti**  >  **Ottieni strumenti e funzionalità** dalla barra dei menu.

1. In **Programma di installazione di Visual Studio** scegliere la scheda **Singoli componenti** e scorrere verso il basso fino alla sezione **Debug e test**. Selezionare **Strumenti per test di carico e delle prestazioni Web**.

   ![Componente Strumenti per test di carico e delle prestazioni Web](media/web-perf-load-testing-tools-component.png)

1. Fare clic sul pulsante **Modifica**.

   Il componente Strumenti per test di carico e delle prestazioni Web è stato installato.

## <a name="create-a-web-test-project"></a>Creare un progetto di test Web

Un test Web richiede il modello di progetto di progetto di test di carico e prestazioni Web. In questa sezione si creerà un progetto di test di carico in C#. È anche possibile creare un progetto di test di carico di Visual Basic, se si preferisce.

::: moniker range="vs-2017"

1. Aprire Visual Studio.

   Se si usa il modello del servizio Web di esempio (ASMX), è possibile aggiungere il progetto di test Web alla stessa soluzione.

2. Scegliere **File** > **Nuovo** > **Progetto** dalla barra dei menu.

   Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

3. Nella finestra di dialogo **Nuovo progetto** espandere **Installato** e **Visual C#** e quindi scegliere la categoria **Test**. Scegliere il modello **Progetto di test di carico e prestazioni Web**.

   ![Modello Progetto di test di carico e prestazioni Web](media/web-perf-load-test-project-template.png)

4. Immettere un nome per il progetto se non si vuole usare il nome predefinito e quindi scegliere **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Aprire Visual Studio.

   Se si usa il modello del servizio Web di esempio (ASMX), è possibile aggiungere il progetto di test Web alla stessa soluzione.

2. Nella finestra Start scegliere **Crea un nuovo progetto**.

3. Nella pagina **Crea un nuovo progetto** digitare **test web** nella casella di ricerca e quindi selezionare il modello **Progetto di test di carico e prestazioni Web \[Deprecato]** per C#. Scegliere **Avanti**.

4. Immettere un nome per il progetto se non si vuole usare il nome predefinito e quindi scegliere **Crea**.

::: moniker-end

   Visual Studio crea il progetto e Visualizza i file in **Esplora soluzioni**. Il progetto contiene inizialmente un file di test Web denominato *WebTest1. WebTest*.

## <a name="to-test-a-web-service"></a>Per testare un servizio Web

1. Avviare il servizio Web e, se necessario, scegliere **Interrompi** per sospendere il servizio.

1. Nel progetto di test Web aprire *WebTest1. WebTest*, che apre il Editor test prestazioni Web. Nell'editor di test fare clic con il pulsante destro del mouse sul test delle prestazioni Web e scegliere **Aggiungi richiesta servizio Web**.

1. Nella proprietà **URL** della nuova richiesta digitare il nome del servizio Web, ad esempio **https://localhost:44318/WebService1.asmx** .

1. Per il servizio Web, aprire una sessione separata del browser e digitare l'URL della pagina *asmx* nella barra degli strumenti **Indirizzo** . Nella parte superiore della pagina Web selezionare il metodo che si desidera testare ed esaminare il messaggio SOAP. Nel servizio Web di esempio, il metodo è HelloWorld. Quando si apre il metodo, si noterà che contiene un oggetto `SOAPAction` .

1. Nell'**Editor test prestazioni Web** fare clic con il pulsante destro del mouse sulla richiesta, quindi scegliere **Aggiungi intestazione** per aggiungere una nuova intestazione. Nella proprietà **Nome** digitare `SOAPAction`. Nella proprietà **valore** Digitare il valore visualizzato in `SOAPAction` , ad esempio *http://tempuri.org/HelloWorld* .

1. Espandere il nodo URL nell'editor di test, scegliere il nodo **corpo stringa** e nella proprietà **tipo di contenuto** immettere un valore `text/xml` .

1. Tornare al browser del passaggio 4, selezionare la parte XML della richiesta SOAP dalla pagina descrittiva del servizio Web, quindi copiarla negli Appunti.

   Il contenuto XML è simile a quello riportato nell'esempio seguente:

     ```xml
     <?xml version="1.0" encoding="utf-8"?>
     <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
       <soap:Body>
         <HelloWorld xmlns="http://tempuri.org/">
           <str>string</str>
         </HelloWorld>
       </soap:Body>
     </soap:Envelope>
     ```

1. Tornare alla Editor test prestazioni Web, quindi scegliere i puntini di sospensione **(...)** nella proprietà **corpo stringa** . Incollare il contenuto degli Appunti nella proprietà.

1. Sostituire i valori segnaposto nel codice XML con i valori validi in modo che il test possa essere superato. Nell'esempio precedente, l'istanza di viene sostituita `string` con un nome.

1. Fare clic con il pulsante destro del mouse sulla richiesta del servizio Web e selezionare **Aggiungi parametro QUERYSTRING URL**.

1. Assegnare un nome e un valore al parametro della stringa di query. Nell'esempio precedente il nome è `op` e il valore è `HelloWorld`. Tramite il nome e il valore viene identificata l'operazione di servizio Web da eseguire.

    > [!NOTE]
    > È possibile utilizzare data binding nel corpo SOAP per sostituire qualsiasi valore segnaposto con valori associati a dati utilizzando la `{{DataSourceName.TableName.ColumnName}}` sintassi.

1. Eseguire il test. Nel riquadro superiore del **Visualizzatore risultati test prestazioni web** selezionare la richiesta di servizio Web. Nel riquadro inferiore selezionare la scheda **Web browser** . Verrà visualizzato il codice XML restituito dal servizio Web e i risultati delle operazioni.

   Cercare i risultati per la richiesta del servizio Web.

## <a name="see-also"></a>Vedere anche

- [Creare codice personalizzato e plug-in per test di carico](../test/create-custom-code-and-plug-ins-for-load-tests.md)
