---
title: Come usare CTest per C++ in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/07/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8b30934-5f38-4a18-8819-263e0733cdbe
caps.latest.revision: "14"
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1b471b90748442369cd9cf917e65fd283c5c52ed
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-ctest-for-c-in-visual-studio"></a>Come usare CTest per C++ in Visual Studio
CMake, che include CTest, è integrato nell'IDE di Visual Studio come componente del carico di lavoro **Sviluppo di applicazioni desktop con C++**. Per installarlo nel computer, aprire il programma di installazione di Visual Studio e trovare [CMake Tools per Visual C++](/cpp/ide/cmake-tools-for-visual-cpp) (Strumenti CMake per Visual C++) nell'elenco dei componenti del carico di lavoro.

Il supporto di CMake in Visual Studio non riguarda il sistema di progetti di Visual Studio. Di conseguenza, i test di CTest vengono scritti e configurati come in qualsiasi ambiente CMake. Per altre informazioni sull'uso di CMake in Visual Studio, vedere [CMake Tools for Visual C++](/cpp/ide/cmake-tools-for-visual-cpp) (Strumenti CMake per Visual C++).

**Visual Studio 2017 versione 15.5** CTest non è attualmente integrato con **Esplora test**. È possibile eseguire i test dal menu principale di CMake o dal menu di scelta rapida di un file **CMakeLists.txt** in **Esplora soluzioni**. I risultati del test vengono indirizzati alla **finestra di output** di Visual Studio.

![Eseguire test CTest](media/cpp-cmake-run-tests.png "Eseguire test CTest")


## <a name="see-also"></a>Vedere anche
[Scrittura di unit test per C/C++](writing-unit-tests-for-c-cpp.md)


  







