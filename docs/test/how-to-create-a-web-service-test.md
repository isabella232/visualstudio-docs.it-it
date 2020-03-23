---
title: Creare un test del servizio Web
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, creating Web service tests
- Web services [Visual Studio ALM], creating
- service tests, Web
ms.assetid: fbcd57ee-06ad-4260-8694-09f8e0f93e39
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7a6e42d6d92a74a0fc8be96c966b9146b7888b9e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589097"
---
# <a name="how-to-create-a-web-service-test"></a>Procedura: Creare un test di servizio Web

I test web consentono di testare i servizi web. Utilizzando le opzioni **Inserisci richiesta** e Inserisci richiesta **servizio Web,** è possibile personalizzare le singole richieste nell'Editor **test prestazioni Web** per individuare le pagine del servizio Web. Solitamente queste pagine non vengono visualizzate nell'applicazione Web. Pertanto, per poter accedere alle pagine è necessario personalizzare la richiesta.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Nelle procedure seguenti si usa un servizio Web contenuto nel Commerce Starter Kit. È possibile scaricarlo da [ASP.NET Commerce Starter Kit](https://sourceforge.net/projects/ppcsk/).

**Requisiti**

Visual Studio Enterprise

## <a name="to-test-a-web-service"></a>Per testare un servizio Web

1. Creare un nuovo test delle prestazioni Web. Non appena si apre il browser, scegliere **Interrompi**.

2. **Nell'Editor test prestazioni Web**fare clic con il pulsante destro del mouse sul test delle prestazioni Web e scegliere Aggiungi richiesta servizio **Web**.

3. Nella proprietà **Url** della nuova richiesta digitare il nome **http://localhost/storecsvs/InstantOrder.asmx**del servizio Web, ad esempio .

4. Aprire una sessione separata del browser e digitare l'URL della pagina con estensione *asmx* sulla barra degli strumenti **Indirizzo**. Selezionare il metodo da testare, quindi esaminare il messaggio SOAP. Contiene un elemento `SOAPAction`.

5. Nell'**Editor test prestazioni Web** fare clic con il pulsante destro del mouse sulla richiesta, quindi scegliere **Aggiungi intestazione** per aggiungere una nuova intestazione. Nella proprietà **Nome** digitare `SOAPAction`. Nella proprietà **Valore** digitare il valore contenuto in `SOAPAction`, ad esempio `"http://tempuri.org/CheckStatus"`.

6. Espandere il nodo URL nell'editor, scegliere il nodo **Corpo stringa** e nella proprietà **Tipo di contenuto** immettere un valore `text/xml`.

7. Tornare al browser del passaggio 4, selezionare la parte XML della richiesta SOAP dalla pagina descrittiva del servizio Web, quindi copiarla negli Appunti.

8. Il contenuto XML è simile a quello riportato nell'esempio seguente:

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

11. Fare clic con il pulsante destro del mouse sulla richiesta del servizio Web e scegliere **Aggiungi parametro QueryString URL**.

12. Assegnare un nome e un valore al parametro della stringa di query. Nell'esempio precedente il nome è `op` e il valore è `CheckStatus`. Tramite il nome e il valore viene identificata l'operazione di servizio Web da eseguire.

    > [!NOTE]
    > È possibile usare l'associazione dati nel corpo SOAP per sostituire i valori segnaposto con valori associati a dati mediante la sintassi `{{DataSourceName.TableName.ColumnName}}`.

13. Eseguire il test. Nel riquadro superiore del **Visualizzatore risultati test prestazioni web** selezionare la richiesta di servizio Web. Nel riquadro inferiore selezionare la scheda del browser Web. Verrà visualizzato il codice XML restituito dal servizio Web e i risultati di tutte le operazioni.

## <a name="see-also"></a>Vedere anche

- [Creare codice personalizzato e plug-in per test di carico](../test/create-custom-code-and-plug-ins-for-load-tests.md)
