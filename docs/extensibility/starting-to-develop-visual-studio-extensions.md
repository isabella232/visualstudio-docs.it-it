---
title: Avvio dello sviluppo di estensioni di Visual Studio Documenti Microsoft
ms.date: 09/18/2017
ms.topic: conceptual
helpviewer_keywords:
- getting started, Visual Studio integration
- Visual Studio, integration
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 744475e61458f7b91ce08fba4d17046df36f5558
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699733"
---
# <a name="starting-to-develop-visual-studio-extensions"></a>Sviluppo di estensioni di Visual Studio

Se non hai mai scritto un'estensione di Visual Studio prima, probabilmente hai alcune domande. Abbiamo elencato alcuni dei più comuni qui. Se non vedi le informazioni che stai cercando, usa i pulsanti di feedback **(Questa pagina è stata utile?** nella parte inferiore dello schermo) per chiedere quello che vuoi.

> [!NOTE]
> Questo articolo si applica a Visual Studio in Windows.This article applies to Visual Studio on Windows. Per Visual Studio per Mac, vedere [Estensione di Visual Studio per Mac](/visualstudio/mac/extending-visual-studio-mac). Per il codice di Visual Studio, vedere [Visual Studio Code Extension API](https://code.visualstudio.com/api).

## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>Quale software è necessario per sviluppare le estensioni di Visual Studio?

È necessario installare Visual Studio SDK oltre a Visual Studio per sviluppare le estensioni di Visual Studio.You need to install the Visual Studio SDK in addition to Visual Studio in order to develop Visual Studio extensions. È possibile installare Visual Studio SDK come parte dell'installazione normale oppure installarlo in un secondo momento. Per ulteriori informazioni sull'installazione di Visual Studio SDK, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>Quali tipi di operazioni è possibile eseguire con le estensioni di Visual Studio?

Il cielo è il limite quando si tratta di immaginare diverse estensioni di Visual Studio. Naturalmente, la maggior parte delle estensioni hanno qualcosa a che fare con la scrittura di codice, ma che non deve essere il caso. Ecco alcuni esempi dei tipi di estensioni che puoi compilare:

- Supporto per linguaggi non inclusi in Visual Studio, con colorazione della sintassi, IntelliSense e supporto per compilatori e debug

- Strumenti di produttività che estendono l'esperienza di base dell'IDE con modelli aggiuntivi, refactoring del codice, nuove finestre di dialogo o finestre degli strumenti

- Finestre di progettazione specifiche del dominio per scenari come la progettazione dei dati o il supporto cloudDomain-specific designers for scenarios like data design or cloud support

Per esempi di estensioni, vedere [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Molte estensioni sono open source e Marketplace include collegamenti al repository GitHub.Many extensions are open source, and the Marketplace includes links to their GitHub repo.

## <a name="which-visual-studio-features-can-i-extend"></a>Quali funzionalità di Visual Studio è possibile estendere?

In teoria, è possibile estendere praticamente qualsiasi parte di Visual Studio: menu, barre degli strumenti, comandi, finestre, soluzioni, progetti, editor e così via.

In pratica, abbiamo scoperto che le funzionalità che la maggior parte delle persone vogliono estendere sono comandi, menu e barre degli strumenti, finestre, IntelliSense e progetti. Di seguito sono riportati i collegamenti alle sezioni pertinenti:

- [Estensione di menu e comandi](../extensibility/extending-menus-and-commands.md): aggiungere elementi personalizzati ai menu e alle barre degli strumenti di Visual Studio. È possibile utilizzarli per avviare nuove funzionalità di Visual Studio o le proprie applicazioni helper esterne. È inoltre possibile fornire scelte rapide personalizzate per le voci di menu.

- [Estensione e personalizzazione delle finestre degli strumenti](../extensibility/extending-and-customizing-tool-windows.md): estendere le finestre degli strumenti esistenti o creare finestre degli strumenti personalizzate. Ad esempio, è possibile aggiungere nuove proprietà alle **proprietà**oppure creare una nuova finestra degli strumenti per aggiungere funzionalità aggiuntive.

- [Editor ed estensioni del servizio](../extensibility/editor-and-language-service-extensions.md)di linguaggio : aggiungere le proprie personalizzazioni per IntelliSense fornito per i linguaggi di Visual Studio o creare il supporto per nuovi linguaggi di programmazione. È possibile creare nuovi completamenti di istruzioni, suggerimenti e nuove descrizioni comandi di informazioni rapide. Con le lampadine, è possibile aggiungere suggerimenti di refactoring e correzioni del codice per supportare nuovi linguaggi di programmazione.

- [Estensione dei progetti](../extensibility/extending-projects.md)

- [Estensione di opzioni e impostazioni utente](../extensibility/extending-user-settings-and-options.md)

- [Estensione delle proprietà e della finestra Proprietà](../extensibility/extending-properties-and-the-property-window.md)

- [Estensione di altre parti di Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)

- [Visual Studio Isolated Shell](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

## <a name="what-project-templates-are-provided-by-the-vssdk"></a><a name="BKMK_ProjectTemplate"></a>Quali modelli di progetto vengono forniti da VSSDK?
 I due tipi principali di estensioni sono VSPackage ed estensioni MEF. In generale, le estensioni VSPackage vengono usate per le estensioni che usano o estendono comandi, finestre degli strumenti e progetti. Le estensioni MEF vengono utilizzate per estendere o personalizzare l'editor di Visual Studio.

 Per le estensioni di Visual C e Visual Basic, VSSDK fornisce un modello di progetto VSIX vuoto che è possibile utilizzare con i nuovi modelli di elemento che creano comandi di menu, finestre degli strumenti ed estensioni dell'editor. È inoltre possibile utilizzare questo modello per creare pacchetti di modelli di progetto, frammenti di codice e altri elementi per la distribuzione ad altri utenti.

 Per il linguaggio C, la procedura guidata VSPackage fornisce il codice per aggiungere comandi di menu, finestre degli strumenti ed editor personalizzati.

 Il modello Isolated Shell viene utilizzato per creare un pacchetto di un'estensione in una versione della shell di Visual Studio che è possibile personalizzare e distribuire come propria. Negli argomenti seguenti viene illustrato come iniziare a usare ogni tipo di estensione:

- Comandi di [menu: Creazione di un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md)

- Finestre degli strumenti: [Creazione di un'estensione con una finestra degli](../extensibility/creating-an-extension-with-a-tool-window.md) strumenti

- Estensioni [dell'editor: creazione di un'estensione con un modello di elemento dell'editorEditor extensions: Creating an Extension with an Editor Item Template](../extensibility/creating-an-extension-with-an-editor-item-template.md)

- VSPackage di base: [creazione di un'estensione con un pacchetto VSPackageBasic](../extensibility/creating-an-extension-with-a-vspackage.md) VSPackages: Creating an Extension with a VSPackage

- Modello di progetto VSIX: Introduzione al modello di [progetto VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)

## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>Come faccio a ottenere la mia estensione per apparire come Visual Studio?
 Ottieni ottimi suggerimenti per la progettazione dell'interfaccia utente per l'estensione in Linee guida per l'esperienza utente di [Visual Studio.](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)

## <a name="where-can-i-find-examples-of-vssdk-code"></a>Dove posso trovare esempi di codice VSSDK?
 Ognuno dei collegamenti elencati nella sezione precedente include procedure dettagliate che illustrano come implementare funzionalità specifiche. È inoltre possibile trovare esempi vsSDK open source in GitHub in Esempi di [Visual Studio](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="how-can-i-distribute-my-extension"></a>Come posso distribuire la mia estensione?
 Puoi installare l'estensione su un altro computer o inviarla ai tuoi amici come file .vsix, che installi facendo doppio clic su di esso. Per ulteriori informazioni sui pacchetti VSIX, fare clic su [Shipping Visual Studio Extensions](../extensibility/shipping-visual-studio-extensions.md).

 È anche possibile pubblicare l'estensione in Visual Studio Marketplace, che la rende visibile a un numero elevato di clienti di Visual Studio.You can also publish your extension on the Visual Studio Marketplace, which makes it visible to large numbers of Visual Studio customers. Per un esempio di creazione del pacchetto di un'estensione nel Marketplace, vedere [Procedura dettagliata: pubblicazione di un'estensione](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)di Visual Studio . Per ulteriori informazioni sulle operazioni da eseguire per pubblicare nel Marketplace, vedere [Prodotti ed estensioni per Visual Studio](/azure/devops/extend/overview?view=vsts).

## <a name="see-also"></a>Vedere anche

- [Estensione di Visual Studio per Mac](/visualstudio/mac/extending-visual-studio-mac)
- [Estensione del codice di Visual StudioExtending Visual Studio Code](https://code.visualstudio.com/api)
