---
title: Iniziare a sviluppare estensioni di Visual Studio | Microsoft Docs
ms.date: 09/18/2017
ms.topic: conceptual
helpviewer_keywords:
- getting started, Visual Studio integration
- Visual Studio, integration
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ffee39765d28306509ebe3a2ba30e8fabb79cf80
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55042777"
---
# <a name="starting-to-develop-visual-studio-extensions"></a>Iniziare a sviluppare estensioni di Visual Studio

Se non hai mai scritto un'estensione di Visual Studio prima di, è necessario probabilmente alcune delle domande. Ne sono elencati alcune delle cause più comuni di seguito. Se le informazioni che si sta cercando non viene visualizzata, usare i pulsanti di commenti e suggerimenti (**questa pagina è stata utile?** nella parte inferiore della schermata) per richiedere che si desidera.

> [!NOTE]
> Questo articolo si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [estensione di Visual Studio per Mac](/visualstudio/mac/extending-visual-studio-mac).

## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>Il software necessario per lo sviluppo di estensioni di Visual Studio?

È necessario installare Visual Studio SDK oltre a Visual Studio per sviluppare estensioni di Visual Studio. È possibile installare Visual Studio SDK come parte del programma di installazione regolare, oppure è possibile installarlo in un secondo momento. Per altre informazioni sull'installazione di Visual Studio SDK, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>Quali tipi di operazioni può fare con le estensioni di Visual Studio?

Il cielo è il limite se si desidera immaginando i modi in diverse estensioni di Visual Studio. Naturalmente, la maggior parte delle estensioni avere qualcosa a che fare con la scrittura di codice, ma che non deve necessariamente essere il caso. Di seguito sono riportati alcuni esempi dei tipi di estensioni che è possibile compilare:

- Supporto per lingue che non sono inclusi in Visual Studio, con la colorazione della sintassi, IntelliSense e il supporto del compilatore ed eseguire il debug

- Strumenti di produttività che estendono i principali IDE esperienza con altri modelli, le conversazioni di refactoring, nuovo codice o finestre degli strumenti

- Finestre di progettazione specifici del dominio per scenari come il supporto di progettazione o cloud di dati

Per esempi di estensioni, consultare il [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Molte estensioni sono open source e il Marketplace include i collegamenti per il repository di GitHub.

## <a name="which-visual-studio-features-can-i-extend"></a>Le funzionalità di Visual Studio è possibile estendere?

In teoria, è possibile estendere solo una parte di Visual Studio: menu, barre degli strumenti, comandi, windows, soluzioni, progetti, editor e così via.

In pratica, si è constatato che le funzionalità la maggior parte degli utenti che vogliono estendere sono i comandi, menu e barre degli strumenti, windows, IntelliSense e progetti. Ecco i collegamenti alle sezioni pertinenti:

-   [Estensione di menu e comandi](../extensibility/extending-menus-and-commands.md): aggiungere i propri elementi per Visual Studio menu e barre degli strumenti. È possibile usare tali per avviare le proprie applicazioni di supporto esterno o nuove funzionalità di Visual Studio. È inoltre possibile fornire collegamenti personalizzati per le voci di menu.

-   [Estensione e personalizzazione di Windows lo strumento](../extensibility/extending-and-customizing-tool-windows.md): estendere finestre degli strumenti esistenti o creare finestre degli strumenti. Ad esempio, è possibile aggiungere nuove proprietà per il **proprietà**, oppure è possibile creare una nuova finestra degli strumenti per aggiungere ulteriori funzionalità.

-   [Editor e le estensioni del servizio di linguaggio](../extensibility/editor-and-language-service-extensions.md): aggiungere le proprie personalizzazioni gli elementi IntelliSense forniti per le lingue di Visual Studio o creare il supporto per nuovi linguaggi di programmazione. È possibile creare nuovi completamenti di istruzione, suggerimenti e le descrizioni comandi informazioni rapide di nuovo. Con le lampadine, è possibile aggiungere i suggerimenti di refactoring e correzioni del codice per supportare nuovi linguaggi di programmazione.

-   [Estensione dei progetti](../extensibility/extending-projects.md)

-   [Estensione di opzioni e impostazioni utente](../extensibility/extending-user-settings-and-options.md)

-   [Estensione delle proprietà e della finestra Proprietà](../extensibility/extending-properties-and-the-property-window.md)

-   [Estensione di altre parti di Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)

-   [Visual Studio Isolated Shell](/visualstudio/extensibility/shell/visual-studio-isolated-shell)

##  <a name="BKMK_ProjectTemplate"></a> Quali modelli di progetto forniti da VSSDK?
 I due tipi principali di estensioni sono VSPackage ed estensioni MEF. In genere, le estensioni VSPackage vengono utilizzate per le estensioni che utilizzano o estendono i comandi, finestre degli strumenti e progetti. Le estensioni MEF vengono utilizzate per estendere o personalizzare l'editor di Visual Studio.

 Le estensioni di Visual C# e Visual Basic, VSSDK fornisce un modello di progetto VSIX vuoto che è possibile utilizzare insieme i nuovi modelli di elementi che creano comandi di menu, finestre degli strumenti e le estensioni dell'editor. È anche possibile usare questo modello per modelli di progetto di pacchetto, frammenti di codice e altri elementi per la distribuzione ad altri utenti.

 Per C++, la creazione guidata pacchetto VSPackage fornisce il codice per aggiungere i comandi di menu, finestre degli strumenti ed editor personalizzati.

 Il modello della Shell isolata viene utilizzato per creare un pacchetto di un'estensione in una versione di Visual Studio shell che è possibile personalizzare e distribuire il proprio. Gli argomenti seguenti illustrano come iniziare a usare ogni tipo di estensione:

-   Comandi di menu: [Creazione di un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md)

-   Finestre degli strumenti: [Creazione di un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md)

-   Estensioni dell'editor: [Creazione di un'estensione con un modello di elemento dell'editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)

-   Pacchetti VSPackage di base: [Creazione di un'estensione con un pacchetto VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)

-   Modello di progetto VSIX: [Introduzione al modello di progetto VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)

## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>Come si ottiene l'estensione per l'aspetto di Visual Studio?
 Ottenere suggerimenti straordinari per progettazione dell'interfaccia utente per l'estensione nella [Visual Studio User Experience Guidelines](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

## <a name="where-can-i-find-examples-of-vssdk-code"></a>Dove trovare esempi di VSSDK codice?
 Ogni collegamento indicato nella sezione precedente sono incluse le procedure dettagliate che illustrano come implementare le funzionalità specifiche. È anche possibile trovare open source in GitHub all'indirizzo esempi di VSSDK [esempi di Visual Studio](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="how-can-i-distribute-my-extension"></a>Come è possibile distribuire l'estensione?
 È possibile installare l'estensione in un altro computer o inviarlo ad altri utenti come file con estensione VSIX, che si installa facendovi doppio clic. È possibile trovare ulteriori informazioni sui pacchetti VSIX [spedizione di estensioni di Visual Studio](../extensibility/shipping-visual-studio-extensions.md).

 È anche possibile pubblicare l'estensione in Visual Studio Marketplace, che rende visibile a un numero elevato di clienti di Visual Studio. Per un esempio di creazione del pacchetto di un'estensione nel Marketplace, vedere [procedura dettagliata: Pubblicazione di un'estensione di Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md). Per altre informazioni su cosa occorre fare per pubblicare nel Marketplace, vedere [prodotti ed estensioni per Visual Studio](/azure/devops/extend/overview?view=vsts).

## <a name="see-also"></a>Vedere anche

- [Estensione di Visual Studio per Mac](/visualstudio/mac/extending-visual-studio-mac)