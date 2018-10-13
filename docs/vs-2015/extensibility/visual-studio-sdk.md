---
title: Visual Studio SDK | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
caps.latest.revision: 57
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 930eab1a9356cf16a8615015742af30aa338bd21
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49260200"
---
# <a name="visual-studio-sdk"></a>Visual Studio SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio SDK consente di estendere le funzionalità di Visual Studio o integrare le nuove funzionalità in Visual Studio. È possibile distribuire le estensioni ad altri utenti, oltre che per Visual Studio Gallery. Di seguito sono illustrati alcuni dei modi in cui si può estendere Visual Studio:  
  
-   Aggiungere i comandi, pulsanti, menu e altri elementi dell'interfaccia utente per l'IDE  
  
-   Aggiungere finestre degli strumenti per la nuova funzionalità  
  
-   Estensione di IntelliSense per una determinata lingua, o fornire IntelliSense per nuovi linguaggi di programmazione  
  
-   Usare le lampadine per fornire suggerimenti e i suggerimenti che consentono agli sviluppatori di scrivere codice migliore  
  
-   Abilitare il supporto per una nuova lingua  
  
-   Aggiungere un tipo di progetto personalizzati  
  
-   Raggiungi milioni di sviluppatori tramite Visual Studio Gallery  
  
 Se non hai mai scritto un'estensione di Visual Studio prima di, è necessario trovare altre informazioni su queste funzionalità e alla [iniziando a sviluppare estensioni di Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).  
  
## <a name="installing-the-visual-studio-sdk"></a>Installazione di Visual Studio SDK  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="whats-new-in-the-visual-studio-2015-sdk"></a>Novità in Visual Studio 2015 SDK  
 Visual Studio SDK contiene alcune nuove funzionalità, tra cui le lampadine e nuovi elementi di progetto che consentono di creare comandi di menu, finestre degli strumenti e le estensioni di editor utilizzando un pacchetto VSIX. Per altre informazioni, vedere [What ' s New in Visual Studio 2015 SDK](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md).  
  
## <a name="visual-studio-user-experience-guidelines"></a>Linee guida sull'esperienza utente di Visual Studio  
 Ottenere suggerimenti straordinari per progettazione dell'interfaccia utente per l'estensione nella [Visual Studio User Experience Guidelines](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
 È anche possibile imparare a migliorare l'aspetto in dispositivi con DPI elevato con l'estensione nostri [indirizzamento problemi DPI](../extensibility/addressing-dpi-issues2.md) argomento.  
  
 Sfruttare il [servizio immagini e il catalogo](../extensibility/image-service-and-catalog.md) per la gestione delle immagini ottimale e il supporto per valori DPI alti e temi.  
  
## <a name="finding-and-installing-existing-visual-studio-extensions"></a>Ricerca e l'installazione di estensioni di Visual Studio esistente  
 È possibile trovare le estensioni di Visual Studio nel **estensioni e aggiornamenti** nella finestra di dialogo il **Tools** menu. Per altre informazioni, vedere [Ricerca e uso delle estensioni di Visual Studio](../ide/finding-and-using-visual-studio-extensions.md). È anche possibile trovare estensioni nel [Visual Studio Gallery](https://visualstudiogallery.msdn.microsoft.com/)  
  
## <a name="visual-studio-sdk-reference"></a>Informazioni di riferimento su Visual Studio SDK  
 È possibile trovare il riferimento API di Visual Studio SDK alla [riferimenti di Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md).  
  
## <a name="visual-studio-sdk-samples"></a>Esempi di Visual Studio SDK  
 È possibile trovare esempi open source di estensioni di Visual Studio SDK in GitHub all'indirizzo [esempi di Visual Studio](https://aka.ms/vs2015sdksamples). Questo repository GitHub contiene alcuni esempi che illustrano diverse funzionalità estensibile in Visual Studio.  
  
## <a name="other-visual-studio-sdk-resources"></a>Altre risorse di Visual Studio SDK  
 Se si hanno domande sulle VSSDK o si desidera condividere le proprie esperienze di sviluppo di estensioni, è possibile usare la [forum sull'estendibilità di Visual Studio](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) o nella [tale Group Chat](https://gitter.im/Microsoft/extendvs).  
  
 È possibile trovare altre informazioni, il [VSX Arcana blog](http://blogs.msdn.com/b/vsx/) e un numero di blog scritti dai Microsoft MVPs:  
  
-   [Estensioni preferite di Visual Studio](http://geekswithblogs.net/sdorman/archive/2014/10/05/favorite-visual-studio-extensions.aspx)  
  
-   [Estendibilità di Visual Studio](http://www.visualstudioextensibility.com/overview/vs/)  
  
-   [Estensione di Visual Studio](http://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un'estensione con un comando di Menu](../extensibility/creating-an-extension-with-a-menu-command.md)   
 [Procedura: eseguire la migrazione di progetti di estendibilità di Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md)   
 [Domande frequenti: Conversione di componenti aggiuntivi in estensioni VSPackage](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md)   
 [Gestione di più thread in codice gestito](../extensibility/managing-multiple-threads-in-managed-code.md)   
 [Estensione di menu e comandi](../extensibility/extending-menus-and-commands.md)   
 [Aggiunta di comandi alle barre degli strumenti](../extensibility/adding-commands-to-toolbars.md)   
 [Estensione e personalizzazione di Windows degli strumenti](../extensibility/extending-and-customizing-tool-windows.md)   
 [Editor e le estensioni del servizio di linguaggio](../extensibility/editor-and-language-service-extensions.md)   
 [Estensione di progetti](../extensibility/extending-projects.md)   
 [Opzioni e impostazioni di estensione utente](../extensibility/extending-user-settings-and-options.md)   
 [Creazione progetto personalizzato e i modelli di elemento](../extensibility/creating-custom-project-and-item-templates.md)   
 [Estensione delle proprietà e la finestra delle proprietà](../extensibility/extending-properties-and-the-property-window.md)   
 [Estensione di altre parti di Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Uso e fornitura di servizi](../extensibility/using-and-providing-services.md)   
 [Estensione di servizi connessi](../extensibility/extending-connected-services.md)   
 [Gestione dei pacchetti VSPackage](../extensibility/managing-vspackages.md)   
 [Visual Studio Isolated Shell](../extensibility/visual-studio-isolated-shell.md)   
 [Estensioni di Visual Studio di spedizione](../extensibility/shipping-visual-studio-extensions.md)   
 [All'interno di Visual Studio SDK](../extensibility/internals/inside-the-visual-studio-sdk.md)   
 [Supporto per Visual Studio SDK](../extensibility/support-for-the-visual-studio-sdk.md)   
 [Archivio](../extensibility/archive.md)   
 [Riferimenti su Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md)

