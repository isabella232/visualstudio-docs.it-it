---
title: JIT debug e ottimizzazione | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], optimized code
- optimized code, debugging
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 56b010a01ccd7e40e696653e13dd7c972c97a9cb
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65690542"
---
# <a name="jit-optimization-and-debugging"></a>Debug e ottimizzazione JIT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si esegue il debug di un'applicazione gestita, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] viene disattivata l'ottimizzazione del codice just-in-time (JIT) per impostazione predefinita. Viene pertanto eseguito il debug di codice non ottimizzato. L'esecuzione di codice non ottimizzato è più lenta, ma il debug è più completo. Il debug di codice ottimizzato è più complesso ed è consigliabile eseguirlo solo se un problema si verifica nel codice ottimizzato ma non può essere riprodotto nella versione non ottimizzata.  
  
 L'ottimizzazione JIT è controllata nella [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] per il **disattivare l'ottimizzazione JIT al caricamento del modulo** opzione. È possibile trovare questa opzione sul **generali** pagina il **debug** nodo nel **opzioni** nella finestra di dialogo.  
  
 Se si deseleziona il **disattivare l'ottimizzazione JIT al caricamento del modulo** opzione, è possibile eseguire il debug del codice JIT ottimizzato, ma la possibilità di eseguire il debug potrebbe risultare limitata poiché il codice ottimizzato non corrisponde al codice sorgente. Di conseguenza, finestre del debugger, ad esempio la **variabili locali** e **Auto** finestra potrebbe non visualizzare quante più informazioni come se si esegue il debug di codice non ottimizzato.  
  
 Un'altra differenza importante riguarda il debug con Just My Code. Se si esegue il debug con Just My Code, il codice ottimizzato è ritenuto dal debugger codice non utente, che non deve essere visualizzato durante il debug. Se viene eseguito il debug di codice ottimizzato JIT, pertanto, è utile disattivare Just My Code. Per altre informazioni, vedere [limitare l'accesso a Just My Code](../debugger/just-my-code.md#BKMK_Enable_or_disable_Just_My_Code).  
  
 Tenere presente che il **disattivare l'ottimizzazione JIT al caricamento del modulo** opzione Disattiva l'ottimizzazione del codice quando vengono caricati i moduli. Se ci si connette a un processo già in esecuzione, è possibile che contenga codice già caricato, compilato tramite JIT e ottimizzato. Il **disattivare l'ottimizzazione JIT al caricamento del modulo** opzione non ha alcun effetto su tale codice, anche se ha effetto sui moduli caricati dopo aver collegato. Inoltre, il **disattivare l'ottimizzazione JIT al caricamento del modulo** opzione non riguarda i moduli, ad esempio WinForms. dll, che vengono creati con NGEN.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di codice gestito](../debugger/debugging-managed-code.md)   
 [Spostarsi nel codice con il Debugger](../debugger/navigating-through-code-with-the-debugger.md)   
 [Connettersi a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Processo di esecuzione gestita](https://msdn.microsoft.com/library/476b03dc-2b12-49a7-b067-41caeaa2f533)
