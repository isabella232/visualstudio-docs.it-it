---
title: Verifica e debug del codice di SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- unit testing [SharePoint development in Visual Studio]
- IntelliTrace [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, IntelliTrace
- SharePoint development in Visual Studio, unit testing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: eb462c01b1c4809a192d432ad1364dcaa58e0277
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/27/2018
ms.locfileid: "53804000"
---
# <a name="verify-and-debug-sharepoint-code"></a>Verificare ed eseguire il debug del codice di SharePoint
Con IntelliTrace e il testing unità è possibile eseguire più facilmente il debug delle soluzioni SharePoint, nonché garantire il corretto funzionamento di ogni singolo metodo in esse. È possibile usare queste funzionalità per i progetti di SharePoint in Visual Studio, seguire le stesse procedure utilizzate per altri tipi di progetti.

## <a name="intellitrace"></a>IntelliTrace
Con IntelliTrace è possibile determinare non solo lo stato corrente della soluzione SharePoint ma anche gli eventi generati in passato e il contesto in cui si sono verificati. È possibile scorrere i diversi momenti della soluzione SharePoint in cui sono stati registrati eventi di interesse, esaminando gli stati e i valori delle variabili in ogni punto. Grazie a questa navigazione dinamica, il debug delle soluzioni SharePoint è più facile e rapido, senza la necessità di impostare numerosi punti di interruzione. È inoltre possibile salvare la sessione di debug in un log IntelliTrace (*iTrace*) del file, aprirlo in un secondo momento in Visual Studio Enterprise ed eseguire il debug di post-arresto anomalo. Il *iTrace* file include informazioni dettagliate su quando e dove si sono verificati errori specifici di SharePoint, in modo che è possibile determinare la causa di errori. Le informazioni contenute nel *iTrace* file è un subset del log degli errori completo che crea la registrazione del sistema unificato in SharePoint. Queste informazioni prevedono eventi specifici di SharePoint, ad esempio quando un profilo utente viene aperto o chiuso e quando le proprietà in un progetto SharePoint vengono caricate, lette o modificate. È possibile configurare quali eventi vengono registrati da IntelliTrace. Per altre informazioni, vedere [tramite dati di IntelliTrace salvati](../debugger/using-saved-intellitrace-data.md).

Quando si verifica un errore in SharePoint, nella finestra di dialogo dell'errore viene visualizzato un identificatore "ID correlazione" di questo errore specifico. È anche possibile ottenere gli ID di correlazione dagli eventi elencati nel *iTrace* file. Per visualizzare un elenco di tutti gli eventi che si sono verificati con un ID di correlazione specificato, è possibile immettere l'ID nel **analisi** sezione della pagina di riepilogo di IntelliTrace. In questa sezione è possibile scegliere se visualizzare solo i nomi degli eventi che si sono verificati o i nomi degli eventi con le informazioni sulle chiamate, ad esempio il nome della funzione, i punti di uscita e ingresso, i parametri e i valori restituiti.

È possibile ottenere gli eventi di Visual Studio in IntelliTrace scegliendo il **F5** chiave. Per ottenere gli eventi specifici di SharePoint, tuttavia, è necessario raccogliere i dati IntelliTrace nelle soluzioni SharePoint tramite Microsoft Monitoring Agent. Questo strumento raccoglie dati IntelliTrace e crea *iTrace* file per le applicazioni distribuite all'esterno di Visual Studio. Per altre informazioni, vedere [funzionalità IntelliTrace](../debugger/intellitrace-features.md) e [usando l'agente di raccolta autonomo IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md).

## <a name="unit-test"></a>Unit test
È possibile trovare più facilmente gli errori nel codice mediante l'esecuzione di unit test, in cui si creano ed esegue il codice di test all'interno di metodi di test. Questi metodi sono contenute variabili vuote e un'istruzione Assert che è possibile usare per verificare la logica e funzionalità del progetto basato sul modello a oggetti SharePoint. Per altre informazioni, vedere [Eseguire unit test del codice](../test/unit-test-your-code.md).

### <a name="support-for-microsoft-fakes-framework"></a>Supporto per framework Microsoft Fakes
I progetti SharePoint supportano Microsoft Fakes, vale a dire un framework di isolamento in cui è possibile creare shim e test stub basati su delegati in applicazioni basate su .NET Framework. Utilizzando il framework Fakes, è possibile creare, gestire e inserire implementazioni fittizie negli unit test. Tramite questi stub e shim è possibile isolare gli unit test dall'ambiente. È possibile creare stub per testare il codice tramite cui vengono utilizzate interfacce o classi non sealed con metodi che possono essere sottoposti a override. È possibile creare shim per reindirizzare le chiamate hardcoded a classi sealed con metodi statici o non sottoponibili a override in un'implementazione alternativa di shim. È inoltre possibile utilizzare i delegati con tipi di stub e di shim per personalizzare dinamicamente il comportamento di singoli membri stub. Per altre informazioni, vedere [isolare codice sottoposto a Test tramite Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md).

## <a name="related-articles"></a>Articoli correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[IntelliTrace](../debugger/intellitrace.md)|Viene descritto come eseguire più facilmente il debug delle soluzioni di Visual Studio utilizzando IntelliTrace.|
|[Procedura dettagliata: Eseguire il debug di un'applicazione SharePoint tramite IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)|Viene illustrato come utilizzare IntelliTrace per individuare errori di codice in un progetto SharePoint.|
|[Eseguire unit test del codice](../test/unit-test-your-code.md)|Viene descritto come individuare errori logici nel codice tramite unit test.|

## <a name="see-also"></a>Vedere anche

- [Migliorare la qualità del codice](../test/improve-code-quality.md)