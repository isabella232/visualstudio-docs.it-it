---
title: Modifica della shell isolata tramite. File vsct | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .vsct file
ms.assetid: 6d147c2d-10e9-400e-b8ce-5566287b41ba
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8c106a04e809e772ac3b8a77192fb2f101161e9c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194227"
---
# <a name="modifying-the-isolated-shell-by-using-the-vsct-file"></a>Modifica della shell isolata tramite il file con estensione vsct
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il progetto dell'interfaccia utente per un progetto di Visual Studio Isolated Shell contiene un file con estensione vsct che consente di specificare quali gruppi di applicazioni e singoli comandi sono disponibili nell'applicazione. Di seguito è riportato un Estratto da un file con estensione vsct non modificato.  
  
```  
<!-- <Define name="No_WindowListCommand"/> -->  
<!-- <Define name="No_MoreWindowsCommand"/> -->  
<!-- <Define name="No_PaneNextPaneCommand"/> -->  
<!-- <Define name="No_PanePrevPaneCommand"/> -->  
```  
  
 Per impostazione predefinita, sono inclusi la maggior parte dei comandi e dei gruppi di comandi. Per escludere un comando o un gruppo di comandi, è sufficiente rimuovere il commento dal comando o dal gruppo.  
  
 Ad esempio, per rimuovere i comandi riquadro successivo e riquadro precedente, rimuovere il commento `No_PaneNextPaneCommand` dalle `No_PanePrevPaneCommand` voci e:  
  
```  
  
<Define name="No_PaneNextPaneCommand"/> <Define name="No_PanePrevPaneCommand"/>  
  
```  
  
 Per un esempio più dettagliato di queste personalizzazioni, vedere [procedura dettagliata: creazione di un'applicazione shell isolata di base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="referenced-files"></a>File di riferimento  
 Il file con estensione vsct predefinito per un'applicazione fa riferimento ai file seguenti. Questi file si trovano nella sottodirectory \VisualStudioIntegration\Common\Inc\ della directory di installazione di Visual Studio SDK.  
  
|File|Descrizione|  
|----------|-----------------|  
|wbids. h|Identità dell'interfaccia utente per il pacchetto Web browse.|  
|AppIDCmdUsed. vsct|Tabella dei comandi per gli elementi primari dell'interfaccia utente di Visual Studio.|  
|EmulatorCmdUsed. vsct|Tabella dei comandi per gli elementi dell'interfaccia utente dell'emulazione di Emacs e Brief Editor.|  
|Vsdebugguids. h|Definisce i GUID della pagina comandi, opzioni e altre funzionalità del debugger di Visual Studio.|  
|VsDbgCmdUsed. vsct|Tabella dei comandi per il debugger.|  
  
 Il file AppIDCmdUsed. vsct include gli elementi dell'interfaccia utente di Visual Studio in base ai simboli definiti nel file Application. vsct.  
  
 Per ulteriori informazioni, vedere [progettazione della tabella dei comandi XML (. Vsct)](../extensibility/internals/designing-xml-command-table-dot-vsct-files.md) e [vsct XML Schema Reference](../extensibility/vsct-xml-schema-reference.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Isolated Shell](../extensibility/visual-studio-isolated-shell.md)
