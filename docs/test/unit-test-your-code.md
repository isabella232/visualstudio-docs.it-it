---
title: Strumenti di unit test & attività
description: Informazioni sugli strumenti unit test che è possibile usare per offrire a sviluppatori e tester un modo rapido per cercare errori logici nel codice.
ms.custom: SEO-VS-2020
ms.date: 08/10/2021
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, unit tests
- unit tests, verifying code with
- testing code, automated tests
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: bd506fe8c47050e936854c51f6e3c225210bcdff
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122100400"
---
# <a name="unit-test-tools-and-tasks"></a>Strumenti e attività di unit test

Gli unit test rappresentano per sviluppatori e tester un modo rapido per verificare la presenza di errori di logica nei metodi delle classi in progetti C#, Visual Basic e C++.

Gli strumenti di unit test includono:

* **Esplora test** &mdash; Eseguire unit test e visualizzarne i risultati in **Esplora test.** È possibile usare qualsiasi framework di unit test, incluso un framework di terze parti, purché provvisto di un adattatore per **Esplora test**.

* **Framework unit test Microsoft per il codice gestito** &mdash; Microsoft unit test framework per il codice gestito viene installato con Visual Studio e fornisce un framework per il test del codice .NET.

* **Framework di unit test nativo** &mdash; Microsoft Il framework di unit test nativo Microsoft per C++ viene installato come parte del carico di **lavoro Sviluppo di applicazioni desktop con C++.** Offre un framework per testare codice nativo. Anche i framework Google Test, Boost.Test e CTest sono inclusi e sono disponibili adattatori di terze parti per framework di test aggiuntivi. Per altre informazioni, vedere [Scrivere unit test per C/C++](../test/writing-unit-tests-for-c-cpp.md).

* **Strumenti di code coverage** &mdash; È possibile determinare la quantità di codice prodotto che gli unit test eserciteranno da un comando in Esplora test.

* **Microsoft Fakes di isolamento** &mdash; Il framework Microsoft Fakes di isolamento può creare classi e metodi sostitutivi per il codice .NET di produzione e di sistema che creano dipendenze nel codice testato. L'implementazione di delegati falsi per una funzione consente di controllare il comportamento e l'output dell'oggetto di dipendenza.

Per .NET, è anche possibile usare [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md) per esplorare il codice e generare dati di test e un gruppo di unit test. Per ogni istruzione nel codice viene generato un input di test che eseguirà l'istruzione. Viene eseguita un'analisi del caso per ogni ramo condizionale nel codice.

## <a name="key-tasks"></a>Attività chiave

Usare gli articoli seguenti per la comprensione e la creazione di unit test:

|Attività|Argomenti correlati|
|-|-----------------------|
|**Esercitazioni:** Informazioni sugli unit test in Visual Studio esempi di codice.|- [Introduzione a unit test](getting-started-with-unit-testing.md)<br />- [Sviluppo basato su test con Esplora test](../test/quick-start-test-driven-development-with-test-explorer.md)|
|**Unit test con Esplora test:** informazioni su come Esplora test può agevolare la creazione di unit test più produttivi ed efficienti.|- [Nozioni di base su unit test](../test/unit-test-basics.md)<br />- [Creare un unit test progetto](../test/create-a-unit-test-project.md)<br />- [Eseguire unit test con Esplora test](../test/run-unit-tests-with-test-explorer.md)<br />- [Installare framework di unit test di terze parti](../test/install-third-party-unit-test-frameworks.md)|
|**Codice .NET per unit test**|- [Creare ed eseguire unit test per il codice .NET](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)|
|**Unit test di codice C++**|- [Scrivere unit test per C/C++](../test/writing-unit-tests-for-c-cpp.md)<br />- [Procedura: Aggiungere unit test alle app C++](../test/how-to-use-microsoft-test-framework-for-cpp.md)|
|**Usare code coverage per identificare la percentuale del codice del progetto in fase di test:** informazioni sulla funzionalità code coverage degli strumenti di test di Visual Studio.|- [Usare code coverage per determinare la quantità di codice testato](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)|
|**Isolamento degli unit test**|- [Isolare il codice .NET testato con Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)|
|**Eseguire l'analisi di stress e prestazioni usando i test di carico:** Informazioni su come creare test di carico per isolare i problemi di prestazioni e stress nell'applicazione (deprecati).|- [Guida introduttiva: Creare un progetto di test di carico](../test/quickstart-create-a-load-test-project.md)<br />- [Test di carico (Azure Test Plans e TFS)](/azure/devops/test/load-test/index?view=vsts&preserve-view=true)|
|**Impostare i controlli di qualità:** Informazioni su come creare controlli di qualità per imporre che i test vengano eseguiti prima che il codice venga archiviato o unito.|- [Criteri di archiviazione (Azure Repos TFVC)](/azure/devops/repos/tfvc/add-check-policies?view=vsts&preserve-view=true)|
|**Impostare le opzioni di test:** Informazioni su come configurare le opzioni di test, ad esempio dove vengono archiviati i risultati dei test.|[Configurazione di unit test usando un file con estensione runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|

## <a name="api-reference-documentation"></a>Documentazione di riferimento delle API

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting> descrive lo spazio dei nomi UnitTesting, che rende disponibili attributi, eccezioni, asserzioni e altre classi che supportano il testing unità.
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web> descrive lo spazio dei nomi UnitTesting.Web, che estende lo spazio dei nomi UnitTesting offrendo supporto per unit test ASP.NET e del servizio Web.

## <a name="see-also"></a>Vedi anche

- [Migliorare la qualità del codice](../test/improve-code-quality.md)