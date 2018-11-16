---
title: GUID e ID dei comandi di Visual Studio | Microsoft Docs
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
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a1dbf79cc90f1f0ab0a7ff982fcabfa8d52150d3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51760150"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>GUID e ID dei comandi di Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

I valori GUID e ID dei comandi inclusi nell'ambiente di sviluppo integrato (IDE) di Visual Studio vengono definiti nei file con estensione vsct che vengono installati come parte di Visual Studio SDK. Per altre informazioni, vedere [IDE-Defined comandi, menu e gruppi](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).  
  
 Per altre informazioni su come utilizzare gli oggetti dell'IDE che sono definiti in file con estensione vsct, vedere [estensione di menu e comandi](../../extensibility/extending-menus-and-commands.md).  
  
## <a name="finding-a-command-definition"></a>Ricerca di una definizione di comando  
 Poiché Visual Studio definisce i comandi di più di mille, non è pratico elencarle tutte in questo articolo. Al contrario, seguire questi passaggi per individuare la definizione di un comando.  
  
#### <a name="to-locate-a-command-definition"></a>Per individuare una definizione di comando  
  
1. In Visual Studio, aprire i file seguenti nella *percorso di installazione di Visual Studio SDK*cartella \VisualStudioIntegration\Common\Inc\: SharedCmdDef.vsct, ShellCmdDef.vsct, VsDbgCmdUsed.vsct, Venusmenu.vsct.  
  
    La maggior parte dei comandi di Visual Studio sono definiti in SharedCmdDef.vsct e ShellCmdDef.vsct. VsDbgCmdUsed.vsct definisce i comandi relativi al debugger e Venusmenu.vsct definisce i comandi specifici per lo sviluppo Web.  
  
2. Se il comando è una voce di menu, tenere presente il testo esatto della voce di menu. Se il comando è un pulsante sulla barra degli strumenti, si noti il testo della descrizione comando visualizzato quando si posiziona su di esso.  
  
3. Premere CTRL + F per aprire la **trovare** nella finestra di dialogo.  
  
4. Nel **Find what** , digitare il testo annotato nel passaggio 2.  
  
5. Verificare che **tutti i documenti aperti** viene visualizzato nei **Cerca in** casella.  
  
6. Fare clic sui **Trova successivo** pulsante fino a quando il testo selezionato nella `<Strings>` sezione di un [elemento pulsante](../../extensibility/button-element.md).  
  
    Il `<Button>` elemento che il comando viene visualizzata in è la definizione di comando.  
  
   Quando è stata trovata la definizione di comando, è possibile inserire una copia del comando in un altro menu o sulla barra degli strumenti mediante la creazione di un [elemento CommandPlacement](../../extensibility/commandplacement-element.md) che ha gli stessi `guid` e `id` valori del comando. Per altre informazioni, vedere [creazione di gruppi riutilizzabili di pulsanti](../../extensibility/creating-reusable-groups-of-buttons.md).  
  
### <a name="special-cases"></a>Casi speciali  
 Nei casi seguenti, il testo del menu o il testo della descrizione comando potrebbe non corrispondere esattamente quali sono le novità della definizione del comando.  
  
-   Voci di menu che includono un carattere sottolineato, ad esempio la **Print** comando il **File** menu, in cui il P è sottolineato.  
  
     I caratteri preceduti dal carattere '&' nei nomi di voce di menu sono visualizzati come sottolineato. Tuttavia, i file con estensione vsct sono scritti in XML, che usa il carattere '&' per indicare i caratteri speciali e richiede che deve essere digitata una e commerciale che deve essere visualizzato come&amp;'. Pertanto, in un file con estensione vsct, il **Print** comando è visualizzato come '&amp;Print'.  
  
-   I comandi che hanno testo dinamico, ad esempio **salvare** *Filename corrente*e generato dinamicamente le voci di menu, ad esempio gli elementi nel **file recenti** elenco.  
  
     Non vi è alcun modo affidabile per cercare testo dinamico. In alternativa, trovare un gruppo che ospita il comando desiderato consultando [GUID e ID del menu di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) oppure [GUID e ID di Visual Studio le barre degli strumenti](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)e cercare l'ID di tale gruppo. Se la definizione di comando non è presente il gruppo come relativo [elemento padre](../../extensibility/parent-element.md), cercare SharedCmdPlace.vsct e ShellCmdPlace.vsct (o VsDbgCmdPlace.vsct per i comandi del debugger) un `<CommandPlacement>` che imposta l'elemento padre dell'elemento di comando. AndVsDbgCmdPlace.vsct SharedCmdPlace.vsct, ShellCmdPlace.vsct, inclusi i *percorso di installazione di Visual Studio SDK*\VisualStudioIntegration\Common\Inc\ cartella.  
  
## <a name="see-also"></a>Vedere anche  
 [Confronto tra oggetti MenuCommand e OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md)   
 [Visual Studio Command Table (. File Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Riferimenti sullo schema XML VSCT](../../extensibility/vsct-xml-schema-reference.md)

