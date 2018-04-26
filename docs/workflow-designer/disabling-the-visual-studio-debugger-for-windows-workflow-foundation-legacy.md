---
title: Finestra di progettazione del flusso di lavoro - disabilitazione Debugger di Visual Studio per Windows Workflow Foundation (Legacy)
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- workflows, disabling debugger
- debugging workflows, disabling debugger
- workflow debugger, disabling
ms.assetid: 9da96d0e-f941-4fa9-a1a5-6bab50adfec9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 473ee507e35f5ec5df902df64ee34326dcf90a2b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Disattivazione del debugger di Visual Studio per Windows Workflow Foundation (legacy)

In questo argomento viene descritto come disabilitare il Debugger di Visual Studio usando il file di configurazione quando si compilano applicazioni di Windows Workflow Foundation (WF) in Progettazione flussi di lavoro Windows legacy. Utilizzare la finestra di progettazione del flusso di lavoro legacy quando è necessario avere come destinazione .NET Framework versione 3.5 o la WinFX.

 Per impostazione predefinita, di Visual Studio del Debugger per Windows Workflow Foundation (WF) è abilitato per un processo host. Per disabilitare il debug del flusso di lavoro, è necessario disattivarlo in modo esplicito aggiungendo la voce "disableworkflowdebugging al"  **\<commutatori >** elemento il  **\<System. Diagnostics >** sezione del file di configurazione host.

 Nell’esempio seguente viene illustrato come modificare il file di configurazione dell’host per disabilitare il debug del flusso di lavoro.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
   <system.diagnostics>
      <switches>
         <add name="DisableWorkflowDebugging" value="true"/>
      </switches>
   </system.diagnostics>
</configuration>
```

## <a name="see-also"></a>Vedere anche

- [Richiamo del debugger di Visual Studio per Windows Workflow Foundation (legacy)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)
- [Debug dei flussi di lavoro legacy](../workflow-designer/debugging-legacy-workflows.md)