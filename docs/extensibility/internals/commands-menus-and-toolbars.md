---
title: Comandi, menu e barre degli strumenti Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- commands [Visual Studio]
- toolbars [Visual Studio], commands
ms.assetid: 07b4ed90-dbbd-40df-b6c9-8395fd6f2ab6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2be2f719d0f123328d5c518c08e30df2185e2a19
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709499"
---
# <a name="commands-menus-and-toolbars"></a>Comandi, menu e barre degli strumenti
Menu e barre degli strumenti sono il modo in cui gli utenti accedono ai comandi nel pacchetto VSPackage.Menus and toolbars are the way users access commands in your VSPackage. I comandi sono funzioni che eseguono attività, ad esempio la stampa di un documento, l'aggiornamento di una visualizzazione o la creazione di un nuovo file. Menu e barre degli strumenti sono pratici metodi grafici per presentare i comandi agli utenti. In genere, i comandi correlati sono raggruppati nello stesso menu o sulla stessa barra degli strumenti.

- I menu vengono in genere visualizzati come stringhe di una sola parola raggruppate su una riga nella parte superiore dell'ambiente di sviluppo integrato (IDE, Integrated Development Environment) o in una finestra degli strumenti. I menu possono essere visualizzati anche come risultato di un evento di clic con il pulsante destro del mouse e in tal caso vengono definiti menu di scelta rapida. Quando si fa clic su di essi, i menu si espandono per visualizzare uno o più comandi. Facendo clic sui comandi è possibile eseguire attività oppure aprire sottomenu che contengono altri comandi. Alcuni nomi di menu noti sono **File**, **Modifica**, **Visualizza**e **Finestra**. Per ulteriori informazioni, consultate [Estendere menu e comandi.](../../extensibility/extending-menus-and-commands.md)

- Le barre degli strumenti sono in genere righe di pulsanti e altri controlli, ad esempio caselle combinate, caselle di riepilogo, caselle di testo e controller di menu. Tutti i controlli delle barre degli strumenti sono associati a comandi. Quando si fa clic su un pulsante della barra degli strumenti, viene attivato il comando associato. I pulsanti della barra degli strumenti hanno in genere icone che suggeriscono i comandi sottostanti, ad esempio una stampante per un comando Stampa. In un controllo elenco a discesa, ogni elemento nell'elenco è associato a un comando diverso. Un controller di menu è un oggetto ibrido in cui un lato del controllo è un pulsante della barra degli strumenti e l'altro lato è una freccia rivolta verso il basso che visualizza altri comandi quando si fa clic su di essa. Per ulteriori informazioni, consultate Aggiungere un controller di [menu a una barra degli strumenti.](../../extensibility/adding-a-menu-controller-to-a-toolbar.md)

- Quando si crea un comando, è anche necessario creare un gestore eventi per esso. Il gestore eventi determina quando il comando è visibile o abilitato, consente di modificarne il testo e garantisce che il comando risponda in modo appropriato ("routing") quando attivato. Nella maggior parte dei casi, l'IDE gestisce i comandi usando l'interfaccia <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>. I comandi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] eseguono il routing in modo gerarchico, a partire dal contesto del comando più interno, in base alla selezione locale, e procedendo verso il contesto più esterno, in base alla selezione globale. I comandi aggiunti al menu principale sono immediatamente disponibili per lo scripting. Per ulteriori informazioni, vedere [MenuCommands vs.](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015) [Selection context objects](../../extensibility/internals/selection-context-objects.md)

  Per definire nuovi menu e barre degli strumenti, è necessario descriverli in un file della tabella dei comandi di Visual Studio (*.vsct*). Il modello di pacchetto di Visual Studio crea automaticamente questo file, insieme agli elementi necessari per supportare i comandi, le barre degli strumenti e gli editor selezionati nel modello. In alternativa, è possibile scrivere un file *vsct* personalizzato utilizzando lo schema XML descritto di seguito: [VSCT XML schema reference](../../extensibility/vsct-xml-schema-reference.md).

  Per ulteriori informazioni sull'utilizzo dei file *vsct,* vedere File della tabella dei comandi di [Visual Studio (con estensione vsct).](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

  Negli argomenti di questa sezione viene illustrato il funzionamento di comandi, menu e barre degli strumenti in VSPackage.The topics in this section explain how commands, menus, and toolbars work in VSPackages.

## <a name="in-this-section"></a>Contenuto della sezione
- [Come VSPackage aggiungere elementi dell'interfaccia utenteHow VSPackages add user interface elements](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Descrizione approfondita della specifica del formato della tabella dei comandi.

- [File della tabella dei comandi di Visual Studio (con estensione vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

 Vengono descritti una sintassi basata su XML e un compilatore per le tabelle dei comandi.

- [Posizionamento predefinito di comandi, gruppi e barre degli strumenti](../../extensibility/internals/default-command-group-and-toolbar-placement.md)

 Descrive i comandi, i gruppi, i menu e le barre degli strumenti predefiniti.

- [Comandi, menu e gruppi definiti dall'IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)

 Specifica i menu predefiniti, i comandi e i gruppi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di comandi disponibili per l'utilizzo da parte dell'IDE.

- [Progettazione dei comandi](../../extensibility/internals/command-design.md)

 Viene illustrato come progettare i comandi.

- [Ottimizzare i comandi dei menu e delle barre degli strumenti](../../extensibility/internals/optimizing-menu-and-toolbar-commands.md)

 Fornisce linee guida per i comandi.

- [Rendere disponibili i comandi](../../extensibility/internals/making-commands-available.md)

 Viene illustrato come rendere i comandi disponibili per Visual Studio.

- [Comandi e menu che utilizzano assembly di interoperabilitàCommands and menus that use interop assemblies](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)

 Viene illustrato come implementare comandi che utilizzano assembly di interoperabilità.

## <a name="related-sections"></a>Sezioni correlate
- [Routing dei comandi nei pacchetti VSPackageCommand routing in VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)

 Viene illustrato il routing dei comandi nei pacchetti VSPackage.
