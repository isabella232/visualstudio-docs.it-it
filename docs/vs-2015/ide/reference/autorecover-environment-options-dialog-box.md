---
title: Salvataggio automatico, Ambiente, finestra di dialogo Opzioni | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPag.Environment.AutoRecover
- VS.DialogAutoRestore
- VS.ToolsOptionsPages.Environment.AutoRecover
- VS.ToolsOptionsPages.Environment.Auto_Save_and_Restore
helpviewer_keywords:
- files, recovering
- AutoRecover page
- saving files, automatically
- files, saving automatically
ms.assetid: 397e5e44-4bbe-4289-94d1-642b466c9111
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4d99cef315e37d729db856376929c27cd8b2fe55
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433710"
---
# <a name="autorecover-environment-options-dialog-box"></a>Salvataggio automatico, Ambiente, finestra di dialogo Opzioni
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

È possibile usare questa pagina della finestra di dialogo Opzioni per specificare se eseguire o meno il backup automatico dei file. Questa pagina consente anche di specificare se ripristinare i file modificati nel caso di arresto imprevisto dell'ambiente di sviluppo integrato (IDE). È possibile accedere a questa finestra di dialogo selezionando **Opzioni** dal menu **Strumenti**, scegliendo la cartella **Ambiente** e poi la pagina **Salvataggio automatico**. Se questa pagina non viene visualizzata nell'elenco, selezionare **Mostra tutte le impostazioni** nella finestra di dialogo **Opzioni**.  
  
> [!NOTE]
> Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere Importa/esporta impostazioni dal menu Strumenti. Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 **Salva automaticamente le informazioni ogni \<n> minuti**  
 Usare questa opzione per personalizzare la frequenza con cui un file viene salvato automaticamente nell'editor. Per i file salvati in precedenza, viene salvata una copia del file in \\...\Documenti\Visual Studio \<*versione*>\File di backup\\<*nomeprogetto*>. Se si tratta di un nuovo file che non è stato salvato manualmente, il file viene salvato automaticamente assegnando un nome file generato in modo casuale.  
  
 **Mantieni informazioni di salvataggio automatico per \<n> giorni**  
 Usare questa opzione per specificare per quanto tempo i file creati per il salvataggio automatico devono restare memorizzati in Visual Studio.  
  
## <a name="see-also"></a>Vedere anche  
 [Finestra di dialogo Opzioni](../../ide/reference/options-dialog-box-visual-studio.md)
