---
title: Creare un report delle prestazioni del test di carico usando Excel
description: Informazioni su come generare report Microsoft Excel test di carico basati su due o più risultati dei test. È possibile creare report di confronto e di tendenza di esecuzione.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, creating Excel reports
- load tests, reporting
ms.assetid: b87fb196-9973-4512-a924-088788def4ea
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: f40d477122bbf3fe0057fa1010b9847fa5a7cae0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122075853"
---
# <a name="how-to-create-load-test-performance-reports-using-microsoft-excel"></a>Procedura: Creare report di prestazioni dei test di carico usando Microsoft Excel

È possibile generare report del test di carico di Microsoft Excel basati su due o più risultati del test.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Sono disponibili due tipi di report del test di carico:

- **Esegui confronto** Consente di creare un set di report per il confronto dei dati di due risultati del test di carico tramite tabelle e grafici a barre.

- **Tendenza** È possibile generare l'analisi delle tendenze in due o più risultati del test di carico. I risultati vengono visualizzati usando grafici a linee, ma i dati sono disponibili in tabelle pivot.

> [!TIP]
> È inoltre possibile creare manualmente report di Microsoft Word copiando e incollando dati dalle visualizzazioni Riepilogo, Grafici e Tabelle. Vedere [Procedura: Creare manualmente un report delle prestazioni del test di carico usando Microsoft Word](../test/how-to-manually-create-a-load-test-performance-report-using-microsoft-word.md).

Ciascun report può essere usato per condividere dati relativi alle prestazioni con le parti interessate e mostrare se le prestazioni complessive e l'integrità del sistema stanno migliorando o peggiorando.

Le definizioni del report vengono archiviate nel database del test di carico. Quando viene salvato un report, la definizione per il report viene salvata nel database e può essere usata nuovamente in un secondo momento.

Inoltre, la cartella di lavoro di Excel può essere condivisa con le parti interessate in modo che esse non debbano connettersi al database per vedere il report.

> [!NOTE]
> È possibile condividere la cartella di lavoro di Excel; tuttavia, solo gli utenti con computer in cui è installato Visual Studio saranno in grado di modificare i fogli di calcolo. Gli altri utenti non visualizzano **l'opzione Report test** di carico nella barra **multifunzione Office,** ma potranno visualizzare la cartella di lavoro.

Nella figura seguente è illustrato un esempio di report in cui viene mostrata una correlazione tra una riduzione della velocità della transazione di aggiornamento del carrello e l'alterazione del contatore di percentuale processore. Ciò indica un potenziale problema nel codice dell'applicazione, anziché nel database o nella rete, ed è una situazione adatta alla diagnosi tramite il profiler ASP.NET.

![Possibile problema nel codice dell'applicazione](../test/media/lt_excel.png)

Excel report possono essere generati nell'Analizzatore test di carico , tramite il pulsante Crea **report Excel** sulla  barra degli strumenti o da Excel usando l'opzione Report test di carico nella scheda **Test** di carico della barra **multifunzione Office.**

> [!NOTE]
> Se si aggiungono commenti a un test di carico, vengono visualizzati nel report di Excel.

## <a name="to-generate-load-test-comparison-reports-using-excel"></a>Per generare report di confronto di test di carico con Excel

1. Prima di generare un report, è necessario eseguire un test di carico.

2. È possibile creare report del test di carico di Excel in due modi:

   - Dopo avere completato un test di carico, nella pagina **Risultati test di carico** scegliere il pulsante **Crea rapporto Excel** sulla barra degli strumenti.

      > [!NOTE]
      > Se il **pulsante Crea Excel report** è disabilitato nella barra degli strumenti del Visualizzatore prestazioni Web **Risultati test,** potrebbe essere necessario eseguire Microsoft Excel una volta prima che venga abilitato. Quando viene installato Visual Studio Enterprise, nel computer viene copiato il componente aggiuntivo dei test di carico di Visual Studio Entperprise per Microsoft Excel. Per completare il processo di installazione del componente aggiuntivo è tuttavia necessario eseguire Microsoft Excel.

      Microsoft Excel viene visualizzata la Creazione **guidata report test di carico**.

   **OR**

   1. Aprire Microsoft Excel, selezionare la scheda **Test di** carico nella barra **multifunzione Office** e quindi scegliere Report test **di carico.**

       Verrà **visualizzata la Creazione guidata report test di** carico.

   2. Nella pagina **Selezionare il database che contiene i test di carico**, in **Nome server** digitare il nome del server che contiene i risultati del test di carico.

   3. Nell'elenco a discesa **Nome database** selezionare il database contenente i risultati del test di carico.

3. Nella pagina **Scegliere la modalità di generazione del rapporto** verificare che l'opzione **Crea rapporto** sia selezionata e scegliere **Avanti**.

4. Nella pagina **Tipo di report da generare** verificare che l'opzione **Esegui confronto** sia selezionata e scegliere **Avanti**.

5. Nella pagina **Immettere i dettagli del rapporto test di carico** digitare un nome per il report in **Nome rapporto**.

6. Selezionare il test di carico per il quale generare il report e scegliere **Avanti**.

7. Nella pagina **Selezionare le esecuzioni per il rapporto**, in **Selezionare una o più esecuzioni da aggiungere al rapporto** selezionare due risultati del test di carico da confrontare nel report e scegliere **Avanti**.

   > [!NOTE]
   > È possibile generare un report di confronto solo per due risultati del test di carico. Se si selezionano un solo risultato o più di due risultati del test di carico, verrà visualizzato un messaggio di avviso.

8. Nella pagina **Selezionare i contatori** per il report in Selezionare uno o più contatori da aggiungere al **report** è disponibile un elenco espandibile di contatori per personalizzare il report. Selezionare i contatori che si vuole confrontare dalle due esecuzioni di test selezionate nel report e scegliere **Fine**.

9. Viene generato il report della cartella di lavoro di Excel che include i seguenti fogli di lavoro:

   - **Sommario**: visualizza il nome del report del test di carico e un sommario con collegamenti alle varie schede nel report.

   - **Esecuzioni**: visualizza i dettagli sulle due esecuzioni confrontate nel report.

   - **Confronto test**: visualizza i dettagli del grafico a barre sulle regressioni e i miglioramenti delle prestazioni tra le due esecuzioni confrontate.

   - **Confronto pagine**: visualizza dati di confronto delle prestazioni in percentuale e in un grafico a barre tra le due esecuzioni relativamente alle varie pagine nelle esecuzioni di test.

   - **Confronto computer**: visualizza i dati di confronto tra le due esecuzioni basate sui computer utilizzati.

   - **Confronto errore**: confronta i tipi di errore incontrati tra le due esecuzioni e il numero di occorrenze.

     > [!TIP]
     > Per offrire report più dettagliati, sono disponibili diverse proprietà in test di carico e test delle prestazioni web. La richiesta della pagina dispone di due proprietà presentate nei report: Obiettivo e Nome rapporto. I tempi di risposta della pagina saranno riportati rispetto all'obiettivo e il nome del report sarà usato al posto dell'URL nei report. In Impostazioni di esecuzione dei test di carico, in Gestisci insiemi di contatori, la proprietà Tag computer è presentata nei nomi dei computer del report. È molto utile per descrivere il ruolo di un particolare computer nel report.

## <a name="to-generate-load-test-trend-reports-using-excel"></a>Per generare report sulla tendenza del test di carico con Excel

1. Prima di generare un report, è necessario eseguire un test di carico.

2. È possibile creare report del test di carico di Excel in due modi:

   - Dopo avere completato un test di carico, nella pagina **Risultati test di carico** scegliere il pulsante **Crea rapporto Excel** sulla barra degli strumenti.

      > [!NOTE]
      > Se il **pulsante Crea Excel report** è disabilitato nella barra degli strumenti del Visualizzatore prestazioni Web **Risultati test,** potrebbe essere necessario eseguire Microsoft Excel una volta prima che venga abilitato. Quando viene installato Visual Studio Enterprise, nel computer viene copiato il componente aggiuntivo dei test di carico di Visual Studio Entperprise per Microsoft Excel. Per completare il processo di installazione del componente aggiuntivo è tuttavia necessario eseguire Microsoft Excel.

      Microsoft Excel viene visualizzata la Creazione **guidata report test di carico**.

   **OR**

   1. Aprire Microsoft Excel, selezionare la scheda **Test di** carico nella barra **multifunzione Office** e quindi scegliere Report test **di carico.**

       Verrà **visualizzata la Creazione guidata report test di** carico.

   2. Nella pagina **Selezionare il database che contiene i test di carico**, in **Nome server** digitare il nome del server che contiene i risultati del test di carico.

   3. Nell'elenco a discesa **Nome database** selezionare il database contenente i risultati del test di carico.

3. Nella pagina **Scegliere la modalità di generazione del rapporto** verificare che l'opzione **Crea rapporto** sia selezionata e scegliere **Avanti**.

4. Nella pagina **Tipo di report da generare** verificare che l'opzione **Tendenza** sia selezionata e scegliere **Avanti**.

5. Nella pagina **Immettere i dettagli del rapporto test di carico** digitare un nome per il report in **Nome rapporto**.

6. Selezionare il test di carico per il quale generare il report e scegliere **Avanti**.

7. Nella pagina **Selezionare le esecuzioni per il rapporto**, in **Selezionare una o più esecuzioni da aggiungere al rapporto** selezionare i risultati del test di carico da confrontare nel report e scegliere **Avanti**.

8. Nella pagina **Selezionare i contatori per il rapporto**, in **Selezionare uno o più contatori da aggiungere al rapporto**, è disponibile un elenco espandibile di contatori per personalizzare il report. Dalle esecuzioni dei test selezionate nel report, selezionare i contatori da confrontare per l'analisi delle tendenze e scegliere **Fine**.

9. Il report viene generato con un sommario contenente collegamenti alle varie schede della cartella di lavoro di Excel generate nel report. I collegamenti sono basati sui contatori selezionati per il report della tendenza. Ad esempio, se sono stati lasciati i contatori predefiniti selezionati nel passaggio 7, il report genererà dati presentati in schede separate in Excel per ogni contatore elencato nel passaggio 7. I dati generati per ogni contatore vengono presentati in grafici dello stile tendenza.

   > [!TIP]
   > Per offrire report più dettagliati, sono disponibili diverse proprietà in test di carico e test delle prestazioni web. La richiesta della pagina dispone di due proprietà presentate nei report: Obiettivo e Nome rapporto. I tempi di risposta della pagina saranno riportati rispetto all'obiettivo e il nome del report sarà usato al posto dell'URL nei report. In Impostazioni di esecuzione dei test di carico, in Gestisci insiemi di contatori, la proprietà Tag computer è presentata nei nomi dei computer del report. È molto utile per descrivere il ruolo di un particolare computer nel report.

## <a name="net-security"></a>Protezione .NET

I risultati e i report del test di carico contengono informazioni potenzialmente riservate che potrebbero essere utilizzate per realizzare un attacco al computer o alla rete. I risultati e i report del test di carico contengono nomi di computer e stringhe di connessione. Quando si condividono i report del test di carico con altre persone, è necessario tenere in considerazione tali rischi.

## <a name="see-also"></a>Vedi anche

- [Creare report sui risultati dei test di carico per confronti tra test o analisi delle tendenze](../test/compare-load-test-results.md)
