---
title: Eseguire uno unit test come processo a 64 bit | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests, running
ms.assetid: d23a9ee7-58e3-4e8b-a38c-b2207ea73fea
caps.latest.revision: 27
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cc3ff63e13dc3723cff9e87ce40e6a57b062179f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60114301"
---
# <a name="run-a-unit-test-as-a-64-bit-process"></a>Eseguire uno unit test come processo a 64 bit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se si dispone di un computer a 64 bit, è possibile eseguire unit test e acquisire informazioni sul code coverage come processo a 64 bit.  
  
## <a name="running-a-unit-test-as-a-64-bit-process"></a>Esecuzione di uno unit test come processo a 64 bit  
  
#### <a name="to-run-a-unit-test-as-a-64-bit-process"></a>Per eseguire uno unit test come processo a 64 bit  
  
1. Se il codice o i test sono stati compilati come processi 32 bit/x86, ma si vuole ora eseguirli come processo a 64 bit, ricompilarli con la configurazione **Qualsiasi CPU** o facoltativamente **64 bit**.  
  
    > [!TIP]
    >  Per la massima flessibilità, è consigliabile compilare i progetti di test con la configurazione **Qualsiasi CPU**. È quindi possibile l'esecuzione su entrambi gli agenti a 32 e 64 bit. Non esiste alcun vantaggio nel compilare i progetti di test con la configurazione **64 bit**.  
  
2. Nel menu di Visual Studio scegliere **Test**, quindi **Impostazioni** e infine **Architettura del processore**. Scegliere **x64** per eseguire i test come processo a 64 bit.  
  
     \- oppure -  
  
     Specificare `<TargetPlatform>x64</TargetPlatform>` in un file con estensione runsettings. Un vantaggio di questo metodo consiste nel specificare i gruppi di impostazioni in file diversi e passare rapidamente da impostazioni diverse. È inoltre possibile copiare le impostazioni tra soluzioni. Per altre informazioni, vedere [Configurare unit test usando un file con estensione runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Eseguire unit test con Esplora test](../test/run-unit-tests-with-test-explorer.md)   
 [Eseguire unit test del codice](../test/unit-test-your-code.md)   
 [Specifica delle impostazioni test di Visual Studio](http://msdn.microsoft.com/library/0c15317e-80c6-4317-aed3-82b8e15e3901)
