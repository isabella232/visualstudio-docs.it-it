---
title: Avvio dello sviluppo Visual Studio estensioni | Microsoft Docs
description: Informazioni su alcune domande comuni che potrebbero essere poste la prima volta che si inizia a scrivere un'Visual Studio personalizzata.
ms.custom: SEO-VS-2020
ms.date: 09/18/2017
ms.topic: conceptual
helpviewer_keywords:
- getting started, Visual Studio integration
- Visual Studio, integration
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 260ae4b71d7eb7bed3ac97faa3d0ccf90665f90a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122049454"
---
# <a name="starting-to-develop-visual-studio-extensions"></a>Sviluppo di estensioni di Visual Studio

Se non è mai stata scritta un'estensione Visual Studio, probabilmente si hanno alcune domande. Di seguito sono elencati alcuni dei più comuni. Se non vengono visualizzate le informazioni desiderate, usare i pulsanti di feedback (Questa pagina è **utile?** in alto a destra nella schermata) per chiedere cosa si vuole.

> [!NOTE]
> Questo articolo si applica Visual Studio in Windows. Per Visual Studio per Mac, vedere [Estensione Visual Studio per Mac](/visualstudio/mac/extending-visual-studio-mac). Per Visual Studio Code, vedere API [Visual Studio Code di estensione](https://code.visualstudio.com/api).

## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>Quale software è necessario per sviluppare Visual Studio estensioni?

È necessario installare Visual Studio SDK oltre a Visual Studio per sviluppare Visual Studio estensioni. È possibile installare l'SDK Visual Studio come parte della normale installazione oppure è possibile installarlo in un secondo momento. Per altre informazioni sull'installazione di Visual Studio SDK, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>Quali tipi di operazioni è possibile eseguire con Visual Studio estensioni?

Il cielo è il limite quando si tratta di immaginare estensioni Visual Studio diverse. Naturalmente, la maggior parte delle estensioni ha a che fare con la scrittura di codice, ma questo non è necessario. Ecco alcuni esempi dei tipi di estensioni che è possibile compilare:

- Supporto per i linguaggi non inclusi in Visual Studio, con colorazione della sintassi, IntelliSense e supporto del compilatore e del debug

- Strumenti di produttività che estendono l'esperienza IDE di base con modelli aggiuntivi, refactoring del codice, nuove finestre di dialogo o finestre degli strumenti

- Finestre di progettazione specifiche del dominio per scenari come la progettazione dei dati o il supporto cloud

Per esempi di estensioni, vedere l'Visual Studio [Marketplace.](https://marketplace.visualstudio.com/vs) Molte estensioni sono open source e il Marketplace include collegamenti al relativo GitHub locale.

## <a name="which-visual-studio-features-can-i-extend"></a>Quali Visual Studio è possibile estendere?

In teoria, è possibile estendere qualsiasi parte di Visual Studio: menu, barre degli strumenti, comandi, finestre, soluzioni, progetti, editor e così via.

In pratica, è stato rilevato che le funzionalità che la maggior parte degli utenti vuole estendere sono comandi, menu e barre degli strumenti, finestre, IntelliSense e progetti. Di seguito sono riportati i collegamenti alle sezioni pertinenti:

- [Estensione di menu e comandi:](../extensibility/extending-menus-and-commands.md)consente di aggiungere elementi personalizzati Visual Studio menu e barre degli strumenti. È possibile usarli per avviare nuove funzionalità Visual Studio o applicazioni helper esterne. È anche possibile fornire collegamenti personalizzati per le voci di menu.

- [Estensione e personalizzazione degli strumenti Windows](../extensibility/extending-and-customizing-tool-windows.md): estendere le finestre degli strumenti esistenti o creare finestre degli strumenti. Ad esempio, è possibile aggiungere nuove proprietà a **Proprietà** oppure creare una nuova finestra degli strumenti per aggiungere altre funzionalità.

- [Estensioni dell'editor](../extensibility/editor-and-language-service-extensions.md)e del servizio di linguaggio: aggiungere personalizzazioni alle funzionalità IntelliSense fornite per Visual Studio linguaggi di programmazione o creare il supporto per nuovi linguaggi di programmazione. È possibile creare nuovi completamenti di istruzioni, suggerimenti e nuove descrizioni comando di Informazioni rapide. Con le lampadine è possibile aggiungere suggerimenti di refactoring e correzioni del codice per supportare nuovi linguaggi di programmazione.

- [Estensione dei progetti](../extensibility/extending-projects.md)

- [Estensione di opzioni e impostazioni utente](../extensibility/extending-user-settings-and-options.md)

- [Estensione delle proprietà e della finestra Proprietà](../extensibility/extending-properties-and-the-property-window.md)

- [Estensione di altre parti di Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)

- [Visual Studio Isolated Shell](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

## <a name="what-project-templates-are-provided-by-the-vssdk"></a><a name="BKMK_ProjectTemplate"></a> Quali modelli di progetto vengono forniti da VSSDK?
 I due tipi principali di estensioni sono i pacchetti VSPackage e le estensioni MEF. In generale, le estensioni VSPackage vengono usate per le estensioni che usano o estendono comandi, finestre degli strumenti e progetti. Le estensioni MEF vengono usate per estendere o personalizzare l Visual Studio editor.

 Per le estensioni Visual C# e Visual Basic, VSSDK fornisce un modello di progetto VSIX vuoto che è possibile usare insieme ai nuovi modelli di elemento che creano comandi di menu, finestre degli strumenti ed estensioni dell'editor. È anche possibile usare questo modello per creare un pacchetto di modelli di progetto, frammenti di codice e altri artefatti per la distribuzione ad altri utenti.

 Per C++, la procedura guidata VSPackage fornisce il codice per aggiungere comandi di menu, finestre degli strumenti ed editor personalizzati.

 Il modello Isolated Shell viene usato per creare un pacchetto di un'estensione in una versione della shell Visual Studio che è possibile modificare e distribuire come propria. Gli argomenti seguenti illustrano come iniziare a usare ogni tipo di estensione:

- Comandi di menu: [Creazione di un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md)

- Finestre degli strumenti: [creazione di un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md)

- Estensioni dell'editor: [creazione di un'estensione con un modello di elemento dell'editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)

- Pacchetti VSPackage di base: [creazione di un'estensione con un PACCHETTO VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)

- Modello di progetto VSIX: [Attività iniziali con il modello Project VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)

## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>Ricerca per categorie l'estensione sarà simile Visual Studio?
 Per suggerimenti utili per la progettazione dell'interfaccia utente per l'estensione, Visual Studio [linee guida sull'esperienza utente.](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)

## <a name="where-can-i-find-examples-of-vssdk-code"></a>Dove è possibile trovare esempi di codice VSSDK?
 Ognuno dei collegamenti elencati nella sezione precedente include procedure dettagliate che illustrano come implementare funzionalità specifiche. È anche possibile trovare esempi open source VSSDK in GitHub in Visual Studio Samples ( Esempi di VSSDK). [](https://github.com/Microsoft/VSSDK-Extensibility-Samples)

## <a name="how-can-i-distribute-my-extension"></a>Come si distribuisce l'estensione?
 È possibile installare l'estensione in un altro computer o inviarla agli amici come file con estensione vsix, che è possibile installare facendo doppio clic su di essa. Per altre informazioni sui pacchetti VSIX, vedere [Shipping Visual Studio Extensions.](../extensibility/shipping-visual-studio-extensions.md)

 È anche possibile pubblicare l'estensione in Visual Studio Marketplace, che la rende visibile a un numero elevato di Visual Studio clienti. Per un esempio di creazione del pacchetto di un'estensione nel Marketplace, vedere Procedura dettagliata: Pubblicazione di [un'estensione Visual Studio.](../extensibility/walkthrough-publishing-a-visual-studio-extension.md) Per altre informazioni sulle funzionalità da eseguire per pubblicare nel Marketplace, vedere [Prodotti ed](/azure/devops/extend/overview?view=vsts&preserve-view=true)estensioni per Visual Studio .

## <a name="see-also"></a>Vedi anche

- [Estensione di Visual Studio per Mac](/visualstudio/mac/extending-visual-studio-mac)
- [Estensione Visual Studio Code](https://code.visualstudio.com/api)