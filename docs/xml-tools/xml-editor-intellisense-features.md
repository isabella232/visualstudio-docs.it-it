---
title: Funzionalità IntelliSense dell'editor XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 2b26f214-cc3a-46bf-b260-14eb8e599182
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 36350123135142e84adff0c3189ba81e31ebf6b2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53986206"
---
# <a name="xml-editor-intellisense-features"></a>Funzionalità IntelliSense dell'Editor XML

L'editor XML fornisce funzionalità IntelliSense avanzate paragonabili a quelle di altri editor di linguaggio forniti in Visual Studio. Questa sezione illustra come usare IntelliSense con documenti XML Schema Definition Language (XSD) e XSLT.

## <a name="intellisense-in-an-xsd-document"></a>IntelliSense in un documento XSD
 Dopo uno schema è associato al documento, viene visualizzato un elenco di riepilogo a discesa degli elementi previsti ogni volta che si digita `"<"` oppure fare clic sui **visualizzare un elenco di oggetti membro** pulsante sulla barra degli strumenti editor XML. Per informazioni su come associare gli schemi ai documenti XML, vedere [convalida dei documenti XML](../xml-tools/xml-document-validation.md).

 Quando si preme BARRA SPAZIATRICE all'interno di un tag di inizio, viene visualizzato anche un elenco a discesa contenente tutti gli attributi che possono essere aggiunti all'elemento corrente.

 Quando si digita `"="` per il valore di un attributo oppure la virgoletta di apertura per il valore, viene visualizzato anche un elenco dei possibili valori dell'attributo. I valori vengono forniti solo se lo schema fornisce valori enumerati mediante i facet `xsd:enumeration` o se l'attributo è di tipo `Boolean`. In IntelliSense Viene inoltre fornito un elenco dei codici lingua noti per `xml:lang` o per qualsiasi `simpleType` derivato da `xsd:language`. Per le dichiarazioni dello spazio dei nomi, viene fornito un elenco di IntelliSense dei valori `targetNamespace` noti.

 Un elenco di IntelliSense dei valori possibili viene inoltre visualizzato quando si digita `">"` per chiudere un tag di inizio se l'elemento è un `simpleType`. Il comportamento degli elementi è simile al comportamento degli attributi descritto nel paragrafo precedente.

 Negli elenchi di IntelliSense vengono visualizzate anche le descrizioni comandi basate sulle informazioni relative a `xsd:annotation` e `xsd:documentation` rilevate nello schema associato.

## <a name="intellisense-in-an-xslt-document"></a>IntelliSense in un documento XSLT
 Dopo avere aggiunto un modello denominato o un attributo al documento XSLT, è possibile usare IntelliSense per inserire gli elementi seguenti:

-   Nomi del set di attributi.

-   Modalità modello.

-   Nomi di modello.

-   Nomi del parametro per una determinata modalità.

-   Nomi del parametro per un determinato modello denominato.

Per altre informazioni, vedere [Procedura dettagliata: Uso di XSLT IntelliSense](../xml-tools/walkthrough-using-xslt-intellisense.md) argomento.

## <a name="auto-completion"></a>Completamento automatico
 L'editor XML, inoltre, semplifica la procedura di modifica del codice XML in quanto la sintassi XML richiesta viene inserita automaticamente. Ad esempio, se si digita il seguente tag di inizio:

 `<book>`

 L'editor XML inserisce il tag di fine e posiziona il cursore dopo il tag di inizio. Di seguito è riportato un esempio (il "&#124;" note sulla posizione del cursore):

 `<book>`&#124;`</book>`

 Dal momento che i valori degli attributi devono essere sempre racchiusi tra virgolette, queste vengono inserite automaticamente dall'editor XML. Se ad esempio si digita quanto segue:

 `<book title=`

 L'editor XML aggiunge le virgolette e posiziona il cursore tra le virgolette:

 `<book title="`&#124;`"`

 Analogamente, l'editor XML inserisce automaticamente anche la seguente sintassi XML:

-   Termina un'istruzione di elaborazione: `?>`

-   Termina un blocco CDATA: `]]>`

-   Termina un commento: `-->`

-   Termina una dichiarazione DTD: `>`

L'editor XML è anche la possibilità di inserire uno spazio dei nomi se si seleziona un elemento completo dello spazio dei nomi o attributi da un elenco di IntelliSense e lo spazio dei nomi per tale elemento o attributo non sono ancora nell'ambito di dichiarazione.

Ad esempio, se dall'elenco di IntelliSense si seleziona l'elemento `e:Book` in cui il prefisso è associato allo spazio dei nomi `http://books` che non è stato dichiarato nel documento, l'editor XML inserirà automaticamente la dichiarazione dello spazio dei nomi richiesta. Di seguito è riportato il testo XML risultante:

`<e:Book xmlns:e="http://books"`

## <a name="brace-matching"></a>Corrispondenza parentesi graffe
 Nell'editor XML è inclusa una funzionalità per l'evidenziazione delle parentesi graffe, che fornisce un feedback immediato sugli elementi appena chiusi. È anche possibile usare i tasti di scelta rapida (**Ctrl**+**]**) per passare da una parentesi graffa a parentesi graffa corrispondente.

 L'editor XML effettua tale operazione per i seguenti elementi:

-   Tag di inizio e di fine corrispondenti.

-   Qualsiasi coppia di "\<" o ">" angolari.

-   Inizio e fine dei commenti.

-   Inizio e fine delle istruzioni di elaborazione.

-   Inizio e fine dei blocchi CDATA.

-   Inizio e fine delle dichiarazioni DTD.

-   Virgolette di apertura e chiusura sugli attributi.

## <a name="modify-the-intellisense-options"></a>Modificare le opzioni di IntelliSense
 Le funzionalità IntelliSense e di completamento automatico sono abilitate per impostazione predefinita. Tuttavia, è possibile modificare questo modificando il **Tools** > **opzioni** impostazioni.

 Il **inserimento automatico** sezione il **varie** pagina controlla il comportamento seguente:

|nome|Descrizione|
|-|-----------------|
|Tag di fine|Inserisce i tag di chiusura per i nuovi elementi.|
|Virgolette per attributi|Inserisce i valori di attributo tra virgolette quando si immette un nuovo nome di attributo.|
|Altro markup|Completa commenti, CDATA, DOCTYPE, istruzioni di elaborazione e altre dichiarazioni dei markup.|

### <a name="to-change-the-auto-completion-behavior"></a>Per modificare il comportamento del completamento automatico

1.  Scegliere **Opzioni** dal menu **Strumenti**.

2.  Espandere **Editor di testo**, espandere **XML**e selezionare **varie**.

3.  Apportare modifiche per il **inserimento automatico** della sezione e fare clic su **OK**.

## <a name="see-also"></a>Vedere anche

- [Editor XML](../xml-tools/xml-editor.md)
- [Utilizzo di IntelliSense](../ide/using-intellisense.md)
- [Procedura dettagliata: Uso di XSLT IntelliSense](../xml-tools/walkthrough-using-xslt-intellisense.md)