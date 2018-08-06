---
title: I comandi, menu e barre degli strumenti | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- commands [Visual Studio]
- toolbars [Visual Studio], commands
ms.assetid: 07b4ed90-dbbd-40df-b6c9-8395fd6f2ab6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 686e3a5df183d7296aba8eacffbf061d4d5f958f
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2018
ms.locfileid: "39510806"
---
# <a name="commands-menus-and-toolbars"></a>I comandi, menu e barre degli strumenti
Menu e barre degli strumenti sono che consente agli utenti di accedere ai comandi nel pacchetto VSPackage. I comandi sono funzioni che eseguono attività, ad esempio la stampa di un documento, l'aggiornamento di una visualizzazione o la creazione di un nuovo file. Menu e barre degli strumenti sono pratici metodi grafici per presentare i comandi agli utenti. In genere, i comandi correlati sono raggruppati nello stesso menu o sulla stessa barra degli strumenti.  
  
-   I menu vengono in genere visualizzati come stringhe di una sola parola raggruppate su una riga nella parte superiore dell'ambiente di sviluppo integrato (IDE, Integrated Development Environment) o in una finestra degli strumenti. I menu possono essere visualizzati anche come risultato di un evento di clic con il pulsante destro del mouse e in tal caso vengono definiti menu di scelta rapida. Quando si fa clic su di essi, i menu si espandono per visualizzare uno o più comandi. Facendo clic sui comandi è possibile eseguire attività oppure aprire sottomenu che contengono altri comandi. Alcuni nomi di menu molto noti **File**, **Edit**, **visualizzazione**, e **finestra**. Per altre informazioni, vedere [estendono i menu e comandi](../../extensibility/extending-menus-and-commands.md).  
  
-   Le barre degli strumenti sono in genere righe di pulsanti e altri controlli, ad esempio caselle combinate, caselle di riepilogo, caselle di testo e controller di menu. Tutti i controlli delle barre degli strumenti sono associati a comandi. Quando si fa clic su un pulsante della barra degli strumenti, viene attivato il comando associato. I pulsanti della barra degli strumenti hanno in genere icone che suggeriscono i comandi sottostanti, ad esempio una stampante per un comando Stampa. In un controllo elenco a discesa, ogni elemento nell'elenco è associato a un comando diverso. Un controller di menu è un oggetto ibrido in cui un lato del controllo è un pulsante della barra degli strumenti e l'altro lato è una freccia rivolta verso il basso che visualizza altri comandi quando si fa clic su di essa. Per altre informazioni, vedere [aggiungere un controller di menu per una barra degli strumenti](../../extensibility/adding-a-menu-controller-to-a-toolbar.md).  
  
-   Quando si crea un comando, è anche necessario creare un gestore eventi per esso. Il gestore eventi determina quando il comando è visibile o abilitato, consente di modificarne il testo e garantisce che il comando risponda in modo appropriato ("routing") quando attivato. Nella maggior parte dei casi, l'IDE gestisce i comandi usando il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia. I comandi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] route in modo gerarchico, inizia con il contesto del comando più interno, in base alla selezione locale e procedendo verso il contesto più esterno, in base alla selezione globale. I comandi aggiunti al menu principale sono immediatamente disponibili per lo scripting. Per altre informazioni, vedere [vs confronto tra oggetti MenuCommand. OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md) e [gli oggetti di contesto di selezione](../../extensibility/internals/selection-context-objects.md).  
  
 Per definire nuovi menu e barre degli strumenti, è necessario descriverli in una tabella di comandi di Visual Studio (*vsct*) file. Il modello di pacchetto di Visual Studio crea questo file, con gli elementi necessari per supportare qualsiasi comandi, barre degli strumenti ed editor selezionato nel modello. In alternativa, è possibile scrivere il proprio *vsct* del file, usando il linguaggio XML schema descritto qui: [riferimenti allo schema XML VSCT](../../extensibility/vsct-xml-schema-reference.md).  
  
 Per altre informazioni sull'utilizzo con *vsct* i file, vedere [file table (vsct) di Visual Studio comando](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Gli argomenti di questa sezione illustrano funzionamento dei comandi, menu e barre degli strumenti in VSPackage.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Una descrizione approfondita della specifica di formato di tabella comandi.  
  
 [File di Visual Studio comando table (vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)  
 Descrive una sintassi basata su XML e compilatore per le tabelle di comando.  
  
 [Posizione di comando, il gruppo e sulla barra degli strumenti predefinita](../../extensibility/internals/default-command-group-and-toolbar-placement.md)  
 Descrive barre degli strumenti, i gruppi, i menu e comandi predefiniti.  
  
 [I gruppi, menu e comandi definiti dall'IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)  
 Specifica il menu di scelta predefiniti, comandi e gruppi di comandi disponibili per l'utilizzo da parte di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 [Progettazione dei comandi](../../extensibility/internals/command-design.md)  
 Descrive come progettare i comandi.  
  
 [Ottimizzare i comandi di menu e barra degli strumenti](../../extensibility/internals/optimizing-menu-and-toolbar-commands.md)  
 Offre linee guida per i comandi.  
  
 [Rendere disponibili i comandi](../../extensibility/internals/making-commands-available.md)  
 Spiega come rendere disponibili i comandi di Visual Studio.  
  
 [I comandi e menu che usano assembly di interoperabilità](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)  
 Viene illustrato come implementare i comandi che usano assembly di interoperabilità.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Routing dei comandi nei pacchetti VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)  
 Viene illustrato il routing dei comandi nei pacchetti VSPackage.