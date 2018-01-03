---
title: Eseguire uno unit test come processo a 64 bit | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unit tests, creating
- unit tests, running
ms.assetid: d23a9ee7-58e3-4e8b-a38c-b2207ea73fea
caps.latest.revision: "25"
ms.author: douge
manager: douge
ms.workload: multiple
ms.openlocfilehash: 39addca0d673ae5a9423d4195ffc2bfe3358de4e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="run-a-unit-test-as-a-64-bit-process"></a>Eseguire uno unit test come processo a 64 bit
Se si dispone di un computer a 64 bit, è possibile eseguire unit test e acquisire informazioni sul code coverage come processo a 64 bit.  
  
## <a name="running-a-unit-test-as-a-64-bit-process"></a>Esecuzione di uno unit test come processo a 64 bit  
  
#### <a name="to-run-a-unit-test-as-a-64-bit-process"></a>Per eseguire uno unit test come processo a 64 bit  
  
1.  Se il codice o i test sono stati compilati come processi 32 bit/x86, ma si vuole ora eseguirli come processo a 64 bit, ricompilarli con la configurazione **Qualsiasi CPU** o facoltativamente **64 bit**.  
  
    > [!TIP]
    >  Per la massima flessibilità, è consigliabile compilare i progetti di test con la configurazione **Qualsiasi CPU**. È quindi possibile l'esecuzione su entrambi gli agenti a 32 e 64 bit. Non esiste alcun vantaggio nel compilare i progetti di test con la configurazione **64 bit**.  
  
2.  Nel menu di Visual Studio scegliere **Test**, quindi **Impostazioni** e infine **Architettura del processore**. Scegliere **x64** per eseguire i test come processo a 64 bit.  
  
     \- oppure -  
  
     Specificare `<TargetPlatform>x64</TargetPlatform>` in un file con estensione runsettings. Un vantaggio di questo metodo consiste nel specificare i gruppi di impostazioni in file diversi e passare rapidamente da impostazioni diverse. È inoltre possibile copiare le impostazioni tra soluzioni. Per altre informazioni, vedere [Configurare unit test usando un file con estensione runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Eseguire unit test con Esplora test](../test/run-unit-tests-with-test-explorer.md)   
 [Eseguire unit test del codice](../test/unit-test-your-code.md)   
 [Specifica delle impostazioni test di Visual Studio](/devops-test-docs/test/specifying-test-settings-for-visual-studio-tests)
