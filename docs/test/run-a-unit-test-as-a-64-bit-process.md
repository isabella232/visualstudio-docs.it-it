---
title: Eseguire uno unit test come processo a 64 bit
ms.date: 03/10/2020
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests, running
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: d6c6839f8c4702d88d1022116231c6f22b5dbf21
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "79093908"
---
# <a name="run-a-unit-test-as-a-64-bit-process"></a>Eseguire uno unit test come processo a 64 bit

Se si dispone di un computer a 64 bit, è possibile eseguire unit test e acquisire informazioni sul code coverage come processo a 64 bit.

## <a name="to-run-a-unit-test-as-a-64-bit-process"></a>Per eseguire uno unit test come processo a 64 bit

1. Se il codice o i test sono stati compilati come a 32 bit/x86, ma ora si desidera eseguirli come processo a 64 bit, ricompilarli come **Qualsiasi CPU**.

   ::: moniker range="vs-2017"
   In alternativa, in Visual Studio 2017 è anche possibile compilare il progetto come **a 64 bit.**
   ::: moniker-end

    > [!TIP]
    > Per la massima flessibilità, compilare i progetti di test con la configurazione **Qualsiasi CPU**. È quindi possibile effettuare l'esecuzione sia su agenti a 32 bit che a 64 bit. Non vi è alcun vantaggio nel compilare i progetti di test con la configurazione a **64 bit**.

2. Impostare gli unit test per l'esecuzione come processo a 64 bit.

   ::: moniker range=">=vs-2019"
   Scegliere **Test**dal menu di Visual Studio , quindi **Architettura del processore per i progetti AnyCPU**. Scegliere **x64** per eseguire i test come processo a 64 bit.
   ::: moniker-end
   ::: moniker range="vs-2017"
   Dal menu di Visual Studio scegliere **Test**, quindi **Impostazioni test**, quindi Architettura **del processore**. Scegliere **x64** per eseguire i test come processo a 64 bit.
   ::: moniker-end

   \- - oppure -

   Specificare `<TargetPlatform>x64</TargetPlatform>` in un file con estensione *runsettings*. Un vantaggio di questo metodo consiste nel specificare i gruppi di impostazioni in file diversi e passare rapidamente da impostazioni diverse. È inoltre possibile copiare le impostazioni tra soluzioni. Per altre informazioni, vedere [Configurare unit test usando un file con estensione runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

## <a name="see-also"></a>Vedere anche

- [Eseguire unit test con Esplora test](../test/run-unit-tests-with-test-explorer.md)
- [Eseguire unit test del codiceUnit test your code](../test/unit-test-your-code.md)
