---
title: Visual Studio SDK | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
caps.latest.revision: 57
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 27dce16d9fe02063eae935af96c26184285e583d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850372"
---
# <a name="visual-studio-sdk"></a>Visual Studio SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio SDK consente di estendere le funzionalità di Visual Studio o di integrare nuove funzionalità in Visual Studio. È possibile distribuire le estensioni ad altri utenti e a Visual Studio Gallery. Di seguito sono illustrati alcuni dei modi in cui si può estendere Visual Studio:  
  
- Aggiungere comandi, pulsanti, menu e altri elementi dell'interfaccia utente all'IDE  
  
- Aggiunta di finestre degli strumenti per nuove funzionalità  
  
- Estendi IntelliSense per un determinato linguaggio o fornisci IntelliSense per i nuovi linguaggi di programmazione  
  
- Usare le lampadine per fornire suggerimenti e suggerimenti che consentono agli sviluppatori di scrivere codice migliore  
  
- Abilita supporto per una nuova lingua  
  
- Aggiungere un tipo di progetto personalizzato  
  
- Raggiungi milioni di sviluppatori tramite il Visual Studio Marketplace  
  
  Se non è mai stata scritta un'estensione di Visual Studio, è necessario trovare altre informazioni su queste funzionalità e [avviare lo sviluppo di estensioni di Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).  
  
## <a name="installing-the-visual-studio-sdk"></a>Installazione di Visual Studio SDK  
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. Viene inclusa come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare Visual Studio SDK in un secondo momento. Per ulteriori informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="whats-new-in-the-visual-studio-2015-sdk"></a>Novità di Visual Studio 2015 SDK  
 Visual Studio SDK include alcune nuove funzionalità, incluse le lampadine e i nuovi elementi di progetto che consentono di creare comandi di menu, finestre degli strumenti ed estensioni dell'editor usando un pacchetto VSIX. Per ulteriori informazioni, vedere Novità [di Visual Studio 2015 SDK](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md).  
  
## <a name="visual-studio-user-experience-guidelines"></a>Linee guida sull'esperienza utente di Visual Studio  
 Suggerimenti utili per la progettazione dell'interfaccia utente per l'estensione nelle [linee guida sull'esperienza utente di Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
 È anche possibile ottenere informazioni su come rendere l'estensione molto interessante nei dispositivi ad alta risoluzione con i [problemi di indirizzamento dpi](../extensibility/addressing-dpi-issues2.md) .  
  
 Sfrutta i vantaggi del [servizio immagini e del catalogo](../extensibility/image-service-and-catalog.md) per ottimizzare la gestione delle immagini e il supporto per valori dpi e temi elevati.  
  
## <a name="finding-and-installing-existing-visual-studio-extensions"></a>Ricerca e installazione di estensioni di Visual Studio esistenti  
 È possibile trovare le estensioni di Visual Studio nella finestra di dialogo **estensioni e aggiornamenti** del menu **strumenti** . Per altre informazioni, vedere [ricerca e uso delle estensioni di Visual Studio](../ide/finding-and-using-visual-studio-extensions.md). È anche possibile trovare estensioni nel [Visual Studio Marketplace](https://marketplace.visualstudio.com/)  
  
## <a name="visual-studio-sdk-reference"></a>Informazioni di riferimento su Visual Studio SDK  
 Informazioni di riferimento sulle API di Visual Studio SDK sono disponibili in [riferimenti a Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md).  
  
## <a name="visual-studio-sdk-samples"></a>Esempi di Visual Studio SDK  
 È possibile trovare esempi Open Source di estensioni di Visual Studio SDK in GitHub in [Visual Studio Samples](https://github.com/Microsoft/VSSDK-Extensibility-Samples). Questo repository GitHub contiene esempi che illustrano varie funzionalità estendibili in Visual Studio.  
  
## <a name="other-visual-studio-sdk-resources"></a>Altre risorse di Visual Studio SDK  
 In caso di domande su VSSDK o se si vuole condividere le proprie esperienze sviluppando estensioni, è possibile usare il [Forum di estendibilità di Visual Studio](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) o la [chat del gruppo ExtendVS](https://gitter.im/Microsoft/extendvs).  
  
 Per ulteriori informazioni, vedere il [Blog di VSX Arcana](https://blogs.msdn.microsoft.com/vsx/) e un numero di Blog scritti da Microsoft MVP:  
  
- [Estensioni di Visual Studio preferite](https://scottdorman.blog/2014/10/05/favorite-visual-studio-extensions/)  
  
- [Estendibilità di Visual Studio](http://www.visualstudioextensibility.com/overview/vs/)  
  
- [Estensione di Visual Studio](https://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md)   
 [Procedura: eseguire la migrazione di progetti di estendibilità a Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md)   
 [Domande frequenti: conversione di componenti aggiuntivi in estensioni VSPackage](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md)   
 [Gestione di più thread nel codice gestito](../extensibility/managing-multiple-threads-in-managed-code.md)   
 [Estensione di menu e comandi](../extensibility/extending-menus-and-commands.md)   
 [Aggiunta di comandi alle barre degli strumenti](../extensibility/adding-commands-to-toolbars.md)   
 [Estensione e personalizzazione delle finestre degli strumenti](../extensibility/extending-and-customizing-tool-windows.md)   
 [Editor e estensioni del servizio di linguaggio](../extensibility/editor-and-language-service-extensions.md)   
 [Estensione di progetti](../extensibility/extending-projects.md)   
 [Estensione delle impostazioni e delle opzioni utente](../extensibility/extending-user-settings-and-options.md)   
 [Creazione di modelli di progetto e di elemento personalizzati](../extensibility/creating-custom-project-and-item-templates.md)   
 [Estensione delle proprietà e della finestra delle proprietà](../extensibility/extending-properties-and-the-property-window.md)   
 [Estensione di altre parti di Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Uso e fornitura di servizi](../extensibility/using-and-providing-services.md)   
 [Estensione di Servizi connessi](../extensibility/extending-connected-services.md)   
 [Gestione dei pacchetti VSPackage](../extensibility/managing-vspackages.md)   
 [Shell isolata di Visual Studio](../extensibility/visual-studio-isolated-shell.md)   
 [Distribuzione delle estensioni di Visual Studio](../extensibility/shipping-visual-studio-extensions.md)   
 [All'interno di Visual Studio SDK](../extensibility/internals/inside-the-visual-studio-sdk.md)   
 [Supporto per Visual Studio SDK](../extensibility/support-for-the-visual-studio-sdk.md)   
 [Archivio](../extensibility/archive.md)   
 [Informazioni di riferimento su Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md)
