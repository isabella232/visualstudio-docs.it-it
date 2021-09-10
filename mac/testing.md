---
title: Visual Studio per Mac strumenti di test
description: Creazione ed esecuzione di test usando Visual Studio per Mac.
ms.date: 11/09/2020
ms.topic: conceptual
helpviewer_keywords:
- testing tools [Visual Studio for Mac]
- unit tests [Visual Studio for Mac]
ms.author: jomatthi
author: jmatthiesen
ms.openlocfilehash: 3956c3158fd4ec1ad32b76882ac3f9d4cf1ea9bf
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123964649"
---
# <a name="testing-tools-in-visual-studio-for-mac"></a>Strumenti di test in Visual Studio per Mac

Visual Studio per Mac strumenti di test possono aiutare l'utente e il team a sviluppare e sostenere standard elevati di eccellenza del codice. Gli unit test possono essere scritti ed eseguiti usando Microsoft unit test Framework (MSTest), xUnit o NUnit.

## <a name="creating-tests"></a>Creazione di test
Per iniziare a testare, è possibile creare un nuovo progetto di test nella soluzione facendo clic con il pulsante destro del mouse sulla soluzione e scegliendo il menu Aggiungi > **Nuovo Project...** . Scegliere quindi una delle categorie Test sul lato sinistro della finestra di dialogo, ad esempio la categoria Test web e console > **test.** Selezionare il tipo di progetto di test da creare e fare clic su Avanti. Seguire le istruzioni nelle finestre di dialogo visualizzate e quindi verrà aggiunto un nuovo progetto di test alla soluzione.

![Finestra di dialogo Nuovo progetto con la sezione Test > Web e console selezionata, che mostra i progetti xUnit, MSTest e NUnit](media/create-new-test-project.PNG)

> [!NOTE]
> Per altre informazioni sugli unit test delle applicazioni .NET Core e sulla selezione di framework unit test, vedere la documentazione unit [test in .NET Core e .NET Standard.](/dotnet/core/testing/?pivots=xunit)

## <a name="running-tests"></a>Esecuzione di test
La **finestra Unit test** viene usata per eseguire unit test e viene aperta usando il menu Visualizza > **test.** Gli unit test nella soluzione vengono individuati e visualizzati automaticamente in questa finestra, in cui è possibile eseguire tutti i test o un set di test selezionati.

![Finestra test che mostra un elenco di unit test e una barra degli strumenti per l'esecuzione o l'arresto dei test.](media/test-window.PNG)

Quando si modifica una classe C# che contiene unit test, è possibile eseguire i  test facendo clic con il pulsante destro del mouse sulla classe di test o su un metodo di test e scegliendo il **menu** Esegui test o Esegui test di debug. Se si sceglie la voce di **menu** Esegui test, i test verranno eseguiti nella finestra di test, scegliendo il **menu** Debug test e collegando il debugger in modo da risolvere i problemi relativi al codice.

![Menu di scelta rapida dell'editor con le opzioni Esegui ed esegui debug test](media/run-tests-context-menu.PNG)

Durante l'esecuzione dei test viene **visualizzata Risultati test** finestra di dialogo in modo da poter esaminare i test riusciti o non superati e l'output dell'esecuzione di tali test.

![Finestra risultati test che mostra un test non superato e un conteggio di 21 test superati e 1 test non superato.](media/test-results-window.PNG)

## <a name="see-also"></a>Vedi anche

- [Unit test in .NET Core e .NET Standard](/dotnet/core/testing)
- [Informazioni di base con unit test (Visual Studio in Windows)](/visualstudio/test/getting-started-with-unit-testing)
- [Nozioni di base sugli unit test (Visual Studio su Windows)](/visualstudio/test/unit-test-basics)