---
title: Modifica della Shell isolata tramite il. File Vsct | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .vsct file
ms.assetid: 6d147c2d-10e9-400e-b8ce-5566287b41ba
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 67955586333cf665b7cffd5039ef2f6e051834a9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49260000"
---
# <a name="modifying-the-isolated-shell-by-using-the-vsct-file"></a>Modifica della Shell isolata tramite il. File Vsct
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il progetto dell'interfaccia utente per un progetto di shell isolata di Visual Studio contiene un file vsct che consente di specificare quali gruppi di applicazioni e i singoli comandi sono disponibili nell'applicazione. Di seguito è riportato un estratto da un file con estensione vsct non modificato.  
  
```  
<!-- <Define name="No_WindowListCommand"/> -->  
<!-- <Define name="No_MoreWindowsCommand"/> -->  
<!-- <Define name="No_PaneNextPaneCommand"/> -->  
<!-- <Define name="No_PanePrevPaneCommand"/> -->  
```  
  
 Per impostazione predefinita, la maggior parte dei comandi e i gruppi di comandi sono inclusi. Per escludere un comando o un gruppo di comando, è sufficiente rimuovere il commento tale comando o un gruppo.  
  
 Ad esempio, per rimuovere il riquadro successivo e precedente comandi riquadro, rimuovere il commento il `No_PaneNextPaneCommand` e `No_PanePrevPaneCommand` voci:  
  
```  
  
<Define name="No_PaneNextPaneCommand"/> <Define name="No_PanePrevPaneCommand"/>  
  
```  
  
 Per una più dettagliate esempio queste personalizzazioni, vedere [procedura dettagliata: creazione di un'applicazione Shell isolata di base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="referenced-files"></a>File di riferimento  
 Il file con estensione vsct predefinito per un'applicazione fa riferimento ai file seguenti. Questi file si trovano nella sottodirectory \VisualStudioIntegration\Common\Inc\ della directory di installazione di Visual Studio SDK.  
  
|File|Descrizione|  
|----------|-----------------|  
|wbids.h|Identità dell'interfaccia utente per il pacchetto Web Sfoglia.|  
|AppIDCmdUsed.vsct|Tabella di comandi per gli elementi dell'interfaccia utente di Visual Studio primari.|  
|EmulatorCmdUsed.vsct|Tabella di comando per Emacs e Brief elementi dell'interfaccia utente di emulazione dell'editor.|  
|Vsdebugguids.h|Definisce i GUID dei comandi, pagina delle opzioni e altre funzionalità del debugger di Visual Studio.|  
|VsDbgCmdUsed.vsct|Tabella di comando per il debugger.|  
  
 Il file AppIDCmdUsed.vsct include gli elementi dell'interfaccia utente di Visual Studio in base ai simboli definiti nel file con estensione vsct dell'applicazione.  
  
 Per altre informazioni, vedere [Progettazione tabella comandi XML (. File Vsct)](../extensibility/internals/designing-xml-command-table-dot-vsct-files.md) e il [riferimento allo Schema XML VSCT](../extensibility/vsct-xml-schema-reference.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Isolated Shell](../extensibility/visual-studio-isolated-shell.md)

