---
title: Disabilitazione del debugger per Windows Workflow Foundation (legacy) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, disabling debugger
- debugging workflows, disabling debugger
- workflow debugger, disabling
ms.assetid: 9da96d0e-f941-4fa9-a1a5-6bab50adfec9
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: eddd72d648e7349f51096a21131f38c2e370a277
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656790"
---
# <a name="disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Disattivazione del debugger di Visual Studio per Windows Workflow Foundation (legacy)
In questo argomento viene descritto come disabilitare il Debugger [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] usando il file di configurazione in caso di compilazione di applicazioni [!INCLUDE[wf](../includes/wf-md.md)] in [!INCLUDE[wfd1](../includes/wfd1-md.md)] legacy. Usare la [!INCLUDE[wfd2](../includes/wfd2-md.md)] legacy quando è necessario fare riferimento a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Per impostazione predefinita, il debugger di [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] per [!INCLUDE[wf](../includes/wf-md.md)] è abilitato per un processo host. Per disabilitare il debug del flusso di lavoro, è necessario disattivarlo in modo esplicito aggiungendo una voce "DisableWorkflowDebugging" **\<switches elemento >** nella sezione **\<system. Diagnostics >** del file di configurazione dell'host.

 Nell’esempio seguente viene illustrato come modificare il file di configurazione dell’host per disabilitare il debug del flusso di lavoro.

```
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
 [Richiamo del debugger di Visual Studio per i flussi di lavoro legacy di debug Windows Workflow Foundation (legacy)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md) [Debug dei flussi di lavoro legacy](../workflow-designer/debugging-legacy-workflows.md)