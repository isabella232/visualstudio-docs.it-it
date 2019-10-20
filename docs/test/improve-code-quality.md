---
title: Strumenti di test
ms.date: 03/16/2018
ms.topic: conceptual
helpviewer_keywords:
- testing tools [Visual Studio]
- unit tests [Visual Studio]
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: b68793e512cdb367375cc9f27d61ae5a85e4f078
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653274"
---
# <a name="testing-tools-in-visual-studio"></a>Strumenti di test di Visual Studio

Gli strumenti di test di Visual Studio consentono allo sviluppatore e al team di creare e gestire standard di eccellenza del codice elevati.

> [!NOTE]
> Il testing unità è disponibile in tutte le edizioni di Visual Studio. Altri strumenti di test, come ad esempio Live Unit Testing, IntelliTest e il test codificato dell'interfaccia utente, sono disponibili solo in Visual Studio Enterprise Edition. Per altre informazioni sulle edizioni, vedere [Confronta gli IDE di Visual Studio](https://visualstudio.microsoft.com/vs/compare/).

## <a name="test-explorer"></a>Esplora test

La finestra **Esplora test** consente agli sviluppatori di creare, gestire ed eseguire unit test. È possibile utilizzare il framework per unit test di Microsoft o uno tra i diversi framework di terze parti o open source.

::: moniker range="vs-2017"
![Esplora test di Visual Studio](media/devtest-testexplorer.png)
::: moniker-end

::: moniker range="vs-2019"
![Esplora test di Visual Studio 16.2](media/vs-2019/test-explorer-16-2.PNG)
::: moniker-end

* [Introduzione agli unit test](unit-test-your-code.md)
* [Eseguire unit test con Esplora test](run-unit-tests-with-test-explorer.md)
* [Domande frequenti su Esplora test](test-explorer-faq.md)
* [Installare framework di unit test di terze parti](install-third-party-unit-test-frameworks.md)

Visual Studio è anche estendibile e consente l'uso di adattatori di unit test di terze parti come NUnit e xUnit.net. La funzionalità di clonazione del codice implica inoltre la produzione di software di qualità elevata, poiché consente di identificare i blocchi di codice semanticamente simile che possono essere candidati per le normali operazioni di refactoring o correzione di bug.

![Integrazione con test di terze parti](media/devtest-thirdparty.png)

## <a name="live-unit-testing"></a>Live Unit Testing

[Live Unit Testing](../test/live-unit-testing.md) consente di eseguire automaticamente unit test in background e di visualizzare graficamente i risultati di code coverage e test nell'editor del codice di Visual Studio.

## <a name="intellitest"></a>IntelliTest

IntelliTest genera automaticamente unit test e dati di test per il codice gestito. IntelliTest migliora il code coverage e riduce significativamente l'impegno necessario per creare e gestire unit test per codice nuovo o esistente.

![IntelliTest in azione](media/devtest-intellitest.png)

* [Generare unit test per il codice con IntelliTest](generate-unit-tests-for-your-code-with-intellitest.md)
* [Post di blog su IntelliTest](https://devblogs.microsoft.com/devops/intellitest-one-test-to-rule-them-all/)
* [Manuale di riferimento per IntelliTest](intellitest-manual/index.md)

## <a name="code-coverage"></a>Code coverage

[Code coverage](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md) determina la percentuale di codice del progetto che viene effettivamente testata dai test codificati come ad esempio gli unit test. Per una protezione efficace dai bug, i test devono analizzare o "coprire" gran parte del codice.

L'analisi di code coverage può essere applicata sia al codice gestito che a quello non gestito (nativo).

Il code coverage è un'opzione per l'esecuzione dei metodi di test utilizzando Esplora test. Nella tabella dei risultati viene illustrata la percentuale di codice che è stata eseguita per ogni assembly, classe e metodo. Inoltre, nell'editor standard viene visualizzato il codice testato.

* [Usare la funzionalità code coverage per determinare la quantità di codice testato](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [Lab su unit test, code coverage e analisi dei cloni di codice con Visual Studio](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Unit%20Testing,%20Code%20Coverage%20and%20Code%20Clone%20Analysis%20with%20Visual%20Studio%202015.docx)
* [Personalizzare l'analisi code coverage](customizing-code-coverage-analysis.md)

## <a name="microsoft-fakes"></a>Microsoft Fakes

[Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md) consente di isolare il codice che si sta testando sostituendo altre parti dell'applicazione con stub o shim.

## <a name="user-interface-testing-with-coded-ui-and-selenium"></a>Test dell'interfaccia utente con interfaccia utente codificata e Selenium

I test codificati dell'interfaccia utente consentono di creare test completamente automatici per convalidare le funzionalità e il comportamento dell'interfaccia utente dell'applicazione. Sono in grado di automatizzare il testing dell'interfaccia utente in diverse tecnologie, tra cui le app UWP basate su XAML, le app browser e le app di SharePoint.

Sia che si scelgano i test codificati dell'interfaccia utente più evoluti, sia che si usino test generici basati su browser con Selenium, Visual Studio offre tutti gli strumenti necessari.

![Test dell'interfaccia utente con interfaccia utente codificata](media/devtest-codeduitest.png)

* [Usare l'automazione dell'interfaccia utente per testare il codice](use-ui-automation-to-test-your-code.md)
* [Creazione, modifica e gestione di un test codificato dell'interfaccia utente](walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
* [Testare app UWP con test codificati dell'interfaccia utente](test-uwp-app-with-coded-ui-test.md)
* [Lab sull'esecuzione di test codificati dell'interfaccia utente con Visual Studio Enterprise](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Introduction%20to%20Coded%20UI%20Tests%20with%20Visual%20Studio%20Enterprise%202015.docx)

## <a name="load-testing"></a>Test di carico

I [test di carico](../test/quickstart-create-a-load-test-project.md) simulano il carico su un'applicazione server tramite l'esecuzione di unit test e test delle prestazioni Web.

## <a name="related-scenarios"></a>Scenari correlati

* [Test manuali ed esplorativi (Azure Test Plans)](/azure/devops/test/index?view=vsts)
* [Test di carico (Azure Test Plans)](/azure/devops/test/load-test/index?view=vsts)
* [Test continuati (Azure Test Plans)](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts)
* [Strumenti di analisi del codice](../code-quality/code-analysis-for-managed-code-overview.md)
