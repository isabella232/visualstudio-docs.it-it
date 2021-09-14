---
title: Colorazione della sintassi in un servizio di linguaggio legacy | Microsoft Docs
description: Informazioni su Visual Studio un servizio di colorazione della sintassi in un servizio di linguaggio legacy per identificare gli elementi del linguaggio e visualizzarli in colori in un editor.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring
- language services, syntax coloring
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 0444e435552fafd56b638fa7932e900498836d0d
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626040"
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>Colorazione della sintassi in un servizio di linguaggio legacy

Visual Studio un servizio di colorazione per identificare gli elementi del linguaggio e visualizzarli con i colori specificati in un editor.

## <a name="colorizer-model"></a>Modello colorizer
 Il servizio di linguaggio implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> l'interfaccia , che viene quindi usata dagli editor. Questa implementazione è un oggetto separato dal servizio di linguaggio, come illustrato nella figura seguente:

 ![Rappresentazione grafica dell'applicazione dei colori SVC](../../extensibility/internals/media/figlgsvccolorizer.gif)

> [!NOTE]
> Il servizio di colorazione della sintassi è separato dal meccanismo Visual Studio per colorare il testo. Per altre informazioni sul meccanismo generale che [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] supporta la colorazione, vedere [Uso di tipi di carattere e colori](/previous-versions/visualstudio/visual-studio-2015/extensibility/using-fonts-and-colors?preserve-view=true&view=vs-2015).

 Oltre al colorizer, il servizio di linguaggio può fornire elementi colorabili personalizzati usati dall'editor, indicando che fornisce elementi colorabili personalizzati. A tale scopo, implementare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> l'interfaccia sullo stesso oggetto che implementa l'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> . Restituisce il numero di elementi colorabili personalizzati quando l'editor chiama il metodo e restituisce un singolo elemento colorabile personalizzato quando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> l'editor chiama il metodo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> .

 Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> metodo restituisce un oggetto che implementa l'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> . Se il servizio di linguaggio supporta valori di colore a 24 bit o elevati, deve implementare l'interfaccia sullo stesso <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> dell'interfaccia .

## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>Come un vspackage usa un colorizer del servizio di linguaggio

1. Il pacchetto VSPackage deve ottenere il servizio di linguaggio appropriato, che richiede che il servizio di linguaggio VSPackage eserciti le operazioni seguenti:

    1. Usare un oggetto che implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> l'interfaccia per ottenere il testo da colorare.

         Il testo viene in genere visualizzato usando un oggetto che implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> l'interfaccia .

    2. Ottenere il servizio di linguaggio tramite query sul provider di servizi del pacchetto VSPackage per il GUID del servizio di linguaggio. I servizi di linguaggio vengono identificati nel Registro di sistema in base all'estensione di file.

    3. Associare il servizio di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> linguaggio a chiamando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> relativo metodo .

2. Il pacchetto VSPackage può ora ottenere e usare l'oggetto colorizer come indicato di seguito:

    > [!NOTE]
    > I VSPackage che usano l'editor principale non devono ottenere in modo esplicito gli oggetti colorizer di un servizio di linguaggio. Non appena un'istanza dell'editor principale ottiene un servizio di linguaggio appropriato, esegue tutte le attività di colorazione illustrate qui.

    1. Ottenere l'oggetto colorizer del servizio di linguaggio, che implementa le interfacce , e chiamando il metodo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> sull'oggetto del servizio di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> linguaggio.

    2. Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodo per ottenere le informazioni sul colorizer per un intervallo di testo specifico.

         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> restituisce una matrice di valori, uno per ogni carattere nell'intervallo di testo da colorare. I valori sono indici in un elenco di elementi colorabili che è l'elenco di elementi colorabili predefinito gestito dall'editor principale o un elenco di elementi colorabili personalizzato gestito dal servizio di linguaggio stesso.

    3. Usare le informazioni sulla colorazione restituite dal <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodo per visualizzare il testo selezionato.

> [!NOTE]
> Oltre a usare un colorizer del servizio di linguaggio, un VSPackage può usare anche il meccanismo di colorazione del testo per utilizzo Visual Studio utilizzo generico. Per altre informazioni su questo meccanismo, vedere [Uso di tipi di carattere e colori](/previous-versions/visualstudio/visual-studio-2015/extensibility/using-fonts-and-colors?preserve-view=true&view=vs-2015).

## <a name="in-this-section"></a>Contenuto della sezione
- [Implementazione della colorazione della sintassi](../../extensibility/internals/implementing-syntax-coloring.md)

 Viene illustrato come un editor accede alla colorazione della sintassi di un servizio di linguaggio e cosa deve implementare il servizio di linguaggio per supportare la colorazione della sintassi.

- [Procedura: Usare gli elementi colorabili incorporati](../../extensibility/internals/how-to-use-built-in-colorable-items.md)

 Illustra come usare elementi colorabili predefiniti dal servizio di linguaggio.

- [Elementi colorabili personalizzati](../../extensibility/internals/custom-colorable-items.md)

 Viene illustrato come implementare elementi colorabili personalizzati.
