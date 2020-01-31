---
title: Come usare CTest per C++
ms.date: 01/23/2020
ms.topic: conceptual
ms.author: corob
manager: jillfra
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 78759a017575916bce3b3fff643cbce8ff303fd6
ms.sourcegitcommit: 8cbced0fb46959a3a2494852df1e41db1177a26c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2020
ms.locfileid: "76826523"
---
# <a name="how-to-use-ctest-for-c-in-visual-studio-2017-and-later"></a>Come usare CTest per C++ in Visual Studio 2017 e versioni successive

CMake, che include CTest, è integrato nell'IDE di Visual Studio per impostazione predefinita come componente del carico di lavoro **Sviluppo di applicazioni desktop con C++** . Se è necessario installare Visual Studio nel computer in uso, aprire il programma di installazione di Visual Studio, fare clic sul pulsante **Sviluppo di applicazioni desktop con C++** e quindi fare clic su **Modifica**. Nell'elenco dei componenti del carico di lavoro selezionare **Strumenti CMake C++ per Windows**.

## <a name="to-write-tests"></a>Per scrivere i test

Il supporto di CMake in Visual Studio non riguarda il sistema di progetti di Visual Studio. Di conseguenza, i test di CTest vengono scritti e configurati come in qualsiasi ambiente CMake. Usare il comando `enable_testing()` per abilitare i test e il `add_test()` o `gtest_discover_tests()` comando per aggiungere un nuovo test. Per altre informazioni su CTest, vedere la [documentazione di CMake](https://gitlab.kitware.com/cmake/community/wikis/doc/ctest/Testing-With-CTest). 

Per altre informazioni sull'uso di CMake in Visual Studio, vedere [Progetti CMake in Visual Studio](/cpp/build/cmake-projects-in-visual-studio).

## <a name="to-run-tests"></a>Per eseguire i test

CTest è completamente integrato con **Esplora test** e supporta anche i framework di testing unità Google e Boost. Questi framework sono inclusi per impostazione predefinita come componenti del carico di lavoro **Sviluppo di applicazioni desktop con C+++** . Tuttavia, se si aggiorna un progetto da una versione precedente di Visual Studio, potrebbe essere necessario installare questi framework usando il programma di installazione di Visual Studio.

La figura seguente mostra i risultati di un'esecuzione di CTest con il framework Google Test:

![CTest con il framework Google Test in Visual Studio](media/ctest-test-explorer.png)

Se si usa CTest ma non gli adattatori Google o Boost, i risultati vengono visualizzati a livello di CTest anziché a livello del singolo metodo di test. È possibile eseguire il debug ed eseguire istruzione per istruzione eseguibili solo CTest, ma non sono supportate analisi dello stack per singoli test.

## <a name="see-also"></a>Vedere anche

- [Scrivere unit test per C/C++](writing-unit-tests-for-c-cpp.md)
