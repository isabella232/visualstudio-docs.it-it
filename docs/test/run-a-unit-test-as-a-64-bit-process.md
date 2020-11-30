---
title: Eseguire uno unit test come processo a 64 bit
description: Informazioni su come eseguire unit test e acquisire informazioni code coverage come processo a 64 bit. È necessario disporre di un computer a 64 bit.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: how-to
helpviewer_keywords:
- unit tests, creating
- unit tests, running
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 7d18a97a3cf8f680e7bfe3d679e8e57f7cc716fb
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329068"
---
# <a name="run-a-unit-test-as-a-64-bit-process"></a>Eseguire uno unit test come processo a 64 bit

Se si dispone di un computer a 64 bit, è possibile eseguire unit test e acquisire informazioni sul code coverage come processo a 64 bit.

## <a name="to-run-a-unit-test-as-a-64-bit-process"></a>Per eseguire uno unit test come processo a 64 bit

1. Se il codice o i test sono stati compilati come 32 bit/x86, ma ora si desidera eseguirli come processo a 64 bit, ricompilarli come **qualsiasi CPU**.

   ::: moniker range="vs-2017"
   In alternativa, in Visual Studio 2017, è anche possibile compilare il progetto come **64 bit**.
   ::: moniker-end

    > [!TIP]
    > Per la massima flessibilità, compilare i progetti di test con la configurazione **Qualsiasi CPU**. È quindi possibile effettuare l'esecuzione sia su agenti a 32 bit che a 64 bit. Non vi sono vantaggi nella compilazione di progetti di test con la configurazione a **64 bit** , a meno che non si chiami codice supportato solo su 64 bit.

2. Impostare gli unit test per l'esecuzione come processo a 64 bit.

   ::: moniker range=">=vs-2019"
   Dal menu di Visual Studio scegliere **test**, quindi **architettura del processore per progetti AnyCPU**. Scegliere **x64** per eseguire i test come processo a 64 bit.
   ::: moniker-end
   ::: moniker range="vs-2017"
   Dal menu di Visual Studio scegliere **test**, quindi scegliere **impostazioni test**, quindi **architettura del processore**. Scegliere **x64** per eseguire i test come processo a 64 bit.
   ::: moniker-end

   \- - oppure -

   Specificare `<TargetPlatform>x64</TargetPlatform>` in un file con estensione *runsettings*. Un vantaggio di questo metodo consiste nel specificare i gruppi di impostazioni in file diversi e passare rapidamente da impostazioni diverse. È inoltre possibile copiare le impostazioni tra soluzioni. Per altre informazioni, vedere [Configurare unit test usando un file con estensione runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

## <a name="see-also"></a>Vedi anche

- [Eseguire unit test con Esplora test](../test/run-unit-tests-with-test-explorer.md)
- [Eseguire unit test del codice](../test/unit-test-your-code.md)
