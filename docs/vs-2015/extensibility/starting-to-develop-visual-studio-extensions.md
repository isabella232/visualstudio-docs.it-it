---
title: Avvio dello sviluppo di estensioni | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- getting started, Visual Studio integration
- Visual Studio, integration
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d62a4c6cc45681fe6a66ae57df2e1da1d1cc12e0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850589"
---
# <a name="starting-to-develop-visual-studio-extensions"></a>Sviluppo di estensioni di Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se non è mai stata scritta un'estensione di Visual Studio, è probabile che si verifichino alcune domande. Qui sono elencate alcune delle più comuni. Se non vengono visualizzate le informazioni che si stanno cercando, usare i pulsanti commenti e suggerimenti (**Questa pagina è stata utile?** nella parte inferiore della schermata) per chiedere cosa si vuole.

## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>Quale software è necessario per sviluppare le estensioni di Visual Studio?
 Per lo sviluppo di estensioni di Visual Studio, è necessario installare Visual Studio 2015 SDK, oltre a Visual Studio 2015.   È possibile installare Visual Studio 2015 SDK come parte dell'installazione normale oppure è possibile installarlo in un secondo momento. Per ulteriori informazioni sull'installazione di Visual Studio SDK, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>Quali tipi di operazioni è possibile eseguire con le estensioni di Visual Studio?
 Il cielo è il limite quando si tratta di immaginare diverse estensioni di Visual Studio. Naturalmente, la maggior parte delle estensioni ha qualcosa a che fare con la scrittura di codice, ma ciò non è necessario. Di seguito sono riportati alcuni esempi dei tipi di estensioni che è possibile compilare:

- Supporto per lingue non incluse in Visual Studio, con colorazione della sintassi, IntelliSense e supporto del compilatore e del debug

- Strumenti di produttività che estendono l'esperienza IDE di base con modelli aggiuntivi, refactoring del codice, nuovi dialoghi o finestre degli strumenti

- Finestre di progettazione specifiche del dominio per scenari come la progettazione dei dati o il supporto Cloud

  Per esempi di estensioni, vedere la [Visual Studio Marketplace](https://marketplace.visualstudio.com/). È anche possibile esaminare le [estensioni open source di Visual Studio](https://github.com/Microsoft/extendvs/blob/master/CommunityExtensions.md).

## <a name="which-visual-studio-features-can-i-extend"></a>Quali funzionalità di Visual Studio è possibile estendere?
 In teoria, è possibile estendere praticamente qualsiasi parte di Visual Studio: menu, barre degli strumenti, comandi, finestre, soluzioni, progetti, editor e così via.

 In pratica, è stato rilevato che le funzionalità che la maggior parte degli utenti vogliono estendere sono i comandi, i menu e le barre degli strumenti, Windows, IntelliSense e i progetti. Ecco i collegamenti alle sezioni pertinenti:

- [Estensione di menu e comandi](../extensibility/extending-menus-and-commands.md): aggiungere elementi personalizzati ai menu e alle barre degli strumenti di Visual Studio. È possibile usarli per avviare nuove funzionalità di Visual Studio o le proprie applicazioni Helper esterne. È anche possibile specificare collegamenti personalizzati per le voci di menu.

- [Estensione e personalizzazione delle finestre degli](../extensibility/extending-and-customizing-tool-windows.md)strumenti: estendere le finestre degli strumenti esistenti o creare le proprie finestre degli strumenti. Ad esempio, è possibile aggiungere nuove proprietà alle **Proprietà**oppure è possibile creare una nuova finestra degli strumenti per aggiungere ulteriori funzionalità.

- [Editor e Language Service Extensions](../extensibility/editor-and-language-service-extensions.md): aggiungere personalizzazioni personalizzate fornite da IntelliSense per i linguaggi di Visual Studio o creare supporto per i nuovi linguaggi di programmazione. È possibile creare nuovi completamenti di istruzioni, suggerimenti e nuove descrizioni comandi di informazioni rapide. Con le lampadine è possibile aggiungere suggerimenti per il refactoring e correzioni del codice per supportare i nuovi linguaggi di programmazione.

- [Estensione dei progetti](../extensibility/extending-projects.md)

- [Estensione di opzioni e impostazioni utente](../extensibility/extending-user-settings-and-options.md)

- [Estensione delle proprietà e della finestra Proprietà](../extensibility/extending-properties-and-the-property-window.md)

- [Estensione di altre parti di Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)

- [Visual Studio Isolated Shell](../extensibility/visual-studio-isolated-shell.md)

## <a name="what-project-templates-are-provided-by-the-vssdk"></a><a name="BKMK_ProjectTemplate"></a> Quali modelli di progetto sono forniti da VSSDK?
 I due tipi principali di estensioni sono VSPackage ed estensioni MEF. In generale, le estensioni VSPackage vengono usate per le estensioni che usano o estendono i comandi, le finestre degli strumenti e i progetti. Le estensioni MEF vengono usate per estendere o personalizzare l'editor di Visual Studio.

 Per le estensioni Visual C# ed Visual Basic, VSSDK fornisce un modello di progetto VSIX vuoto che è possibile usare insieme ai nuovi modelli di elemento che creano comandi di menu, finestre degli strumenti ed estensioni dell'editor. Per ulteriori informazioni, vedere Novità [di Visual Studio 2015 SDK](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md). È anche possibile usare questo modello per creare pacchetti di modelli di progetto, frammenti di codice e altri elementi da distribuire ad altri utenti.

 Per C++, la procedura guidata VSPackage fornisce il codice per aggiungere i comandi di menu, le finestre degli strumenti e gli editor personalizzati.

 Il modello di shell isolata viene usato per creare il pacchetto di un'estensione in una versione della shell di Visual Studio che è possibile personalizzare e distribuire in modo autonomo. Negli argomenti seguenti viene illustrato come iniziare a usare ogni tipo di estensione:

- Comandi di menu: [creazione di un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md)

- Finestre degli strumenti: [creazione di un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md)

- Estensioni dell'Editor: [creazione di un'estensione con un modello di elemento dell'editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)

- Pacchetti VSPackage di base: [creazione di un'estensione con un pacchetto VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)

- Modello di progetto VSIX: [Introduzione con il modello di progetto VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)

- Visual Studio Isolated Shell: [procedura dettagliata: creazione di un'applicazione shell isolata di base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)

## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>Ricerca per categorie ottenere un'estensione simile a Visual Studio?
 Suggerimenti utili per la progettazione dell'interfaccia utente per l'estensione nelle [linee guida sull'esperienza utente di Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

## <a name="where-can-i-find-examples-of-vssdk-code"></a>Dove è possibile trovare esempi di codice VSSDK?
 Ognuno dei collegamenti elencati nella sezione precedente include procedure dettagliate in cui viene illustrato come implementare funzionalità specifiche. È anche possibile trovare esempi Open Source di VSSDK su GitHub in [Visual Studio Samples](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="how-can-i-distribute-my-extension"></a>Come si distribuisce l'estensione?
 È possibile installare l'estensione in un altro computer o inviarla agli amici come file con estensione VSIX, che viene installato facendo doppio clic su di esso. Per ulteriori informazioni sui pacchetti VSIX, vedere la pagina relativa alle [estensioni di Visual Studio](../extensibility/shipping-visual-studio-extensions.md).

 È anche possibile pubblicare l'estensione in Visual Studio Gallery, rendendola visibile a un numero elevato di clienti di Visual Studio. Per un esempio di creazione del pacchetto di un'estensione per la raccolta, vedere [procedura dettagliata: pubblicazione di un'estensione di Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md). Per altre informazioni su ciò che è necessario fare per pubblicare nella raccolta, vedere [prodotti ed estensioni per Visual Studio](https://visualstudiogallery.msdn.microsoft.com/).
