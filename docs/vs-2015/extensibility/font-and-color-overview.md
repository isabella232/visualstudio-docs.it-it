---
title: Panoramica dei tipi di carattere e dei colori | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], font and color
- font and color control [Visual Studio SDK], editors
ms.assetid: 2203e4e7-8b7f-44ec-8884-6ff718d4f278
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0a20cfa2372b1e55652ffcebe6d173cff86140a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204351"
---
# <a name="font-and-color-overview"></a>Panoramica di tipi di carattere e colori
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questo argomento vengono illustrate le impostazioni relative ai colori e ai tipi di carattere nel [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Integrated Development Environment (IDE). Vengono inoltre introdotti i concetti delle categorie e degli elementi visualizzati e viene descritto il modo in cui i VSPackage e l'editor principale utilizzano gli attributi di testo.  
  
## <a name="the-fonts-and-colors-property-page"></a>Pagina delle proprietà tipi di carattere e colori  
 È possibile gestire gli attributi del testo visualizzato nell' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Integrated Development Environment (IDE) tramite la pagina delle proprietà **tipi di carattere e colori** . Per trovare la pagina delle proprietà **tipi di carattere e colori** , scegliere **Opzioni**dal menu **strumenti** . Espandere **Ambiente**e fare clic su **Tipi di carattere e colori**.  
  
## <a name="categories-and-display-items"></a>Categorie e elementi visualizzati  
 I tipi di carattere e i colori sono organizzati in **categorie** e **elementi visualizzati**.  
  
- Una **categoria** è un contenitore logico o funzionale per una serie di **elementi visualizzati**.  
  
   Un elenco di **categorie** è disponibile nella casella a discesa **Mostra impostazioni per** della pagina delle proprietà **tipi di carattere e colori** .  
  
- Un **elemento visualizzato** è un'entità di testo ben definita, ad esempio un commento, una stringa o una struttura di controllo che deve essere colorata quando viene visualizzata.  
  
  Ogni **elemento visualizzato** viene definito in modo univoco all'interno della **categoria** che lo contiene. Di conseguenza, più di una **categoria** può avere un **elemento visualizzato** con lo stesso nome.  
  
## <a name="vspackage-control-of-fonts-and-colors"></a>Controllo VSPackage di tipi di carattere e colori  
 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]Consente ai VSPackage di:  
  
- Definire le **categorie**di tipi di carattere e colori.  
  
- Specificare i tipi di carattere e i colori utilizzati per presentare **gli elementi visualizzati**.  
  
- Interagire con la pagina delle proprietà **tipi di carattere e colori** .  
  
- Aggregare più **categorie** in gruppi.  
  
- Mantieni le modifiche nelle impostazioni predefinite.  
  
  Esistono due modi per interagire con le selezioni di tipi di carattere e colori all'interno di [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] .  
  
- Un metodo viene definito colorazione della *sintassi*. Viene usato da un pacchetto VSPackage che Personalizza l'editor esistente [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] per implementare un servizio di linguaggio e creare un editor di origine.  
  
   Solo una **categoria** supporta questo meccanismo, ovvero l'editor di **testo**.  
  
- Un'alternativa più generale supporta tutte le altre **categorie** e i componenti dell'interfaccia utente diversi dall'editor di origine quando viene visualizzato il testo. Per altre informazioni, vedere <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>.  
  
## <a name="core-editor-text-settings"></a>Impostazioni del testo dell'editor principale  
 Le impostazioni relative al tipo di carattere e al colore per l'editor principale di un oggetto servizio di linguaggio sono regolate dal **testo EditorCategory** trovato nella casella di riepilogo a discesa **Mostra impostazioni per** della pagina delle proprietà **tipi di carattere e colori** .  
  
 Quando si utilizzano gli editor, è necessario utilizzare il meccanismo di controllo dei colori e dei tipi di carattere specializzati fornito dal servizio di linguaggio per controllare ed estendere le impostazioni dell' **editor di testo** . Il meccanismo viene definito colorazione della *sintassi* e fornisce:  
  
- Una tecnica semplificata per la gestione dei tipi di carattere e dei colori degli elementi visualizzati.  
  
   Per altre informazioni, vedere <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.  
  
- Meccanismo di colorazione ben definito e ottimizzato.  
  
   Per altre informazioni, vedere <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>.  
  
- La possibilità di usare gli elementi visualizzati predefiniti dal **testo EditorCategory** e di estenderli.  
  
   Per altre informazioni, vedere [procedura: usare elementi colorabili incorporati](../extensibility/internals/how-to-use-built-in-colorable-items.md) e [elementi colorabili personalizzati](../extensibility/internals/custom-colorable-items.md).  
  
- Persistenza automatica dello stato corrente degli elementi visualizzati incorporati e personalizzati con la categoria **editor di testo** .  
  
  Per ulteriori informazioni sulla colorazione della sintassi, vedere [colorazione della sintassi in un servizio di linguaggio legacy](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce legacy nell'editor](../extensibility/legacy-interfaces-in-the-editor.md)   
 [Colorazione della sintassi in un servizio di linguaggio legacy](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
