---
title: GUID e ID dei comandi di Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 35e2c354293679d9cb6044b0c5f21b77aadb7f52
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220160"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>Comandi i GUID e ID di Visual Studio
I valori GUID e ID dei comandi inclusi nell'ambiente di sviluppo integrato (IDE) di Visual Studio vengono definiti nei file con estensione vsct che vengono installati come parte di Visual Studio SDK. Per altre informazioni, vedere [definiti dall'IDE comandi, menu e gruppi](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).  
  
 Per altre informazioni su come lavorare con gli oggetti definiti in IDE *vsct* i file, vedere [estendono i menu e comandi](../../extensibility/extending-menus-and-commands.md).  
  
## <a name="find-a-command-definition"></a>Trovare una definizione di comando  
 Poiché Visual Studio definisce i comandi più di 1000, è poco pratica per elencarle tutte in questo articolo. Al contrario, seguire questi passaggi per individuare la definizione di un comando.  
  
### <a name="to-locate-a-command-definition"></a>Per individuare una definizione di comando  
  
1. In Visual Studio, aprire i file seguenti nella *< percorso di installazione di Visual Studio SDK\>\visualstudiointegration\common\inc.\\*  cartella: *SharedCmdDef.vsct*, *ShellCmdDef.vsct*, *VsDbgCmdUsed.vsct*, *Venusmenu.vsct*.  
  
    La maggior parte dei comandi di Visual Studio sono definiti nel *SharedCmdDef.vsct* e *ShellCmdDef.vsct*. *VsDbgCmdUsed.vsct* definisce i comandi relativi al debugger, e *Venusmenu.vsct* definisce i comandi specifici per lo sviluppo Web.  
  
2. Se il comando è una voce di menu, tenere presente il testo esatto della voce di menu. Se il comando è un pulsante sulla barra degli strumenti, si noti il testo della descrizione comando visualizzato quando si posiziona su di esso.  
  
3. Premere **Ctrl**+**F** per aprire la **trovare** nella finestra di dialogo.  
  
4. Nel **Find what** , digitare il testo annotato nel passaggio 2.  
  
5. Verificare che **tutti i documenti aperti** viene visualizzato nei **Cerca in** casella.  
  
6. Fare clic sui **Trova successivo** pulsante fino a quando il testo selezionato nella `<Strings>` sezione di un [elemento pulsante](../../extensibility/button-element.md).  
  
    Il `<Button>` elemento che il comando viene visualizzata in è la definizione di comando.  
  
   Quando è stata trovata la definizione di comando, è possibile inserire una copia del comando in un altro menu o sulla barra degli strumenti mediante la creazione di un [elemento CommandPlacement](../../extensibility/commandplacement-element.md) che ha gli stessi `guid` e `id` valori del comando. Per altre informazioni, vedere [creazione di gruppi riutilizzabili di pulsanti](../../extensibility/creating-reusable-groups-of-buttons.md).  
  
### <a name="special-cases"></a>Casi speciali  
 Nei casi seguenti, il testo del menu o il testo della descrizione comando potrebbe non corrispondere esattamente quali sono le novità della definizione del comando.  
  
-   Voci di menu che includono un carattere sottolineato, ad esempio la **Print** comando il **File** dal menu in cui il *P* è sottolineato.  
  
     Caratteri preceduti da una e commerciale (&) carattere in nomi di menu vengono visualizzate come sottolineato. Tuttavia *vsct* i file vengono scritti in formato XML, che usa il carattere e commerciale (&) per indicare i caratteri speciali e richiede che una e commerciale da visualizzare deve essere digitata come  *&amp;amp;*. Pertanto, in un *vsct* file, il **stampa** comando viene visualizzata come  *&amp;amp; Stampa*.  
  
-   I comandi che hanno testo dinamico, ad esempio **salvare** \<Filename corrente\>e generato dinamicamente le voci di menu, ad esempio gli elementi nel **file recenti** elenco.  
  
     Non vi è alcun modo affidabile per cercare testo dinamico. In alternativa, trovare un gruppo che ospita il comando desiderato consultando [menu GUID e ID di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) o [GUID e ID di Visual Studio le barre degli strumenti](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)e cercare l'ID di tale gruppo. Se la definizione di comando non è presente il gruppo come relativo [elemento padre](../../extensibility/parent-element.md), ricerca *SharedCmdPlace.vsct* e *ShellCmdPlace.vsct* (o  *VsDbgCmdPlace.vsct* per i comandi del debugger) per un `<CommandPlacement>` elemento che imposta l'elemento padre del comando. *SharedCmdPlace.vsct*, *ShellCmdPlace.vsct*, e *VsDbgCmdPlace.vsct* presenti il *\<percorso di installazione di Visual Studio SDK\>\ VisualStudioIntegration\Common\Inc\\* cartella.  
  
## <a name="see-also"></a>Vedere anche  
 [Confronto tra oggetti MenuCommand Visual Studio. OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)   
 [File di Visual Studio comando table (vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Riferimento allo schema XML VSCT](../../extensibility/vsct-xml-schema-reference.md)
