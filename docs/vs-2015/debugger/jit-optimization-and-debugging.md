---
title: Ottimizzazione e debug JIT | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690542"
---
# <a name="jit-optimization-and-debugging"></a>Debug e ottimizzazione JIT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si esegue il debug di un'applicazione gestita, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] in viene eliminata l'ottimizzazione del codice JIT (just-in-Time) per impostazione predefinita. Viene pertanto eseguito il debug di codice non ottimizzato. L'esecuzione di codice non ottimizzato è più lenta, ma il debug è più completo. Il debug di codice ottimizzato è più complesso ed è consigliabile eseguirlo solo se un problema si verifica nel codice ottimizzato ma non può essere riprodotto nella versione non ottimizzata.  
  
 L'ottimizzazione JIT è controllata in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dall'opzione **Disattiva l'ottimizzazione JIT al caricamento del modulo** . Questa opzione è reperibile nella pagina **generale** del nodo **debug** della finestra di dialogo **Opzioni** .  
  
 Se si deseleziona l'opzione non **visualizzare l'ottimizzazione JIT al caricamento del modulo** , è possibile eseguire il debug del codice JIT ottimizzato, ma la possibilità di eseguire il debug può essere limitata perché il codice ottimizzato non corrisponde al codice sorgente. Di conseguenza, le finestre del debugger, ad esempio **variabili locali** e **auto** , potrebbero non visualizzare tutte le informazioni che verrebbero eseguite durante il debug di codice non ottimizzato.  
  
 Un'altra differenza importante riguarda il debug con Just My Code. Se si esegue il debug con Just My Code, il codice ottimizzato è ritenuto dal debugger codice non utente, che non deve essere visualizzato durante il debug. Se viene eseguito il debug di codice ottimizzato JIT, pertanto, è utile disattivare Just My Code. Per altre informazioni, vedere  [limitare l'esecuzione di un Just My Code](../debugger/just-my-code.md#BKMK_Enable_or_disable_Just_My_Code).  
  
 Tenere presente che l'opzione **di eliminazione dell'ottimizzazione JIT al caricamento del modulo** evita l'ottimizzazione del codice quando vengono caricati i moduli. Se ci si connette a un processo già in esecuzione, è possibile che contenga codice già caricato, compilato tramite JIT e ottimizzato. L'opzione **Elimina l'ottimizzazione JIT al caricamento del modulo** non ha alcun effetto su tale codice, anche se influirà sui moduli caricati dopo la connessione. Inoltre, l'opzione **Disattiva l'ottimizzazione JIT al caricamento del modulo** non influisce sui moduli, ad esempio WinForms.dll, creati con Ngen.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug del codice gestito](../debugger/debugging-managed-code.md)   
 [Esplorazione del codice con il debugger](../debugger/navigating-through-code-with-the-debugger.md)   
 [Connetti a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Processo di esecuzione gestita](https://msdn.microsoft.com/library/476b03dc-2b12-49a7-b067-41caeaa2f533)
