---
title: Come usare Boost.Test per C++ in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/07/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e0710a8-8e8a-4f6e-8415-5ab3eb830079
caps.latest.revision: "14"
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: af55f9f124b2ec609c4f0a590e7c2fab738624d4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-boosttest-for-c-in-visual-studio"></a>Come usare Boost.Test per C++ in Visual Studio
In **Visual Studio 2017 versione 15.5** e versioni successive Boost.Test è integrato nell'IDE di Visual Studio come componente del carico di lavoro **Sviluppo di applicazioni desktop con C++**. Per installarlo nel computer, aprire il programma di installazione di Visual Studio e trovare **Boost.Test Adapter** (Adattatore Boost.Test Adapter) nell'elenco dei componenti del carico di lavoro:

![Installare Boost Test](media/cpp-boost-component.png "Installare Boost.Test per C++")

## <a name="install-boost"></a>Installare Boost

 Per usare Boost.Test è necessario installare [Boost](http://www.boost.org/). Se Boost non è stato installato, è consigliabile usare il sistema di gestione pacchetti Vcpkg. 

1. Seguire le istruzioni in [vcpkg: gestione pacchetti per C++ per Windows](/cpp/vcpkg) per installare vcpkg, se non è già stato installato.
2. Eseguire `vcpkg install boost` per installare le librerie di Boost.
3. Eseguire il comando `vcpkg integrate install` per configurare Visual Studio con la libreria e includere i percorsi delle intestazioni di Boost e dei file binari. 

## <a name="create-a-project-for-your-tests"></a>Creare un progetto per i test
In Visual Studio 2017 versione 15.5 non sono disponibili progetti di test preconfigurati o modelli di elementi per Boost.Test. Pertanto, è necessario creare un progetto di applicazione console per contenere i test. L'inserimento dei modelli di test per Boost.Test è previsto per le versioni future di Visual Studio. 

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo della soluzione e scegliere **Aggiungi | Nuovo progetto**. 
2. Nel riquadro sinistro scegliere **Desktop di Windows** e quindi scegliere **Applicazione console di Windows** nel riquadro centrale. 
3. Specificare un nome per il progetto e fare clic su **OK**. 

## <a name="add-include-directives"></a>Aggiungere direttive include
Nel file con estensione cpp del test aggiungere le direttive `#include` necessarie per rendere visibili al codice di test i tipi e le funzioni del programma. Il programma si trova in genere al livello superiore della gerarchia di cartelle. Se si digita `#include "../"`, viene visualizzata una finestra di IntelliSense ed è possibile selezionare il percorso completo del file di intestazione.

![Aggiungere direttive #include](media/cpp-gtest-includes.png "Aggiungere direttive include al file con estensione cpp del test")

È necessario includere almeno la [variante di intestazione singola di Boost.Test](http://www.boost.org/doc/libs/1_48_0/libs/test/doc/html/utf/user-guide/usage-variants/single-header-variant.html) con `#include <path>/unit_test.hpp` e definire `BOOST_TEST_MODULE`. L'esempio seguente è sufficiente per rendere individuabile il test in **Esplora test**:

```cpp
#include "stdafx.h"
#define BOOST_TEST_MODULE MyTest
#include <boost/test/included/unit_test.hpp>
#include "../MyProgram/MyClass.h" // project being tested
#include <string>

BOOST_AUTO_TEST_CASE(my_boost_test)
{
    std::string name = "Bill";
    MyClass mc(name);
    Assert::AreEqual();
    BOOST_CHECK(name == mc.GetName());
}
```

## <a name="write-and-run-tests"></a>Scrivere ed eseguire i test
È ora possibile scrivere ed eseguire i Boost Test. Per informazioni sulle macro dei test, vedere la [documentazione della libreria Boost Test](http://www.boost.org/doc/libs/1_38_0/libs/test/doc/html/index.html). Per informazioni sull'individuazione, l'esecuzione e il raggruppamento dei test usando **Esplora test**, vedere [Eseguire unit test con Esplora test](run-unit-tests-with-test-explorer.md).

## <a name="see-also"></a>Vedere anche
[Scrittura di unit test per C/C++](writing-unit-tests-for-c-cpp.md)


  







