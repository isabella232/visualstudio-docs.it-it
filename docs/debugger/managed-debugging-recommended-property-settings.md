---
title: Debugger proprietà le impostazioni consigliate per C#, Visual Basic | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], managed
- debugging managed code, recommended property settings
ms.assetid: 3d14a8d4-2925-44d0-be41-ec546d411db9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d15e41f07f4866b12937455b79f2f2f7a7ba4052
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54971140"
---
# <a name="managed-debugging-recommended-property-settings"></a>Debug gestito: Impostazioni consigliate delle proprietà
Determinate proprietà devono essere impostate nello stesso modo per tutti gli scenari di debug gestito.  
  
 Nelle tabelle riportate di seguito sono indicate le impostazioni consigliate delle proprietà.  
  
 Le impostazioni non specificate in queste tabelle possono variare in base al tipo di progetto gestito. Ad esempio, la proprietà **Azione di avvio** verrà impostata in modo diverso in un progetto Windows Form e in un progetto [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
### <a name="configuration-properties-on-the-build-c-or-compile-visual-basic-tab"></a>Proprietà di configurazione disponibili nella scheda Compila (C#) o Compila (Visual Basic)  
  
|**Nome proprietà**|**Impostazione**|  
|-----------------------|-----------------|  
|**Definisci costante DEBUG**|C#e F#: Impostare la casella di controllo selezionata. per consentire all'applicazione di utilizzare la classe Debug.|  
|**Definisci costante TRACE**|C#e F#: Impostare la casella di controllo selezionata. per consentire all'applicazione di utilizzare la classe Trace.|  
|**Ottimizza codice**|C#, F#e Visual Basic: Impostare su false. L'esecuzione del debug di codice ottimizzato è più complessa perché le istruzioni generate non corrispondono direttamente al codice sorgente. Se si nota un bug presente solo nel codice ottimizzato del programma, è possibile attivare questa impostazione, tenendo però presente che il codice riportato nella finestra **Disassembly** è generato da codice sorgente ottimizzato che potrebbe non corrispondere a quanto visualizzato nell'editor del codice. Per eseguire il debug di codice ottimizzato, disattivare Just My Code. (Vedere [Limitare l'esecuzione di istruzioni a Just My Code](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code)).<br /><br /> Per altre informazioni, vedere [impostazioni di progetto per C# Debug Configurations](../debugger/project-settings-for-csharp-debug-configurations.md) oppure [impostazioni di progetto per una configurazione di Debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).|  
|**Percorso output**|Impostare su bin\Debug\\.|  
|**Opzioni di compilazione avanzate**|Solo Visual Basic. Fare clic su **Avanzate** per impostare le proprietà avanzate descritte nella tabella riportata di seguito.|  
  
### <a name="advanced-compiler-settings-dialog-box"></a>Finestra di dialogo Impostazioni del compilatore avanzate  
  
|**Nome proprietà**|**Impostazione**|  
|-----------------------|-----------------|  
|**Abilita ottimizzazioni**|Impostare su false per i motivi indicati nella **Ottimizza codice** opzione nella tabella precedente.|  
|**Genera informazioni di debug**|Selezionare questa casella di controllo se si desidera che durante la compilazione venga impostato il flag /DEBUG. In questo modo verranno generate le informazioni necessarie per semplificare il debug.|  
|**Definisci costante DEBUG**|Selezionare questa casella di controllo per definire la costante `DEBUG`, che consente all'applicazione di utilizzare la classe <xref:System.Diagnostics.Debug>.|  
|**Definisci costante TRACE**|Selezionare questa casella di controllo per definire la costante `TRACE`, che consente all'applicazione di utilizzare la classe <xref:System.Diagnostics.Trace>.|  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di codice gestito](../debugger/debugging-managed-code.md)   
 [Tipi di progetto C#, F# e Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)