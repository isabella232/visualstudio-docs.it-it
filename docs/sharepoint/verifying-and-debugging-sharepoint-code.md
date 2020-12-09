---
title: Verifica e debug del codice SharePoint | Microsoft Docs
description: Verificare ed eseguire il debug del codice SharePoint. Usare IntelliTrace per esaminare gli eventi passati e lo stato corrente nella soluzione. Usare gli unit test per assicurarsi che i metodi funzionino correttamente.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- unit testing [SharePoint development in Visual Studio]
- IntelliTrace [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, IntelliTrace
- SharePoint development in Visual Studio, unit testing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ce891e40552c0f8927bfd4ce006b750b6e5f8a54
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914504"
---
# <a name="verify-and-debug-sharepoint-code"></a>Verificare ed eseguire il debug del codice SharePoint
Con IntelliTrace e unit test è possibile eseguire più facilmente il debug delle soluzioni SharePoint, nonché garantire il corretto funzionamento di ogni singolo metodo in esse. È possibile utilizzare queste funzionalità per i progetti SharePoint in Visual Studio seguendo le stesse procedure usate per altri tipi di progetti.

## <a name="intellitrace"></a>IntelliTrace
Con IntelliTrace è possibile determinare non solo lo stato corrente della soluzione SharePoint ma anche gli eventi generati in passato e il contesto in cui si sono verificati. È possibile scorrere i diversi momenti della soluzione SharePoint in cui sono stati registrati eventi di interesse, esaminando gli stati e i valori delle variabili in ogni punto. Grazie a questa navigazione dinamica, il debug delle soluzioni SharePoint è più facile e rapido, senza la necessità di impostare numerosi punti di interruzione. È anche possibile salvare la sessione di debug in un file di log IntelliTrace (con *estensione iTrace*), aprirlo in un secondo momento in Visual Studio Enterprise ed eseguire il debug dopo l'arresto anomalo del sistema. Il file con *estensione iTrace* include informazioni dettagliate su quando e dove si sono verificati errori specifici di SharePoint, in modo da individuare più facilmente le cause degli errori. Le informazioni nel file con *estensione iTrace* sono un subset del log degli errori completo creato da Unified Logging System (ULS) in SharePoint. Queste informazioni prevedono eventi specifici di SharePoint, ad esempio quando un profilo utente viene aperto o chiuso e quando le proprietà in un progetto SharePoint vengono caricate, lette o modificate. È possibile configurare quali eventi vengono registrati da IntelliTrace. Per altre informazioni, vedere [Uso dei dati di IntelliTrace salvati](../debugger/using-saved-intellitrace-data.md).

Quando si verifica un errore in SharePoint, nella finestra di dialogo dell'errore viene visualizzato un identificatore "ID correlazione" di questo errore specifico. È anche possibile ottenere gli ID correlazione dagli eventi elencati nel file con *estensione iTrace* . Per visualizzare un elenco di tutti gli eventi che si sono verificati con un ID correlazione specificato, è possibile immettere l'ID nella sezione **analisi** della pagina di riepilogo di IntelliTrace. In questa sezione è possibile scegliere se visualizzare solo i nomi degli eventi che si sono verificati o i nomi degli eventi con le informazioni sulle chiamate, ad esempio il nome della funzione, i punti di uscita e ingresso, i parametri e i valori restituiti.

È possibile ottenere gli eventi di Visual Studio in IntelliTrace scegliendo il tasto **F5** . Per ottenere gli eventi specifici di SharePoint, tuttavia, è necessario raccogliere i dati IntelliTrace nelle soluzioni SharePoint tramite Microsoft Monitoring Agent. Questo strumento raccoglie i dati IntelliTrace e crea file con *estensione iTrace* per le applicazioni distribuite all'esterno di Visual Studio. Per altre informazioni, vedere [funzionalità IntelliTrace](../debugger/intellitrace-features.md) e [uso dell'agente di raccolta autonomo IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md).

## <a name="unit-test"></a>Unit test
È possibile individuare più facilmente gli errori nel codice eseguendo unit test, in cui è possibile scrivere ed eseguire il codice di test all'interno di metodi di test. Questi metodi contengono variabili vuote e un'istruzione Assert che è possibile usare per verificare la logica e la funzionalità del progetto in base al modello a oggetti di SharePoint. Per altre informazioni, vedere [Eseguire unit test del codice](../test/unit-test-your-code.md).

### <a name="support-for-microsoft-fakes-framework"></a>Supporto per il Framework Microsoft Fakes
I progetti SharePoint supportano Microsoft Fakes, vale a dire un framework di isolamento in cui è possibile creare shim e test stub basati su delegati in applicazioni basate su .NET Framework. Utilizzando il framework Fakes, è possibile creare, gestire e inserire implementazioni fittizie negli unit test. Tramite questi stub e shim è possibile isolare gli unit test dall'ambiente. È possibile creare stub per testare il codice tramite cui vengono utilizzate interfacce o classi non sealed con metodi che possono essere sottoposti a override. È possibile creare shim per reindirizzare le chiamate hardcoded a classi sealed con metodi statici o non sottoponibili a override in un'implementazione alternativa di shim. È inoltre possibile utilizzare i delegati con tipi di stub e di shim per personalizzare dinamicamente il comportamento di singoli membri stub. Per ulteriori informazioni, vedere [isolamento del codice sottoposto a test con Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md).

## <a name="related-articles"></a>Articoli correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[IntelliTrace](../debugger/intellitrace.md)|Viene descritto come eseguire più facilmente il debug delle soluzioni di Visual Studio utilizzando IntelliTrace.|
|[Procedura dettagliata: debug di un'applicazione di SharePoint tramite IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)|Viene illustrato come utilizzare IntelliTrace per individuare errori di codice in un progetto SharePoint.|
|[Eseguire unit test del codice](../test/unit-test-your-code.md)|Viene descritto come trovare errori di logica nel codice tramite unit test.|

## <a name="see-also"></a>Vedi anche

- [Migliorare la qualità del codice](../test/improve-code-quality.md)