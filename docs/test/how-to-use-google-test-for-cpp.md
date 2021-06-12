---
title: Come usare Google Test per C++
description: Usare Google Test per creare unit test in Visual Studio.
ms.date: 05/06/2017
ms.topic: how-to
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: a338b6f62aee6ec342ef6a16abec71cb6a833bc0
ms.sourcegitcommit: 4b2b6068846425f6964c1fd867370863fc4993ce
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2021
ms.locfileid: "112042964"
---
# <a name="how-to-use-google-test-for-c-in-visual-studio"></a>Come usare Google Test per C++ in Visual Studio

In Visual Studio 2017 e nelle versioni successive Google Test è integrato nell'IDE di Visual Studio come componente predefinito del carico di lavoro **Sviluppo di applicazioni desktop con C++**. Per verificare che sia installato nel computer, aprire il programma di installazione di Visual Studio e trovare Google Test nell'elenco dei componenti del carico di lavoro:

![Installare Google Test](media/cpp-google-component.png)

::: moniker range=">=vs-2019"

## <a name="add-a-google-test-project-in-visual-studio-2019"></a>Aggiungere un progetto Google Test in Visual Studio 2019

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo della soluzione e scegliere **Aggiungi** > **nuovo progetto**.
2. Impostare **Linguaggio** su **C++** e digitare **test** nella casella di ricerca. Nell'elenco risultati scegliere **Google Test Project** (Progetto Google Test).
3. Specificare un nome per il progetto di test e fare clic su **OK**.

![Nuovo progetto Google Test](media/vs-2019/cpp-gtest-new-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

## <a name="add-a-google-test-project-in-visual-studio-2017"></a>Aggiungere un progetto Google Test in Visual Studio 2017

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo della soluzione e scegliere **Aggiungi** > **nuovo progetto**.
2. Nel riquadro sinistro scegliere test **Visual C++** e quindi scegliere Google Test >  **progetto** nel riquadro centrale.
3. Specificare un nome per il progetto di test e fare clic su **OK**.

![Nuovo progetto Google Test](media/cpp-gtest-new-project.png)

::: moniker-end

## <a name="configure-the-test-project"></a>Configurare il progetto di test

Nella finestra di dialogo **Configurazione progetto di test** visualizzata è possibile scegliere il progetto che si vuole testare. Quando si sceglie un progetto, Visual Studio aggiunge un riferimento al progetto selezionato. Se non si sceglie alcun progetto, è necessario aggiungere manualmente i riferimenti al progetto o ai progetti che si vuole testare. Per la scelta di un collegamento statico o dinamico ai file binari di Google Test, tenere presente le stesse considerazioni che si applicano a qualsiasi programma C++. Per altre informazioni, vedere [DLL in Visual C++](/cpp/build/dlls-in-visual-cpp).

![Configurare il progetto Google Test](media/cpp-gtest-config.png)

## <a name="set-additional-options"></a>Impostare opzioni aggiuntive

Scegliere Opzioni strumenti dal menu  >    >  **principale Test Adapter for Google Test** per impostare opzioni aggiuntive. Per altre informazioni su queste impostazioni, vedere la documentazione di Google Test.

![Impostazioni del progetto Google Test](media/cpp-gtest-settings.png)

## <a name="add-include-directives"></a>Aggiungere direttive include

Nel file *con estensione cpp di* test aggiungere le direttive necessarie per rendere visibili al codice di test i tipi e le funzioni del `#include` programma. Il programma si trova in genere al livello superiore della gerarchia di cartelle. Se si digita `#include "../"`, viene visualizzata una finestra di IntelliSense ed è possibile selezionare il percorso completo del file di intestazione.

![Aggiungere direttive #include](media/cpp-gtest-includes.png)

## <a name="write-and-run-tests"></a>Scrivere ed eseguire i test

È ora possibile scrivere ed eseguire i Google Test. Per informazioni sulle macro dei test, vedere [Google Test Primer](https://github.com/google/googletest/blob/master/docs/primer.md) (Introduzione a Google Test). Per informazioni sull'individuazione, l'esecuzione e il raggruppamento dei test usando **Esplora test**, vedere [Eseguire unit test con Esplora test](run-unit-tests-with-test-explorer.md).

## <a name="see-also"></a>Vedi anche

[Scrivere unit test per C/C++](writing-unit-tests-for-c-cpp.md)
