---
title: Creare stub di metodo di unit test
description: Informazioni su come usare il comando Crea unit test, che consente di configurare facilmente un progetto di test, la classe di test e lo stub del metodo di test al suo interno.
ms.custom: SEO-VS-2020
ms.date: 07/26/2021
ms.topic: how-to
helpviewer_keywords:
- unit testing, create unit tests
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
ms.openlocfilehash: b32cdf6da48b1becc9aed825f6e14127e31ee30b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122135819"
---
# <a name="create-unit-test-method-stubs-from-code"></a>Creare unit test stub di metodo dal codice

Il comando **Crea unit test** crea stub di metodo di unit. Questa funzionalità consente di semplificare la configurazione di un progetto di test, della classe di test e dello stub del metodo di test all'interno di essa.

::: moniker range="vs-2017"
> [!NOTE]
> Il **comando di** menu Crea unit test è disponibile solo per il codice C# destinato a .NET Framework (ma non a .NET Core o .NET Standard).
::: moniker-end
::: moniker range=">=vs-2019"
> [!NOTE]
> Il comando di menu **Crea unit** test è disponibile solo per il codice C#.
::: moniker-end

Il comando di menu **Crea unit test** è estendibile e può essere usato per generare test per MSTest, MSTest V2, NUnit e xUnit.

## <a name="get-started"></a>Introduzione

Per iniziare, selezionare un metodo, un tipo o uno spazio dei nomi nell'editor di codice nel progetto da testare, fare clic con il pulsante destro del mouse e quindi scegliere **Crea unit test**. Verrà visualizzata la finestra di dialogo **Crea unit test**, in cui è possibile configurare la modalità di creazione dei test.

![Uso del comando Crea unit test](media/createunittestcommand.png)

Se le opzioni del framework di test per NUnit o xUnit non sono disponibili, vedere Usare framework unit test [di terze parti.](#use-third-party-unit-test-frameworks)

## <a name="set-unit-test-traits"></a>Impostare tratti di unit test

Se si prevede di eseguire questi test come parte del processo di automazione del test, considerare la possibilità di creare il test in un altro progetto di test (la seconda opzione nella finestra di dialogo precedente) e di impostare i tratti di unit test per lo unit test. In questo modo sarà più facile includere o escludere questi test specifici come parte di una pipeline di distribuzione continua o di integrazione continua. I tratti vengono impostati aggiungendo direttamente i metadati allo unit test, come illustrato di seguito.

![Impostazione di tratti di unit test](media/createunittest.png)

## <a name="use-third-party-unit-test-frameworks"></a>Usare framework di unit test di terze parti

Per generare automaticamente gli unit test per NUnit o xUnit, installare una di queste estensioni del framework di test da Visual Studio Marketplace:

* [NUnit extension for test generators (Estensione NUnit per generatori di test)](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension-18371)
* [xUnit.net extension for test generators (Estensione xUnit.net per generatori di test)](https://marketplace.visualstudio.com/items?itemName=YowkoTsai.xUnitnetTestGenerator)

## <a name="when-should-i-use-this-feature"></a>Quando si deve usare questa funzionalità?

Usare questa funzionalità ogni volta che è necessario creare unit test, ma in particolare quando si testa un codice esistente con poco o nessun code coverage del test e senza documentazione. In altre parole, dove la specifica del codice è limitata o inesistente. Implementa in modo efficace un approccio simile agli [unit test intelligenti](https://devblogs.microsoft.com/devops/introducing-smart-unit-tests/), che caratterizza il comportamento osservato del codice.

Tuttavia, questa funzionalità può essere applicata anche quando uno sviluppatore inizia a scrivere codice e lo usa per il bootstrap degli unit test. All'interno del flusso di scrittura del codice, lo sviluppatore potrebbe voler creare rapidamente uno stub del metodo di unit test, con una classe di test e un progetto di test appropriati, per una parte specifica di codice.

## <a name="see-also"></a>Vedi anche

- [Creare stub di metodo di unit test con il comando Crea unit test](https://devblogs.microsoft.com/devops/creating-unit-test-method-stubs-with-create-unit-tests/)
- [Post di blog sul testing unità](https://devblogs.microsoft.com/devops/?s=unit+testing)
