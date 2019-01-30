---
title: Creare un test del servizio Web
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, creating Web service tests
- Web services [Visual Studio ALM], creating
- service tests, Web
ms.assetid: fbcd57ee-06ad-4260-8694-09f8e0f93e39
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.openlocfilehash: 227c9674434e5f49b322e614c8b8c7ffefda2128
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54964574"
---
# <a name="how-to-create-a-web-service-test"></a>Procedura: Creare un test di servizio Web

I test web consentono di testare i servizi web. Tramite le opzioni **Inserisci richiesta** e **Inserisci richiesta servizio Web** è possibile personalizzare le singole richieste nell'**Editor test prestazioni Web** in modo da individuare le pagine di servizi Web. Solitamente queste pagine non vengono visualizzate nell'applicazione Web. Pertanto, per poter accedere alle pagine è necessario personalizzare la richiesta.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Nelle procedure seguenti si usa un servizio Web contenuto nel Commerce Starter Kit. È possibile scaricarlo da [ASP.NET Commerce Starter Kit](http://go.microsoft.com/fwlink/?LinkId=181469).

**Requisiti**

Visual Studio Enterprise

## <a name="to-test-a-web-service"></a>Per testare un servizio Web

1.  Creare un nuovo test Web. Non appena si apre il browser, scegliere **Interrompi**.

2.  Nell'**Editor test prestazioni Web** fare clic con il pulsante destro del mouse sul test prestazioni Web, quindi scegliere **Aggiungi richiesta servizio Web**.

3.  Nella proprietà **Url** della nuova richiesta immettere il nome del servizio Web, ad esempio **http://localhost/storecsvs/InstantOrder.asmx**.

4.  Aprire una sessione separata del browser e digitare l'URL della pagina con estensione *asmx* sulla barra degli strumenti **Indirizzo**. Selezionare il metodo da testare, quindi esaminare il messaggio SOAP. Esso contiene una `SOAPAction`.

5.  Nell'**Editor test prestazioni Web** fare clic con il pulsante destro del mouse sulla richiesta, quindi scegliere **Aggiungi intestazione** per aggiungere una nuova intestazione. Nella proprietà **Nome** digitare `SOAPAction`. Nella proprietà **Valore** digitare il valore contenuto in `SOAPAction`, ad esempio `"http://tempuri.org/CheckStatus"`.

6.  Espandere il nodo URL nell'editor, scegliere il nodo **Corpo stringa** e nella proprietà **Tipo di contenuto** immettere un valore `text/xml`.

7.  Tornare al browser del passaggio 4, selezionare la parte XML della richiesta SOAP dalla pagina descrittiva del servizio Web, quindi copiarla negli Appunti.

8.  Il contenuto XML è simile a quello riportato nell'esempio seguente:

     ```xml
     <?xml version="1.0" encoding="utf-8"?>
     <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
     <soap:Body>
       <CheckStatus xmlns="http://tempuri.org/">
         <userName>string</userName>
         <password>string</password>
         <orderID>int</orderID>
       </CheckStatus>
     </soap:Body>
     </soap:Envelope>
     ```

9. Tornare all'**Editor test prestazioni Web** e quindi scegliere i puntini di sospensione **(…)** nella proprietà **Corpo stringa**. Incollare il contenuto degli Appunti nella proprietà.

10. Sostituire i valori segnaposto con valori XML validi che consentiranno di superare il test. Nell'esempio precedente si devono sostituire le due istanze di `string` e la singola istanza di `int`. L'operazione del servizio Web potrà essere terminata solamente se un utente registrato ha effettuato un ordine.

11. Fare clic con il pulsante destro del mouse sulla richiesta di servizio Web, quindi scegliere **Aggiungi parametro QueryString URL**.

12. Assegnare un nome e un valore al parametro della stringa di query. Nell'esempio precedente il nome è `op` e il valore è `CheckStatus`. Tramite il nome e il valore viene identificata l'operazione di servizio Web da eseguire.

    > [!NOTE]
    > È possibile usare il data binding nel corpo SOAP per sostituire i valori segnaposto con valori associati a dati mediante la sintassi `{{DataSourceName.TableName.ColumnName}}`.

13. Eseguire il test. Nel riquadro superiore del **Visualizzatore risultati test prestazioni web** selezionare la richiesta di servizio Web. Nel riquadro inferiore selezionare la scheda Web browser. Verranno visualizzati l'XML restituito dal servizio Web e i risultati di tutte le operazioni.

## <a name="see-also"></a>Vedere anche

- [Creare codice personalizzato e plug-in per test di carico](../test/create-custom-code-and-plug-ins-for-load-tests.md)