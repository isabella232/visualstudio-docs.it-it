---
title: Uso di tipi di carattere e colori | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, controlling in IDE
- IDE, controlling text color and fonts
- Fonts and Colors property page
- font and color control [Visual Studio SDK]
- text, IDE
ms.assetid: d1a9b99f-fbdc-45ed-920a-e08c3d931ac9
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42ebc9414e3e5bb10f2468ed7f5f4fb4900e4ec6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68177232"
---
# <a name="using-fonts-and-colors"></a>Uso di tipi di carattere e colori
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]Fornisce supporto per l'utilizzo di tipi di carattere e colori per visualizzare il testo.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Panoramica di tipi di carattere e colori](../extensibility/font-and-color-overview.md)  
 Illustra le impostazioni relative ai colori e ai tipi di carattere del testo nel [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Integrated Development Environment (IDE). Vengono inoltre introdotti i concetti delle categorie e degli elementi visualizzati e viene descritto il modo in cui i VSPackage e l'editor principale utilizzano gli attributi di testo.  
  
 [Recupero di informazioni su tipi di carattere e colori per la colorazione del testo](../extensibility/getting-font-and-color-information-for-text-colorization.md)  
 Vengono fornite linee guida per l'implementazione della colorazione del testo in VSPackage che gestiscono **categorie** diverse dall' **editor di testo**.  
  
 [Accesso alle impostazioni di tipi di carattere e colori archiviate](../extensibility/accessing-stored-font-and-color-settings.md)  
 Viene illustrato il modo in cui è possibile archiviare, recuperare e applicare le impostazioni correnti del tipo di carattere e del colore.  
  
 [Implementazione di categorie ed elementi di visualizzazione personalizzati](../extensibility/implementing-custom-categories-and-display-items.md)  
 Vengono descritti i passaggi di base in base ai quali una finestra può creare e utilizzare il proprio **elemento di visualizzazione** e le **categorie** per supportare la visualizzazione di testo.  
  
 Questo approccio richiede un VSPackage per implementare l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> interfaccia e le interfacce correlate.  
  
 [Procedura: Accedere i tipi di carattere e alle combinazioni colori predefiniti](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)  
 Viene illustrato come definire e registrare una categoria utilizzando tipi di carattere e colori predefiniti e come avviare l'utilizzo di tipi di carattere e colori forniti dal sistema.  
  
## <a name="reference"></a>Riferimento  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
 Fornisce un'istanza del `IVsFontAndColorDefaults` o l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> interfaccia corrispondente a un particolare elemento elencato nell'elenco **Mostra impostazioni per** nella pagina **tipi di carattere e colori** della finestra di dialogo **Opzioni** .  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
 Consente a un VSPackage di supportare la pagina **tipi di carattere e colori** dell'IDE definendo i tipi di carattere e i colori predefiniti per una finestra o un componente dell'interfaccia utente.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>  
 Fornisce un meccanismo mediante il quale un VSPackage che fornisce supporto per tipi di carattere e colori può specificare un gruppo di elementi visualizzati, ovvero una supercategoria che rappresenta l'Unione di due o più categorie.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>  
 Consente a un VSPackage di recuperare i dati di tipo carattere e colore oppure di salvarli nel registro di sistema.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
 Notifica ai VSPackage che usano le informazioni relative al tipo di carattere e al colore delle modifiche nelle impostazioni del tipo di carattere e del colore.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities>  
 Fornisce strumenti per l'utilizzo dei dati di input e di output utilizzati dai metodi del meccanismo del [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **tipo di carattere e del colore** .  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
 Determina la memorizzazione nella cache delle impostazioni dei tipi di carattere e dei colori.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Sviluppo di un servizio di linguaggio legacy](../extensibility/internals/developing-a-legacy-language-service.md)  
 Illustra il modo in cui i pacchetti VSPackage possono usare i servizi di linguaggio per personalizzare l' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Editor.  
  
 [Colorazione della sintassi negli editor personalizzati](../extensibility/syntax-coloring-in-custom-editors.md)  
 Descries il modo [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] in cui l'editor usa i servizi di linguaggio per implementare la colorazione della sintassi.  
  
 [Estensione di altre parti di Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Spiega come usare i servizi di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] per creare elementi dell'interfaccia utente che corrispondono al resto di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].
