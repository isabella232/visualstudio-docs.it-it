---
title: Usando tipi di carattere e colori | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- fonts, controlling in IDE
- IDE, controlling text color and fonts
- Fonts and Colors property page
- font and color control [Visual Studio SDK]
- text, IDE
ms.assetid: d1a9b99f-fbdc-45ed-920a-e08c3d931ac9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 96abe68838d028c5de9d6d9418e94ba5b46c0f76
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56693412"
---
# <a name="using-fonts-and-colors"></a>Usando tipi di carattere e colori
Il [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] fornisce il supporto per l'utilizzo di tipi di carattere e colori per visualizzare il testo.

## <a name="in-this-section"></a>In questa sezione
- [Tipo di carattere e colore Overview](../extensibility/font-and-color-overview.md) vengono illustrate le impostazioni del tipo di carattere e colore di testo nel [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE). Inoltre vengono illustrati i concetti di categorie e di elementi visualizzati e viene descritto come i pacchetti VSPackage e l'editor principale di utilizzare gli attributi di testo.

- [Recuperare le informazioni di colore e tipo di carattere per la colorazione del testo](../extensibility/getting-font-and-color-information-for-text-colorization.md) vengono fornite linee guida per l'implementazione di colorazione del testo nei pacchetti VSPackage che gestiscono **categorie** diverso da **Editor di testo**.

- [L'accesso a tipi di carattere archiviate e le impostazioni dei colori](../extensibility/accessing-stored-font-and-color-settings.md) indica come impostazioni correnti di carattere e colori possono essere archiviate, recuperati e applicate.

- [Implementazione categorie personalizzate e gli elementi visualizzati](../extensibility/implementing-custom-categories-and-display-items.md) descrive i passaggi di base mediante il quale è possibile creare e usare il proprio di una finestra **elementi visualizzati** e **categorie** per supportare la visualizzazione del testo.

 Questo approccio richiede un pacchetto VSPackage implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> interfaccia e interfacce correlate.

- [Procedura: Accedere ai tipi di carattere incorporati e combinazione di colori](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md) viene illustrato come definire e registrare una categoria, utilizzando i tipi di carattere incorporati e i colori e avviare l'uso di caratteri fornita dal sistema e i colori.

## <a name="reference"></a>Riferimenti
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> Fornisce un'istanza del `IVsFontAndColorDefaults` o il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> interfaccia che corrisponde a un determinato elemento presente nel **Mostra impostazioni per** nell'elenco il **tipi di carattere e colori** pagina della finestra di **Opzioni** nella finestra di dialogo.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> Consente a un pacchetto VSPackage a supporto dell'IDE **Fonts and Colors** pagina mediante la definizione di tipi di carattere predefiniti e i colori per una finestra o un componente dell'interfaccia utente.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> Fornisce un meccanismo mediante il quale un pacchetto VSPackage che fornisce il supporto del tipo di carattere e colore può specificare un gruppo di elemento visualizzato - una categoria superiore che rappresenta l'unione di due o più categorie.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Consente a un VSPackage di recuperare i dati di carattere e colori oppure salvarlo nel Registro di sistema.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> Notifica ai pacchetti VSPackage che utilizzano le informazioni di carattere e colori sulle modifiche nelle impostazioni del tipo di carattere e colore.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities> Fornisce gli strumenti per lavorare con i dati di input e outpui che viene usati dai metodi della [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **carattere e colori** meccanismo.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> Controlla la memorizzazione nella cache delle impostazioni del tipo di carattere e colore.

## <a name="related-sections"></a>Sezioni correlate
- [Sviluppo di un servizio di linguaggio Legacy](../extensibility/internals/developing-a-legacy-language-service.md) illustra come i pacchetti VSPackage possono usare servizi di linguaggio per personalizzare il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor.

- [Colorazione della sintassi negli editor personalizzati](../extensibility/syntax-coloring-in-custom-editors.md) Descries il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor utilizza servizi di linguaggio per implementare la colorazione della sintassi.

- [Estensione di altre parti di Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md) spiega come usare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] services per creare elementi dell'interfaccia utente che corrispondono al resto del [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].