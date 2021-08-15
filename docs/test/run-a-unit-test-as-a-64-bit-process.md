---
title: Eseguire uno unit test come processo a 64 bit
description: Informazioni su come eseguire unit test e acquisire code coverage informazioni come processo a 64 bit. È necessario disporre di un computer a 64 bit.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: how-to
helpviewer_keywords:
- unit tests, creating
- unit tests, running
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 702e83e487f6d2bbfbb85d8026476ff1c3db9cbfccbbf7f6b431f0ea93b0f1ed
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121315109"
---
# <a name="run-a-unit-test-as-a-64-bit-process"></a>Eseguire uno unit test come processo a 64 bit

Se si dispone di un computer a 64 bit, è possibile eseguire unit test e acquisire informazioni sul code coverage come processo a 64 bit.

## <a name="to-run-a-unit-test-as-a-64-bit-process"></a>Per eseguire uno unit test come processo a 64 bit

1. Se il codice o i test sono stati compilati come a 32 bit/x86, ma ora si vuole eseguirli come processo a 64 bit, ricompilarli come **Qualsiasi CPU.**

   ::: moniker range="vs-2017"
   In alternativa, in Visual Studio 2017 è anche possibile compilare il progetto come **a 64 bit.**
   ::: moniker-end

    > [!TIP]
    > Per la massima flessibilità, compilare i progetti di test con la configurazione **Qualsiasi CPU**. È quindi possibile effettuare l'esecuzione sia su agenti a 32 bit che a 64 bit. La compilazione di progetti di test con la configurazione a **64 bit** non ha alcun vantaggio, a meno che non si chiami codice supportato solo a 64 bit.

2. Impostare gli unit test per l'esecuzione come processo a 64 bit.

   ::: moniker range=">=vs-2019"
   Dal menu Visual Studio scegliere **Test** e quindi Architettura processore **per i progetti AnyCPU.** Scegliere **x64** per eseguire i test come processo a 64 bit.
   ::: moniker-end
   ::: moniker range="vs-2017"
   Dal menu Visual Studio scegliere **Test,** quindi Test Impostazioni **e** infine Architettura **processore.** Scegliere **x64** per eseguire i test come processo a 64 bit.
   ::: moniker-end

   \- - oppure -

   Specificare `<TargetPlatform>x64</TargetPlatform>` in un file con estensione *runsettings*. Un vantaggio di questo metodo consiste nel specificare i gruppi di impostazioni in file diversi e passare rapidamente da impostazioni diverse. È inoltre possibile copiare le impostazioni tra soluzioni. Per altre informazioni, vedere [Configurare unit test usando un file con estensione runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

## <a name="see-also"></a>Vedi anche

- [Eseguire unit test con Esplora test](../test/run-unit-tests-with-test-explorer.md)
- [Eseguire unit test del codice](../test/unit-test-your-code.md)
