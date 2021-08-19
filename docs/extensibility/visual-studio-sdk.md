---
title: Visual Studio Sdk | Microsoft Docs
description: L Visual Studio SDK consente di estendere le funzionalità o aggiungere nuove funzionalità Visual Studio. Informazioni su alcuni dei modi in cui è possibile estendere Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: f61ad24a7a94827720de388ed957f1c33dc7bc8c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122078609"
---
# <a name="visual-studio-sdk"></a>Visual Studio SDK
L Visual Studio SDK consente di estendere Visual Studio funzionalità o integrare nuove funzionalità in Visual Studio. È possibile distribuire le estensioni ad altri utenti, nonché a Visual Studio Marketplace. Di seguito sono illustrati alcuni dei modi in cui si può estendere Visual Studio:

- Aggiungere comandi, pulsanti, menu e altri elementi dell'interfaccia utente all'IDE

- Aggiungere finestre degli strumenti per nuove funzionalità

- Estendere IntelliSense per un linguaggio specifico o fornire IntelliSense per nuovi linguaggi di programmazione

- Usare lampadine per fornire suggerimenti e suggerimenti che consentono agli sviluppatori di scrivere codice migliore

- Abilitare il supporto per una nuova lingua

- Aggiungere un tipo di progetto personalizzato

- Raggiungere milioni di sviluppatori tramite Visual Studio Marketplace

  Se non è mai stata scritta un'estensione Visual Studio, è consigliabile trovare altre informazioni su queste funzionalità e in [Starting to develop Visual Studio extensions](../extensibility/starting-to-develop-visual-studio-extensions.md).

## <a name="install-the-visual-studio-sdk"></a>Installare Visual Studio SDK
 L Visual Studio SDK è una funzionalità facoltativa nella Visual Studio configurazione. È anche possibile installare VS SDK in un secondo momento. Per altre informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="whats-new-in-the-visual-studio-sdk"></a>Novità di Visual Studio SDK
 Visual Studio SDK include alcune nuove funzionalità, ad esempio l'avviso relativo alle estensioni caricate automaticamente in modo sincrono e il formato VSIX v3, nonché modifiche di rilievo, che potrebbero richiedere l'aggiornamento dell'estensione. Per altre informazioni, vedere Novità di [Visual Studio 2019 SDK](../extensibility/whats-new-visual-studio-2019-sdk.md) e Novità di [Visual Studio 2017 SDK.](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md)

## <a name="visual-studio-user-experience-guidelines"></a>Visual Studio linee guida per l'esperienza utente
 Suggerimenti utili per la progettazione dell'interfaccia utente per l'estensione nelle linee [guida Visual Studio'esperienza utente.](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)

 È anche possibile imparare a rendere l'estensione ideale nei dispositivi DPI elevati con [l'articolo Risolvere i problemi DPI.](../extensibility/addressing-dpi-issues2.md)

 Sfruttare i vantaggi del [servizio Immagine e del catalogo per](../extensibility/image-service-and-catalog.md) una gestione delle immagini e un supporto per valori DPI e a sfondo elevati.

## <a name="find-and-install-existing-visual-studio-extensions"></a>Trovare e installare le estensioni Visual Studio esistenti
 Le estensioni Visual Studio disponibili sono disponibili nella **finestra di dialogo Estensioni e** aggiornamenti del menu Strumenti.  Per altre informazioni, vedere [Trovare e usare le Visual Studio.](../ide/finding-and-using-visual-studio-extensions.md) È anche possibile trovare le estensioni in [Visual Studio Marketplace](https://marketplace.visualstudio.com/)

## <a name="visual-studio-sdk-reference"></a>Visual Studio Informazioni di riferimento su SDK
 Per informazioni di riferimento sull'API Visual Studio SDK, vedere Visual Studio SDK Reference (Informazioni di riferimento [sull'SDK).](../extensibility/visual-studio-sdk-reference.md)

## <a name="visual-studio-sdk-samples"></a>Visual Studio Esempi di SDK
 È possibile trovare open source esempi di estensioni di VS SDK GitHub in [Visual Studio Esempi](https://github.com/Microsoft/VSSDK-Extensibility-Samples). Questo GitHub contiene esempi che illustrano varie funzionalità estendibili in Visual Studio.

## <a name="other-visual-studio-sdk-resources"></a>Altre Visual Studio SDK
 Per domande su VSSDK o per condividere le esperienze di sviluppo di estensioni, è possibile usare Visual Studio [Extensibility Forum](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) o [ExtendVS Gitter Chatroom.](https://gitter.im/Microsoft/extendvs)

 Altre informazioni sono disponibili nel [blog di VSX Arcana](/archive/blogs/vsx/) e in diversi blog scritti da Microsoft MVP:

- [Estensioni Visual Studio preferiti](https://scottdorman.blog/2014/10/05/favorite-visual-studio-extensions/)

- [Estendibilità in Visual Studio](http://www.visualstudioextensibility.com/overview/vs/)

- [Estensione Visual Studio](https://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)

## <a name="see-also"></a>Vedi anche

- [Creare un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md)
- [Procedura: Eseguire la migrazione di progetti di estendibilità Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)
- [Domande frequenti: Conversione di componenti aggiuntivi in estensioni VSPackage](/previous-versions/visualstudio/visual-studio-2015/extensibility/faq-converting-add-ins-to-vspackage-extensions?preserve-view=true&view=vs-2015)
- [Gestire più thread nel codice gestito](../extensibility/managing-multiple-threads-in-managed-code.md)
- [Estendere menu e comandi](../extensibility/extending-menus-and-commands.md)
- [Aggiungere comandi alle barre degli strumenti](../extensibility/adding-commands-to-toolbars.md)
- [Estendere e personalizzare le finestre degli strumenti](../extensibility/extending-and-customizing-tool-windows.md)
- [Estensioni del servizio editor ed linguaggio](../extensibility/editor-and-language-service-extensions.md)
- [Estendere i progetti](../extensibility/extending-projects.md)
- [Estendere le impostazioni utente e le opzioni](../extensibility/extending-user-settings-and-options.md)
- [Creare modelli di progetto e di elemento personalizzati](../extensibility/creating-custom-project-and-item-templates.md)
- [Estendere le proprietà e la finestra delle proprietà](../extensibility/extending-properties-and-the-property-window.md)
- [Estendere altre parti di Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)
- [Usare e fornire servizi](../extensibility/using-and-providing-services.md)
- [Gestire VSPackage](../extensibility/managing-vspackages.md)
- [Visual Studio shell isolata](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)
- [Spedire Visual Studio estensioni](../extensibility/shipping-visual-studio-extensions.md)
- [All'interno di Visual Studio SDK](../extensibility/internals/inside-the-visual-studio-sdk.md)
- [Supporto per Visual Studio SDK](../extensibility/support-for-the-visual-studio-sdk.md)
- [Visual Studio Informazioni di riferimento su SDK](../extensibility/visual-studio-sdk-reference.md)