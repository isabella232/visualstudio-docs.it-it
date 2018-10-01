---
title: Tipo di carattere e colore Panoramica | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], font and color
- font and color control [Visual Studio SDK], editors
ms.assetid: 2203e4e7-8b7f-44ec-8884-6ff718d4f278
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a4321619f249a992d9cdd044f621a21d85a6c380
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47527307"
---
# <a name="font-and-color-overview"></a>Tipo di carattere e colore Panoramica
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [tipo di carattere e colore Panoramica](https://docs.microsoft.com/visualstudio/extensibility/font-and-color-overview).  
  
Questo argomento vengono illustrate le impostazioni testo di carattere e colori nella [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ambiente di sviluppo integrato (IDE). Introduce anche i concetti di categorie e di elementi visualizzati e descrive come i pacchetti VSPackage e l'editor principale di utilizzare gli attributi di testo.  
  
## <a name="the-fonts-and-colors-property-page"></a>I tipi di carattere e colori pagina delle proprietà  
 È possibile gestire gli attributi del testo visualizzato nei [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ambiente di sviluppo integrato (IDE) tramite il **Fonts and Colors** pagina delle proprietà. Per trovare il **tipi di carattere e colori** pagina delle proprietà, scegliere il **strumenti** dal menu fare clic su **opzioni**. Espandere **ambiente**, quindi fare clic su **Fonts and Colors**.  
  
## <a name="categories-and-display-items"></a>Le categorie e elementi visualizzati  
 Sono organizzati in tipi di carattere e colori **categorie** e **elementi visualizzati**.  
  
-   Oggetto **categoria** è un contenitore logico o funzionale per numerosi **elementi visualizzati**.  
  
     Un elenco di **categorie** nel **Mostra impostazioni per** casella di riepilogo a discesa del **tipi di carattere e colori** pagina delle proprietà.  
  
-   Oggetto **elemento visualizzato** è un'entità ben definite di testo, ad esempio un commento, stringa o una struttura di controllo che è possibile colorare quando visualizzata.  
  
 Ciascuna **elemento visualizzato** viene definito in modo univoco all'interno di **categoria** che lo contiene. Di conseguenza, più di un **categoria** può avere un **elemento visualizzato** con lo stesso nome.  
  
## <a name="vspackage-control-of-fonts-and-colors"></a>Pacchetto VSPackage di controllo dei tipi di carattere e colori  
 Il [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] consente a pacchetti VSPackage per:  
  
-   Definire tipi di carattere e colori **categorie**.  
  
-   Specificare i tipi di carattere e colori utilizzati per presentare **elementi visualizzati**.  
  
-   Interagire con il **Fonts and Colors** pagina delle proprietà.  
  
-   Aggregazione multiplo **categorie** in gruppi.  
  
-   Rendere persistenti le modifiche nelle impostazioni predefinite.  
  
 Esistono due modi per interagire con tipo di carattere e colore selezioni all'interno di [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)].  
  
-   Uno di questi è detta *colorazione della sintassi*. Viene usato da un pacchetto VSPackage che Personalizza esistente [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] editor per implementare un servizio di linguaggio e creare un'origine dell'editor.  
  
     Un solo **categoria** supporta questo meccanismo, vale a dire, il **Editor di testo**.  
  
-   Un'alternativa più generale supporta tutti gli altri **categorie** e i componenti dell'interfaccia utente diverso da editor di origine quando la visualizzazione di testo. Per altre informazioni, vedere <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>.  
  
## <a name="core-editor-text-settings"></a>Impostazioni dell'Editor principale di testo  
 Le impostazioni di carattere e colori per l'editor principale di un oggetto servizio di linguaggio sono regolate dal **testo EditorCategory** trovato nel **Mostra impostazioni per** casella di riepilogo a discesa del **i tipi di carattere e colori** pagina delle proprietà.  
  
 Quando si lavora con gli editor, è consigliabile usare il carattere specializzato e un meccanismo di controllo di colore che fornisce il servizio di linguaggio per controllare ed estendere il **Editor di testo** impostazioni. Il meccanismo è detto *colorazione della sintassi* e fornisce:  
  
-   Una tecnica semplificata per la gestione di carattere e colori degli elementi visualizzati.  
  
     Per altre informazioni, vedere <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.  
  
-   Un meccanismo ben definiti e con ottimizzazione per la colorazione.  
  
     Per altre informazioni, vedere <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>.  
  
-   La possibilità di entrambi utilizzano gli oggetti di visualizzazione predefinite della **EditorCategory testo** e di estenderle.  
  
     Per altre informazioni, vedere [procedura: elementi colorabili incorporati uso](../extensibility/internals/how-to-use-built-in-colorable-items.md) e [elementi colorabili personalizzati](../extensibility/internals/custom-colorable-items.md).  
  
-   Salvataggio permanente automatico dell'oggetto corrente dello stato di entrambi incorporati e personalizzati visualizzare gli elementi con il **Editor di testo** categoria.  
  
 Per altre informazioni sulla sintassi, vedere colorazione [colorazione della sintassi in un servizio di linguaggio Legacy](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce legacy nell'Editor](../extensibility/legacy-interfaces-in-the-editor.md)   
 [Colorazione della sintassi in un servizio di linguaggio legacy](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

