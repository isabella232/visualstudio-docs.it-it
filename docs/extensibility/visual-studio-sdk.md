---
title: Visual Studio SDK | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6f8b5d7cd33f4466071b836d3438d6973f83fd8a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54969077"
---
# <a name="visual-studio-sdk"></a>Visual Studio SDK
Visual Studio SDK consente di estendere le funzionalità di Visual Studio o integrare le nuove funzionalità in Visual Studio. È possibile distribuire le estensioni ad altri utenti, oltre che per Visual Studio Marketplace. Di seguito sono illustrati alcuni dei modi in cui si può estendere Visual Studio:  
  
- Aggiungere i comandi, pulsanti, menu e altri elementi dell'interfaccia utente per l'IDE  
  
- Aggiungere finestre degli strumenti per la nuova funzionalità  
  
- Estensione di IntelliSense per una determinata lingua, o fornire IntelliSense per nuovi linguaggi di programmazione  
  
- Usare le lampadine per fornire suggerimenti e i suggerimenti che consentono agli sviluppatori di scrivere codice migliore  
  
- Abilitare il supporto per una nuova lingua  
  
- Aggiungere un tipo di progetto personalizzati  
  
- Raggiungi milioni di sviluppatori tramite Visual Studio Marketplace  
  
  Se non hai mai scritto un'estensione di Visual Studio prima di, è necessario trovare altre informazioni su queste funzionalità e alla [iniziando a sviluppare estensioni di Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).  
  
## <a name="install-the-visual-studio-sdk"></a>Installare Visual Studio SDK  
 Visual Studio SDK è una funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="whats-new-in-the-visual-studio-2017-sdk"></a>Novità in Visual Studio 2017 SDK  
 Visual Studio SDK include alcune nuove funzionalità, ad esempio il formato VSIX v3, nonché importanti modifiche che potrebbe essere necessario aggiornare l'estensione. Per altre informazioni, vedere [nuove funzionalità di Visual Studio 2017 SDK](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md).  
  
## <a name="visual-studio-user-experience-guidelines"></a>Linee guida esperienza utente di Visual Studio  
 Ottenere suggerimenti straordinari per progettazione dell'interfaccia utente per l'estensione nella [linee guida sull'esperienza utente di Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
 È anche possibile imparare a migliorare l'aspetto in dispositivi con DPI elevato con l'estensione per il [problemi DPI indirizzo](../extensibility/addressing-dpi-issues2.md) articolo.  
  
 Sfruttare il [immagini servizio e il catalogo](../extensibility/image-service-and-catalog.md) per la gestione delle immagini ottimale e il supporto per valori DPI alti e temi.  
  
## <a name="find-and-install-existing-visual-studio-extensions"></a>Trovare e installare le estensioni di Visual Studio esistente  
 È possibile trovare le estensioni di Visual Studio nel **estensioni e aggiornamenti** nella finestra di dialogo il **Tools** menu. Per altre informazioni, vedere [trovare e usare Visual Studio Extensions](../ide/finding-and-using-visual-studio-extensions.md). È anche possibile trovare estensioni nel [Visual Studio marketplace](https://marketplace.visualstudio.com/)  
  
## <a name="visual-studio-sdk-reference"></a>Riferimenti di Visual Studio SDK  
 È possibile trovare il riferimento API di Visual Studio SDK alla [riferimenti di Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md).  
  
## <a name="visual-studio-sdk-samples"></a>Esempi di Visual Studio SDK  
 È possibile trovare esempi open source di estensioni di Visual Studio SDK in GitHub all'indirizzo [esempi di Visual Studio](https://aka.ms/vs2015sdksamples). Questo repository GitHub contiene alcuni esempi che illustrano diverse funzionalità estensibile in Visual Studio.  
  
## <a name="other-visual-studio-sdk-resources"></a>Altre risorse di Visual Studio SDK  
 Se si hanno domande sulle VSSDK o si desidera condividere le proprie esperienze di sviluppo di estensioni, è possibile usare la [forum sull'estendibilità di Visual Studio](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) o nella [chat Gitter tale](https://gitter.im/Microsoft/extendvs).  
  
 È possibile trovare altre informazioni, il [VSX Arcana blog](https://blogs.msdn.microsoft.com/vsx/) e un numero di blog scritti dai Microsoft MVPs:  
  
-   [Estensioni preferite di Visual Studio](http://geekswithblogs.net/sdorman/archive/2014/10/05/favorite-visual-studio-extensions.aspx)  
  
-   [Extensibility di Visual Studio](http://www.visualstudioextensibility.com/overview/vs/)  
  
-   [Estensione di Visual Studio](http://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)  
  
## <a name="see-also"></a>Vedere anche  
 [Creare un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md)   
 [Procedura: Eseguire la migrazione di progetti di estendibilità in Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)   
 [DOMANDE FREQUENTI: Conversione di componenti aggiuntivi in estensioni VSPackage](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md)   
 [Gestire più thread in codice gestito](../extensibility/managing-multiple-threads-in-managed-code.md)   
 [Estendere i menu e comandi](../extensibility/extending-menus-and-commands.md)   
 [Aggiungere comandi alle barre degli strumenti](../extensibility/adding-commands-to-toolbars.md)   
 [Estendere e personalizzare le finestre degli strumenti](../extensibility/extending-and-customizing-tool-windows.md)   
 [Estensioni del servizio di editor e linguaggio](../extensibility/editor-and-language-service-extensions.md)   
 [Estendere i progetti](../extensibility/extending-projects.md)   
 [Estendere le opzioni e impostazioni utente](../extensibility/extending-user-settings-and-options.md)   
 [Creare modelli di progetto ed elemento personalizzati](../extensibility/creating-custom-project-and-item-templates.md)   
 [Estendere le proprietà e la finestra delle proprietà](../extensibility/extending-properties-and-the-property-window.md)   
 [Estendere altre parti di Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Uso e fornitura di servizi](../extensibility/using-and-providing-services.md)   
 [Gestire i pacchetti VSPackage](../extensibility/managing-vspackages.md)   
 [Visual Studio isolata shell](/visualstudio/extensibility/shell/visual-studio-isolated-shell)   
 [Fornire estensioni di Visual Studio](../extensibility/shipping-visual-studio-extensions.md)   
 [All'interno di Visual Studio SDK](../extensibility/internals/inside-the-visual-studio-sdk.md)   
 [Supporto per Visual Studio SDK](../extensibility/support-for-the-visual-studio-sdk.md)   
 [Archivio](../extensibility/archive.md)   
 [Riferimenti di Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md)
