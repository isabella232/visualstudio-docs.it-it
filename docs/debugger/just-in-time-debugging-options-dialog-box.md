---
title: JIT, Debug, finestra di dialogo Opzioni | Microsoft Docs
description: Il debug JIT consente di eseguire il debug di programmi avviati all'esterno Visual Studio. Informazioni su come abilitare il debug JIT per vari tipi di programma.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Debugger.JIT
- vs.debug.options.JIT
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Just-In-Time debugging, setting options
- Options dialog box, debugging
ms.assetid: 7f11b2e3-3fb5-449d-b07c-6ecf1d6a487d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 9179b67d5a7418cfc16900b28f51e3b0984135aa
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122043895"
---
# <a name="just-in-time-debugging-options-dialog-box"></a>JIT, Debug, Finestra di dialogo Opzioni
Per accedere alla pagina **JIT** scegliere **Opzioni** dal menu **Strumenti**. Nella finestra di dialogo **Opzioni** espandere il nodo **Debug** e selezionare **JIT**. Questa pagina consente di abilitare il debug JIT per codice gestito, codice nativo e script. Per altre informazioni, vedere [Debug JIT](../debugger/just-in-time-debugging-in-visual-studio.md).

 È possibile abilitare il debug JIT per questi tipi di programma:

- Gestita

- Nativo

- Script

  Il debug JIT è una tecnica per il debug di un programma avviato al di fuori di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. È possibile eseguire un programma creato in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] al di fuori dell'ambiente di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Se il debug JIT è abilitato e si verifica un arresto anomalo, viene visualizzata una finestra di dialogo in cui viene chiesto se si desidera eseguire il debug.

## <a name="associated-warnings"></a>Avvisi associati
 Quando si accede a questa pagina della finestra di dialogo **Opzioni**, è possibile che venga visualizzato il seguente messaggio di avviso:

 **Un altro debugger si è registrato come debugger JUST-In-Time. Per eseguire il ripristino, abilitare il debug JIT o eseguire Visual Studio ripristino.**

 Questo messaggio viene visualizzato se come debugger JIT è impostato un altro debugger, ad esempio una versione precedente del debugger di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

 È anche possibile che venga visualizzato il messaggio seguente:

 **Rilevati errori di registrazione del debug JIT. Per eseguire il ripristino, abilitare il debug JIT o eseguire Visual Studio ripristino.**

 In entrambi i casi, finché il problema non viene risolto, per l'esecuzione del debug JIT con [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] sarà necessario disporre dei privilegi di amministratore. Se si tenta di abilitare la modalità JIT in queste condizioni senza disporre di questi privilegi, viene visualizzato il seguente messaggio di errore:

 **Accesso negato. Fare in modo che un amministratore abiliti il debug JIT o ripristina l'installazione di Visual Studio.**

## <a name="see-also"></a>Vedi anche
- [Debug, finestra di dialogo Opzioni](../debugger/debugging-options-dialog-box.md)
- [Procedura: Specificare le impostazioni del debugger Impostazioni](../debugger/how-to-specify-debugger-settings.md)