---
title: Comandi, menu e barre degli strumenti | Microsoft Docs
description: Informazioni sui comandi, i menu e le barre degli strumenti in Visual Studio, incluse le funzionalità e il modo in cui funzionano nei pacchetti VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- commands [Visual Studio]
- toolbars [Visual Studio], commands
ms.assetid: 07b4ed90-dbbd-40df-b6c9-8395fd6f2ab6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2a1b4cdb95fa5b053bc75efb559ea77b84ae56dd
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057156"
---
# <a name="commands-menus-and-toolbars"></a>Comandi, menu e barre degli strumenti
I menu e le barre degli strumenti sono il modo in cui gli utenti accedono ai comandi nel pacchetto VSPackage. I comandi sono funzioni che eseguono attività, ad esempio la stampa di un documento, l'aggiornamento di una visualizzazione o la creazione di un nuovo file. Menu e barre degli strumenti sono pratici metodi grafici per presentare i comandi agli utenti. In genere, i comandi correlati sono raggruppati nello stesso menu o sulla stessa barra degli strumenti.

- I menu vengono in genere visualizzati come stringhe di una sola parola raggruppate su una riga nella parte superiore dell'ambiente di sviluppo integrato (IDE, Integrated Development Environment) o in una finestra degli strumenti. I menu possono essere visualizzati anche come risultato di un evento di clic con il pulsante destro del mouse e in tal caso vengono definiti menu di scelta rapida. Quando si fa clic su di essi, i menu si espandono per visualizzare uno o più comandi. Facendo clic sui comandi è possibile eseguire attività oppure aprire sottomenu che contengono altri comandi. Alcuni nomi di menu noti sono **file**, **modifica**, **Visualizza** e **finestra**. Per altre informazioni, vedere [estendere menu e comandi](../../extensibility/extending-menus-and-commands.md).

- Le barre degli strumenti sono in genere righe di pulsanti e altri controlli, ad esempio caselle combinate, caselle di riepilogo, caselle di testo e controller di menu. Tutti i controlli delle barre degli strumenti sono associati a comandi. Quando si fa clic su un pulsante della barra degli strumenti, viene attivato il comando associato. I pulsanti della barra degli strumenti hanno in genere icone che suggeriscono i comandi sottostanti, ad esempio una stampante per un comando Stampa. In un controllo elenco a discesa, ogni elemento nell'elenco è associato a un comando diverso. Un controller di menu è un oggetto ibrido in cui un lato del controllo è un pulsante della barra degli strumenti e l'altro lato è una freccia rivolta verso il basso che visualizza altri comandi quando si fa clic su di essa. Per ulteriori informazioni, vedere [aggiungere un controller di menu a una barra degli strumenti](../../extensibility/adding-a-menu-controller-to-a-toolbar.md).

- Quando si crea un comando, è anche necessario creare un gestore eventi per esso. Il gestore eventi determina quando il comando è visibile o abilitato, consente di modificarne il testo e garantisce che il comando risponda in modo appropriato ("routing") quando attivato. Nella maggior parte dei casi, l'IDE gestisce i comandi usando l'interfaccia <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>. I comandi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] eseguono il routing in modo gerarchico, a partire dal contesto del comando più interno, in base alla selezione locale, e procedendo verso il contesto più esterno, in base alla selezione globale. I comandi aggiunti al menu principale sono immediatamente disponibili per lo scripting. Per altre informazioni, vedere [oggetti MenuCommand e OleMenuCommands](/previous-versions/visualstudio/visual-studio-2015/misc/menucommands-vs-olemenucommands?preserve-view=true&view=vs-2015) e [oggetti Context di selezione](../../extensibility/internals/selection-context-objects.md).

  Per definire nuovi menu e barre degli strumenti, è necessario descriverli in un file della tabella comandi di Visual Studio (con *estensione vsct*). Il modello di pacchetto di Visual Studio crea automaticamente questo file, insieme agli elementi necessari per supportare qualsiasi comando, barra degli strumenti ed editor selezionato nel modello. In alternativa, è possibile scrivere il proprio file con *estensione vsct* usando il XML schema descritto di seguito: [vsct XML Schema Reference](../../extensibility/vsct-xml-schema-reference.md).

  Per ulteriori informazioni sull'utilizzo dei file con *estensione vsct* , vedere [file della tabella dei comandi di Visual Studio (con estensione vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

  Negli argomenti di questa sezione viene illustrato come funzionano i comandi, i menu e le barre degli strumenti in VSPackage.

## <a name="in-this-section"></a>Contenuto della sezione
- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Descrizione dettagliata della specifica del formato della tabella dei comandi.

- [File della tabella dei comandi di Visual Studio (con estensione vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

 Descrive una sintassi e un compilatore basati su XML per le tabelle dei comandi.

- [Posizionamento predefinito di comandi, gruppi e barre degli strumenti](../../extensibility/internals/default-command-group-and-toolbar-placement.md)

 Vengono descritti i comandi, i gruppi, i menu e le barre degli strumenti predefiniti.

- [Comandi, menu e gruppi definiti dall'IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)

 Specifica i menu, i comandi e i gruppi di comandi predefiniti che è possibile utilizzare nell' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

- [Progettazione comandi](../../extensibility/internals/command-design.md)

 Viene illustrato come progettare i comandi.

- [Ottimizza comandi menu e barra degli strumenti](../../extensibility/internals/optimizing-menu-and-toolbar-commands.md)

 Fornisce le linee guida per i comandi.

- [Rendere disponibili i comandi](../../extensibility/internals/making-commands-available.md)

 Viene illustrato come rendere disponibili i comandi per Visual Studio.

- [Comandi e menu che usano assembly di interoperabilità](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)

 Viene illustrato come implementare i comandi che utilizzano assembly di interoperabilità.

## <a name="related-sections"></a>Sezioni correlate
- [Routing di comandi nei pacchetti VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)

 Illustra il routing del comando nei pacchetti VSPackage.