---
title: Visual Studio SDK - Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 56f772d7d27f11318cdeb0bf365373d5f7c1294b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698072"
---
# <a name="visual-studio-sdk"></a>Visual Studio SDK
Visual Studio SDK consente di estendere le funzionalità di Visual Studio o di integrare nuove funzionalità in Visual Studio. È possibile distribuire le estensioni ad altri utenti, nonché a Visual Studio Marketplace. Di seguito sono illustrati alcuni dei modi in cui si può estendere Visual Studio:

- Aggiungere comandi, pulsanti, menu e altri elementi dell'interfaccia utente all'IDE

- Aggiungere finestre degli strumenti per nuove funzionalità

- Estendere IntelliSense per un determinato linguaggio o fornire IntelliSense per nuovi linguaggi di programmazioneExtend IntelliSense for a given language, or provide IntelliSense for new programming languages

- Usa le lampadine per fornire suggerimenti e suggerimenti che aiutano gli sviluppatori a scrivere codice migliore

- Abilitare il supporto per una nuova lingua

- Aggiungere un tipo di progetto personalizzatoAdd a custom project type

- Raggiungi milioni di sviluppatori tramite Visual Studio Marketplace

  Se non è mai stata scritta un'estensione di Visual Studio prima, è necessario trovare ulteriori informazioni su queste funzionalità e in [Avvio per sviluppare le estensioni](../extensibility/starting-to-develop-visual-studio-extensions.md)di Visual Studio .

## <a name="install-the-visual-studio-sdk"></a>Installare Visual Studio SDK
 Visual Studio SDK è una funzionalità facoltativa nel programma di installazione di Visual Studio.The Visual Studio SDK is an optional feature in Visual Studio setup. È anche possibile installare l'SDK di VISUAL SMI in un secondo momento. Per ulteriori informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="whats-new-in-the-visual-studio-2017-sdk"></a>Novità di Visual Studio 2017 SDK
 Visual Studio SDK dispone di alcune nuove funzionalità, ad esempio il formato VSIX v3 e le modifiche di rilievo, che potrebbero richiedere l'aggiornamento dell'estensione. Per ulteriori informazioni, vedere [Novità di Visual Studio 2017 SDK.](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md)

## <a name="visual-studio-user-experience-guidelines"></a>Linee guida per l'esperienza utente di Visual Studio
 Ottieni ottimi suggerimenti per la progettazione dell'interfaccia utente per l'estensione nelle linee guida per [l'esperienza utente](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)di Visual Studio.

 Puoi anche imparare a rendere l'estensione accattivante nei dispositivi Con valori DPI elevati con l'articolo [Address DPI issues](../extensibility/addressing-dpi-issues2.md) (Problemi relativi ai valori DPI per l'indirizzo).

 Approfitta del [servizio E del catalogo delle immagini](../extensibility/image-service-and-catalog.md) per una gestione e un supporto per valori DPI e tematici elevati.

## <a name="find-and-install-existing-visual-studio-extensions"></a>Trovare e installare le estensioni di Visual Studio esistentiFind and install existing Visual Studio extensions
 È possibile trovare le estensioni di Visual Studio nella finestra di dialogo **Estensioni e aggiornamenti** del menu **Strumenti.You** can find Visual Studio extensions in the Extensions and Updates dialog on the Tools menu. Per ulteriori informazioni, vedere [Trovare e utilizzare le estensioni](../ide/finding-and-using-visual-studio-extensions.md)di Visual Studio . È inoltre possibile trovare estensioni in [Visual Studio Marketplace](https://marketplace.visualstudio.com/)

## <a name="visual-studio-sdk-reference"></a>Guida di riferimento a Visual Studio SDK
 È possibile trovare il riferimento all'API di Visual Studio SDK in Guida di riferimento a [Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md).

## <a name="visual-studio-sdk-samples"></a>Esempi di Visual Studio SDK
 È possibile trovare esempi open source di estensioni di VISUAL SDK in GitHub in Esempi di [Visual Studio](https://github.com/Microsoft/VSSDK-Extensibility-Samples). Questo repository GitHub contiene esempi che illustrano varie funzionalità estensibili in Visual Studio.This GitHub repo contains samples that illustrate various extensible features in Visual Studio.

## <a name="other-visual-studio-sdk-resources"></a>Altre risorse di Visual Studio SDK
 In caso di domande su VSSDK o si desidera condividere le proprie esperienze nello sviluppo di estensioni, è possibile utilizzare il forum di [estendibilità](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) di Visual Studio o la chat [di Gitter ExtendVS](https://gitter.im/Microsoft/extendvs).

 È possibile trovare ulteriori informazioni nel [blog VSX Arcana](https://blogs.msdn.microsoft.com/vsx/) e una serie di blog scritti da Microsoft MVP:

- [Estensioni di Visual Studio preferite](https://scottdorman.blog/2014/10/05/favorite-visual-studio-extensions/)

- [Estendibilità di Visual Studio](http://www.visualstudioextensibility.com/overview/vs/)

- [Estensione di Visual StudioExtending Visual Studio](https://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)

## <a name="see-also"></a>Vedere anche

- [Creare un'estensione con un comando di menuCreate an extension with a menu command](../extensibility/creating-an-extension-with-a-menu-command.md)
- [Procedura: eseguire la migrazione di progetti di estendibilità a Visual Studio 2017How to: Migrate extensibility projects to Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)
- [Domande frequenti: conversione di componenti aggiuntivi in estensioni VSPackageFAQ: Converting add-ins to VSPackage extensions](/visualstudio/extensibility/faq-converting-add-ins-to-vspackage-extensions?view=vs-2015)
- [Gestire più thread nel codice gestitoManage multiple threads in managed code](../extensibility/managing-multiple-threads-in-managed-code.md)
- [Estendere menu e comandi](../extensibility/extending-menus-and-commands.md)
- [Aggiungere comandi alle barre degli strumenti](../extensibility/adding-commands-to-toolbars.md)
- [Estendere e personalizzare le finestre degli strumenti](../extensibility/extending-and-customizing-tool-windows.md)
- [Editor e estensioni del servizio di linguaggio](../extensibility/editor-and-language-service-extensions.md)
- [Estendere i progetti](../extensibility/extending-projects.md)
- [Estendere le impostazioni e le opzioni utente](../extensibility/extending-user-settings-and-options.md)
- [Creare modelli di progetto e di elemento personalizzati](../extensibility/creating-custom-project-and-item-templates.md)
- [Estendere le proprietà e la finestra delle proprietàExtend properties and the property window](../extensibility/extending-properties-and-the-property-window.md)
- [Estendere altre parti di Visual StudioExtend other parts of Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)
- [Utilizzo e fornitura di servizi](../extensibility/using-and-providing-services.md)
- [Gestire VSPackage](../extensibility/managing-vspackages.md)
- [Shell isolata di Visual StudioVisual Studio isolated shell](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)
- [Spedire le estensioni di Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
- [All'interno di Visual Studio SDK](../extensibility/internals/inside-the-visual-studio-sdk.md)
- [Supporto per Visual Studio SDK](../extensibility/support-for-the-visual-studio-sdk.md)
- [Guida di riferimento a Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md)
