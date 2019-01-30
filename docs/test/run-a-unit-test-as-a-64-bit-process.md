---
title: Eseguire uno unit test come processo a 64 bit
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests, running
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 1e4a5919a4c030380e82794c9dd1dbe4ca35cc11
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55024279"
---
# <a name="run-a-unit-test-as-a-64-bit-process"></a>Eseguire uno unit test come processo a 64 bit

Se si dispone di un computer a 64 bit, è possibile eseguire unit test e acquisire informazioni sul code coverage come processo a 64 bit.

## <a name="to-run-a-unit-test-as-a-64-bit-process"></a>Per eseguire uno unit test come processo a 64 bit

1. Se il codice o i test sono stati compilati come processi 32 bit/x86, ma si vuole ora eseguirli come processo a 64 bit, ricompilarli con la configurazione **Qualsiasi CPU** o facoltativamente **64 bit**.

    > [!TIP]
    > Per la massima flessibilità, compilare i progetti di test con la configurazione **Qualsiasi CPU**. È quindi possibile effettuare l'esecuzione sia su agenti a 32 bit che a 64 bit. Non vi è alcun vantaggio nel compilare i progetti di test con la configurazione a **64 bit**.

2. Nel menu di Visual Studio scegliere **Test**, quindi **Impostazioni** e infine **Architettura del processore**. Scegliere **x64** per eseguire i test come processo a 64 bit.

   - oppure -

   Specificare `<TargetPlatform>x64</TargetPlatform>` in un file con estensione *runsettings*. Un vantaggio di questo metodo consiste nel specificare i gruppi di impostazioni in file diversi e passare rapidamente da impostazioni diverse. È inoltre possibile copiare le impostazioni tra soluzioni. Per altre informazioni, vedere [Configurare unit test usando un file con estensione runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

## <a name="see-also"></a>Vedere anche

- [Eseguire unit test con Esplora test](../test/run-unit-tests-with-test-explorer.md)
- [Eseguire unit test del codice](../test/unit-test-your-code.md)
