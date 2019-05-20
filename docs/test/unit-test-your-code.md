---
title: Testing unità
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, unit tests
- unit tests, verifying code with
- testing code, automated tests
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 5682d752ba2c1430d8ab708e3dadda754a1ba757
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/09/2019
ms.locfileid: "65461389"
---
# <a name="unit-test-your-code"></a>Eseguire unit test del codice

Gli unit test rappresentano per sviluppatori e tester un modo rapido per verificare la presenza di errori di logica nei metodi delle classi in progetti C#, Visual Basic e C++.

Gli strumenti di unit test includono:

* **Esplora test**: eseguire unit test e visualizzare i risultati in **Esplora test**. È possibile usare qualsiasi framework di unit test, incluso un framework di terze parti, purché provvisto di un adattatore per **Esplora test**.

* **Framework per unit test di Microsoft per il codice gestito**: viene installato con Visual Studio e offre un framework per testare il codice .NET.

* **Framework per unit test di Microsoft per C++**: viene installato come parte del carico di lavoro **Sviluppo di applicazioni desktop con C++**. Offre un framework per testare codice nativo. Anche i framework Google Test, Boost.Test e CTest sono inclusi e sono disponibili adattatori di terze parti per framework di test aggiuntivi. Per altre informazioni, vedere [Scrivere unit test per C/C++](../test/writing-unit-tests-for-c-cpp.md).

* **Strumenti di code coverage**: è possibile determinare la quantità di codice del prodotto sottoposta agli unit test da un singolo comando in Esplora test.

* **Framework di isolamento di Microsoft Fakes**: può creare classi e metodi sostitutivi per il codice di sistema e di produzione che creano le dipendenze nel codice sottoposto a test. L'implementazione di delegati falsi per una funzione consente di controllare il comportamento e l'output dell'oggetto di dipendenza.

È anche possibile creare [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md) che esplorano il codice .NET per generare dati di test e un gruppo di unit test. Per ogni istruzione nel codice viene generato un input di test che eseguirà l'istruzione. Viene eseguita un'analisi del caso per ogni branch condizionale nel codice.

## <a name="key-tasks"></a>Attività chiave

Usare gli articoli seguenti per la comprensione e la creazione di unit test:

|Attività|Argomenti correlati|
|-|-----------------------|
|**Guide introduttive e procedure dettagliate:** informazioni sugli unit test in Visual Studio da esempi di codice.|- [Procedura dettagliata: Creare ed eseguire unit test per codice gestito](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)<br />- [Guida introduttiva: Sviluppo basato su test con Esplora test](../test/quick-start-test-driven-development-with-test-explorer.md)<br />- [Procedura: Aggiungere unit test ad app C++](../test/how-to-use-microsoft-test-framework-for-cpp.md)|
|**Unit test con Esplora test:** informazioni su come Esplora test può agevolare la creazione di unit test più produttivi ed efficienti.|- [Nozioni di base sugli unit test](../test/unit-test-basics.md)<br />- [Creare un progetto di unit test](../test/create-a-unit-test-project.md)<br />- [Eseguire unit test con Esplora test](../test/run-unit-tests-with-test-explorer.md)<br />- [Installare framework di unit test di terze parti](../test/install-third-party-unit-test-frameworks.md)|
|**Unit test di codice C++**|- [Scrivere unit test per C/C++](../test/writing-unit-tests-for-c-cpp.md)|
|**Isolamento degli unit test**|- [Isolare codice sottoposto a test con Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)|
|**Usare code coverage per identificare la percentuale del codice del progetto in fase di test:** informazioni sulla funzionalità code coverage degli strumenti di test di Visual Studio.|- [Usare la funzionalità code coverage per determinare la quantità di codice testato](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)|
|**Eseguire analisi di stress e prestazioni usando test di carico:** informazioni su come creare test di carico per isolare problemi di prestazioni e di stress nell'applicazione.|- [Guida introduttiva: Creare un progetto di test di carico](../test/quickstart-create-a-load-test-project.md)<br />- [Test di carico (Azure Test Plans e TFS)](/azure/devops/test/load-test/index?view=vsts)|
|**Impostare quality gate:** informazioni su come creare quality gate che stabiliscano l'esecuzione dei test prima dell'archiviazione o dell'unione del codice.|- [Criteri di archiviazione (Azure Repos TFVC)](/azure/devops/repos/tfvc/add-check-policies?view=vsts)|
|**Impostare le opzioni di test:** informazioni su come configurare le opzioni di test, ad esempio la posizione in cui archiviare i risultati dei test.|[Configurazione di unit test usando un file con estensione runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|

## <a name="api-reference-documentation"></a>Documentazione di riferimento API

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting> descrive lo spazio dei nomi UnitTesting, che rende disponibili attributi, eccezioni, asserzioni e altre classi che supportano il testing unità.
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web> descrive lo spazio dei nomi UnitTesting.Web, che estende lo spazio dei nomi UnitTesting offrendo supporto per unit test ASP.NET e del servizio Web.

## <a name="see-also"></a>Vedere anche

- [Migliorare la qualità del codice](../test/improve-code-quality.md)
