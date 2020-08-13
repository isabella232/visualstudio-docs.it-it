---
title: Strumenti di test di Visual Studio per Mac
ms.date: 08/03/2020
ms.topic: conceptual
helpviewer_keywords:
- testing tools [Visual Studio for Mac]
- unit tests [Visual Studio for Mac]
ms.author: jomatthi
author: jmatthiesen
ms.openlocfilehash: acf34677e8d9b477512763be3c43bb9df0c53c46
ms.sourcegitcommit: 935e1388281df0f04147802606b5cb7f513d45ed
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2020
ms.locfileid: "88200984"
---
# <a name="testing-tools-in-visual-studio-for-mac"></a>Strumenti di test in Visual Studio per Mac

Visual Studio per Mac strumenti di test consentono all'utente e al team di sviluppare e sostenere elevati standard di eccellenza del codice. Gli unit test possono essere scritti ed eseguiti con Microsoft unit test Framework (MSTest), xUnit o NUnit.

## <a name="creating-tests"></a>Creazione di test
Per iniziare a eseguire il test, è possibile creare un nuovo progetto di test nella soluzione facendo clic con il pulsante destro del mouse sulla soluzione e scegliendo il menu **aggiungi > nuovo progetto** . Quindi scegliere una delle categorie di test nella parte sinistra della finestra di dialogo (ad esempio, la categoria **Web e Console > test** ). Selezionare il tipo di progetto di test che si desidera creare, quindi fare clic su Avanti. Seguire le istruzioni riportate nelle finestre di dialogo visualizzate, quindi verrà aggiunto un nuovo progetto di test alla soluzione.

![Finestra di dialogo nuovo progetto con > di test Web e console selezionato, che mostra i progetti xUnit, MSTest e NUnit](media/create-new-test-project.PNG)

> [!NOTE]
> Per ulteriori informazioni sull'unit test delle applicazioni .NET Core e sulla selezione di unit test Framework, vedere la pagina relativa ai [testing unità in .NET Core e .NET standard](https://docs.microsoft.com/dotnet/core/testing/?pivots=xunit) documentazione.

## <a name="running-tests"></a>Esecuzione di test
La finestra **unit test** viene usata per eseguire unit test e viene aperta usando il menu **Visualizza > rilievi > unit test** . Gli unit test nella soluzione vengono individuati automaticamente e visualizzati in questa finestra, in cui è possibile eseguire tutti i test o un set di test selezionati.

![Finestra di test che mostra un elenco di unit test e una barra degli strumenti per l'esecuzione o l'arresto dei test.](media/test-window.PNG)

Quando si modifica una classe C# che contiene unit test, è possibile eseguire i test facendo clic con il pulsante destro del mouse nella classe di test o un metodo di test e scegliendo il menu **Esegui test** o **debug test (s)** . Se si sceglie la voce di menu **Esegui test** , i test vengono eseguiti nella finestra di test, scegliendo il menu **debug test (s)** e si collegherà il debugger in modo da poter risolvere i problemi del codice.

![Menu di scelta rapida dell'editor con le opzioni di esecuzione e debug dei test](media/run-tests-context-menu.PNG)

Quando i test sono in esecuzione, viene visualizzata una finestra di **risultati test** in cui è possibile esaminare i test riusciti o non riusciti e l'output dell'esecuzione dei test.

![Finestra Risultati test che mostra un test non superato e un conteggio di 21 test superati e 1 test non superato.](media/test-results-window.PNG)

## <a name="see-also"></a>Vedere anche

- [Testing unità in .NET Core e .NET Standard](/dotnet/core/testing)
- [Introduzione a unit test (Visual Studio in Windows)](/visualstudio/test/getting-started-with-unit-testing)
- [Nozioni fondamentali sugli unit test (Visual Studio in Windows)](/visualstudio/test/unit-test-basics)
