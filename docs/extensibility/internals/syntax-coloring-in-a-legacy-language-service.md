---
title: Colorazione della sintassi in un servizio di linguaggio legacy | Microsoft Docs
description: Informazioni su come Visual Studio implementa un servizio di colorazione della sintassi in un servizio di linguaggio legacy per identificare gli elementi del linguaggio e visualizzarli in colori in un editor.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring
- language services, syntax coloring
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c90d64fa3835eb3b0963923ba7b65ad7afb5758a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965239"
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>Colorazione della sintassi in un servizio di linguaggio legacy

Visual Studio usa un servizio di colorazione per identificare gli elementi del linguaggio e visualizzarli con i colori specificati in un editor.

## <a name="colorizer-model"></a>Modello di coloratori
 Il servizio di linguaggio implementa l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfaccia, che viene quindi utilizzata dagli editor. Questa implementazione è un oggetto separato dal servizio di linguaggio, come illustrato nella figura seguente:

 ![Rappresentazione grafica dell'applicazione dei colori SVC](../../extensibility/internals/media/figlgsvccolorizer.gif)

> [!NOTE]
> Il servizio di colorazione della sintassi è separato dal meccanismo generale di Visual Studio per la colorazione del testo. Per ulteriori informazioni sul meccanismo generale [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] che supporta la colorazione, vedere [utilizzo di tipi di carattere e colori](/previous-versions/visualstudio/visual-studio-2015/extensibility/using-fonts-and-colors?preserve-view=true&view=vs-2015).

 Oltre a coloratori, il servizio di linguaggio può fornire elementi colorabili personalizzati usati dall'editor, per annunciare che fornisce elementi colorabili personalizzati. È possibile eseguire questa operazione implementando l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> interfaccia sullo stesso oggetto che implementa l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfaccia. Restituisce il numero di elementi colorabili personalizzati quando l'editor chiama il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> metodo e restituisce un singolo elemento colorabile personalizzato quando l'editor chiama il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> metodo.

 Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> metodo restituisce un oggetto che implementa l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> interfaccia. Se il servizio di linguaggio supporta i valori di colore a 24 bit o alto, deve implementare l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfaccia sullo stesso oggetto dell' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> interfaccia.

## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>Modalità di utilizzo di un color del servizio di linguaggio da un VSPackage

1. Il pacchetto VSPackage deve ottenere il servizio di linguaggio appropriato, che richiede il servizio di linguaggio VSPackage per eseguire le operazioni seguenti:

    1. Usare un oggetto che implementa l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interfaccia per ottenere il testo da colorare.

         Il testo viene in genere visualizzato usando un oggetto che implementa l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaccia.

    2. Ottenere il servizio di linguaggio eseguendo una query sul provider di servizi del pacchetto VSPackage per il GUID del servizio di linguaggio. I servizi di linguaggio vengono identificati nel registro di sistema per estensione di file.

    3. Associare il servizio di linguaggio a chiamando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> relativo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> metodo.

2. Il pacchetto VSPackage ora può ottenere e usare l'oggetto colorante come indicato di seguito:

    > [!NOTE]
    > I pacchetti VSPackage che usano l'editor principale non devono ottenere in modo esplicito gli oggetti coloranti di un servizio di linguaggio. Non appena un'istanza dell'editor principale ottiene un servizio di linguaggio appropriato, esegue tutte le attività di colorazione mostrate qui.

    1. Ottenere l'oggetto coloring del servizio di linguaggio, che implementa le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> interfacce e, chiamando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> metodo sull'oggetto del servizio di linguaggio <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> .

    2. Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodo per ottenere le informazioni sul coloratore per un intervallo di testo specifico.

         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Restituisce una matrice di valori, uno per ogni carattere nell'intervallo di testo da colorare. I valori sono indici in un elenco di elementi colorabili che rappresenta l'elenco di elementi colorabili predefinito gestito dall'editor principale o un elenco di elementi colorabili personalizzato gestito dal servizio di linguaggio stesso.

    3. Usare le informazioni di colorazione restituite dal <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodo per visualizzare il testo selezionato.

> [!NOTE]
> Oltre a usare un coloratore del servizio di linguaggio, un pacchetto VSPackage può usare anche il meccanismo di colorazione del testo di Visual Studio per uso generico. Per ulteriori informazioni su questo meccanismo, vedere [utilizzo di tipi di carattere e colori](/previous-versions/visualstudio/visual-studio-2015/extensibility/using-fonts-and-colors?preserve-view=true&view=vs-2015).

## <a name="in-this-section"></a>Contenuto della sezione
- [Implementazione della colorazione della sintassi](../../extensibility/internals/implementing-syntax-coloring.md)

 Viene illustrato il modo in cui un editor accede alla colorazione della sintassi di un servizio di linguaggio e cosa deve implementare il servizio di linguaggio per supportare la colorazione della sintassi.

- [Procedura: Usare gli elementi colorabili incorporati](../../extensibility/internals/how-to-use-built-in-colorable-items.md)

 Viene illustrato come utilizzare elementi colorabili incorporati dal servizio di linguaggio.

- [Elementi colorabili personalizzati](../../extensibility/internals/custom-colorable-items.md)

 Viene illustrato come implementare elementi colorabili personalizzati.
