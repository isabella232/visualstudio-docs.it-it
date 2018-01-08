---
redirect_url: shell/modifying-the-isolated-shell-by-using-the-dot-vsct-file
title: Modifica la Shell isolata tramite il. Il File Vsct | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode, .vsct file
ms.assetid: 6d147c2d-10e9-400e-b8ce-5566287b41ba
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ddf48e384b85946d4efcbb62359f24780507dfa4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="modifying-the-isolated-shell-by-using-the-vsct-file"></a>Modifica la Shell isolata tramite il. File Vsct
Il progetto di interfaccia utente per un progetto di Visual Studio shell isolata contiene un file vsct che consente di specificare quali gruppi di applicazioni e singoli comandi sono disponibili nell'applicazione. Di seguito è un estratto da un file con estensione vsct non modificato.  
  
```  
<!-- <Define name="No_WindowListCommand"/> -->  
<!-- <Define name="No_MoreWindowsCommand"/> -->  
<!-- <Define name="No_PaneNextPaneCommand"/> -->  
<!-- <Define name="No_PanePrevPaneCommand"/> -->  
```  
  
 Per impostazione predefinita, la maggior parte dei comandi e i gruppi di comandi sono inclusi. Per escludere un comando o un gruppo di comando, è sufficiente rimuovere il commento tale comando o un gruppo.  
  
 Ad esempio, per rimuovere il riquadro successivo e precedente comandi riquadro, rimuovere il commento di `No_PaneNextPaneCommand` e `No_PanePrevPaneCommand` voci:  
  
```  
  
<Define name="No_PaneNextPaneCommand"/> <Define name="No_PanePrevPaneCommand"/>  
  
```  
  
 Per più dettagliata di esempio queste personalizzazioni, vedere [procedura dettagliata: creazione di un'applicazione Shell isolata di base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="referenced-files"></a>File di riferimento  
 Il file con estensione vsct predefinito per un'applicazione fa riferimento a file seguenti. Questi file si trovano nella sottodirectory \VisualStudioIntegration\Common\Inc\ della directory di installazione di Visual Studio SDK.  
  
|File|Descrizione|  
|----------|-----------------|  
|wbids.h|Identità dell'interfaccia utente per il pacchetto Web Sfoglia.|  
|AppIDCmdUsed.vsct|Tabella comandi per gli elementi dell'interfaccia utente di Visual Studio primari.|  
|EmulatorCmdUsed.vsct|Tabella per elementi di interfaccia emulazione editor Emacs e della descrizione comandi.|  
|Vsdebugguids.h|Definisce i GUID di comandi, pagina Opzioni e altre funzionalità del debugger di Visual Studio.|  
|VsDbgCmdUsed.vsct|Tabella comandi per il debugger.|  
  
 Il file AppIDCmdUsed.vsct include gli elementi dell'interfaccia utente di Visual Studio in base ai simboli definiti nel file con estensione vsct dell'applicazione.  
  
 Per ulteriori informazioni, vedere [Progettazione tabella comandi XML (. File Vsct)](../extensibility/internals/designing-xml-command-table-dot-vsct-files.md) e [riferimento allo Schema XML VSCT](../extensibility/vsct-xml-schema-reference.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Isolated Shell](../extensibility/visual-studio-isolated-shell.md)