---
title: Colorazione della sintassi in un servizio di linguaggio Legacy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring
- language services, syntax coloring
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b80659e1a61cca27adcc92b4b47c7ff0b4e02e0a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58968757"
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>Colorazione della sintassi in un servizio di linguaggio legacy
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Usa un servizio di colorazione per identificare gli elementi del linguaggio e visualizzarli con i colori specificati in un editor.  
  
## <a name="colorizer-model"></a>Modello colorizzatore  
 Il servizio di linguaggio implementa il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfaccia, che viene quindi utilizzato dagli editor. Questa implementazione è un oggetto separato dal servizio di linguaggio, come illustrato nella figura seguente.  
  
 ![Immagine di Colorizzatore SVC](../../extensibility/internals/media/figlgsvccolorizer.gif "FigLgSvcColorizer")  
Modello colorizzatore semplice  
  
> [!NOTE]
>  Il servizio di colorazione della sintassi è separato dal generali [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] meccanismo per la colorazione del testo. Per altre informazioni generali [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] meccanismo che supportano colorare, vedere [utilizzando i tipi di carattere e colori](../../extensibility/using-fonts-and-colors.md).  
  
 Oltre al colorizzatore, il servizio di linguaggio può fornire elementi colorabili personalizzati che vengono utilizzati dall'editor per annunci pubblicitari che fornisce elementi colorabili personalizzati. È possibile farlo mediante l'implementazione di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> interfaccia sullo stesso oggetto che implementa il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfaccia. Restituisce il numero di elementi colorabili personalizzati quando si chiama l'editor di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> metodo e restituisce un singolo elemento colorabile personalizzato quando si chiama l'editor di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> (metodo).  
  
 Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> metodo restituisce un oggetto che implementa il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> interfaccia. Se il servizio di linguaggio supporta valori di colore a 24 bit o elevato, è necessario implementare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfaccia sull'oggetto stesso come il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> interfaccia.  
  
## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>Come un pacchetto VSPackage Usa un Colorizzatore del servizio di linguaggio  
  
1.  Il pacchetto VSPackage deve ottenere il servizio di linguaggio appropriato, che richiede il servizio di linguaggio VSPackage di eseguire le operazioni seguenti:  
  
    1.  Usare un oggetto che implementa il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interfaccia per ottenere il testo da colorare.  
  
         Il testo è in genere visualizzato utilizzando un oggetto che implementa il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaccia.  
  
    2.  Ottenere il servizio di linguaggio eseguendo una query il provider di servizi del pacchetto VSPackage per il GUID del servizio di linguaggio. Servizi di linguaggio vengono identificati nel Registro di sistema dall'estensione del file.  
  
    3.  Associare il servizio di linguaggio con il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> chiamando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> (metodo).  
  
2.  Il pacchetto VSPackage può ora ottenere e usare l'oggetto colorizzatore come indicato di seguito:  
  
    > [!NOTE]
    >  I pacchetti VSPackage che utilizzano l'editor principale non sono necessario ottenere una lingua in modo esplicito gli oggetti del colorizzatore del servizio. Non appena un'istanza di editor principale ha ottenuto un servizio di linguaggio appropriato, esegue tutte le attività di colorazione illustrate di seguito.  
  
    1.  Ottenere l'oggetto colorizzatore del servizio di linguaggio, che implementa il `T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer`, e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> interfacce, chiamando la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> metodo sul servizio di linguaggio <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> oggetto.  
  
    2.  Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodo per ottenere le informazioni del colorizzatore per un determinato intervallo di testo.  
  
         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Restituisce una matrice di valori, uno per ogni carattere nell'intervallo di testo viene colorato. I valori sono gli indici in un elenco di elementi colorabili che è l'elenco di elementi colorabili predefiniti gestiti dall'editor principale o un elenco di elementi colorabili personalizzati gestiti dal servizio di linguaggio stesso.  
  
    3.  Usare le informazioni di colorazione restituite dal <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodo per visualizzare il testo selezionato.  
  
> [!NOTE]
>  Oltre a usare un colorizzatore del servizio di linguaggio, un VSPackage può usare anche il generico [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] la colorazione del meccanismo di testo. Per altre informazioni su questo meccanismo, vedere [utilizzando i tipi di carattere e colori](../../extensibility/using-fonts-and-colors.md).  
  
## <a name="in-this-section"></a>In questa sezione  
 [Implementazione della colorazione della sintassi](../../extensibility/internals/implementing-syntax-coloring.md)  
 Viene illustrato come un editor accede a un servizio di linguaggio colorazione della sintassi e il servizio di linguaggio deve implementare per supportare la sintassi colorazione.  
  
 [Procedura: Usare elementi colorabili incorporati](../../extensibility/internals/how-to-use-built-in-colorable-items.md)  
 Viene illustrato come utilizzare elementi colorabili incorporati dal servizio di linguaggio.  
  
 [Elementi colorabili personalizzati](../../extensibility/internals/custom-colorable-items.md)  
 Viene illustrato come implementare elementi colorabili personalizzati.  
  
## <a name="see-also"></a>Vedere anche  
 [Uso di tipi di carattere e colori](../../extensibility/using-fonts-and-colors.md)
