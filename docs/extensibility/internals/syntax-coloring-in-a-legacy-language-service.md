---
title: Colorazione della sintassi in un servizio di linguaggio Legacy Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring
- language services, syntax coloring
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2589ec24f230287306e0ff7e802d381fb6ab18b7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704752"
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>Colorazione della sintassi in un servizio di linguaggio legacy

Visual Studio usa un servizio di colorazione per identificare gli elementi del linguaggio e visualizzarli con i colori specificati in un editor.

## <a name="colorizer-model"></a>Modello Colorizer
 Il servizio di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> linguaggio implementa l'interfaccia, che viene quindi utilizzata dagli editor. Questa implementazione è un oggetto separato dal servizio di linguaggio, come illustrato nella figura seguente:This implementation is a separate object from the language service, as shown in the following illustration:

 ![Rappresentazione grafica dell'applicazione dei colori SVC](../../extensibility/internals/media/figlgsvccolorizer.gif)

> [!NOTE]
> Il servizio di colorazione della sintassi è separato dal meccanismo generale di Visual Studio per la colorazione del testo. Per ulteriori informazioni [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] sul meccanismo generale di supporto della colorazione, consultate [Utilizzo di tipi di carattere e colori.](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015)

 Oltre al colorizer, il servizio di linguaggio può fornire elementi colorabili personalizzati che vengono utilizzati dall'editor, pubblicizzando che fornisce elementi colorabili personalizzati. A tale scopo, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> è possibile implementare l'interfaccia sullo stesso oggetto che implementa l'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> . Restituisce il numero di elementi colorabili <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> personalizzati quando l'editor chiama il metodo e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> restituisce un singolo elemento colorabile personalizzato quando l'editor chiama il metodo.

 Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> metodo restituisce un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> oggetto che implementa l'interfaccia . Se il servizio di linguaggio supporta valori di colore <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> a 24 bit <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> o alti, deve implementare l'interfaccia sullo stesso oggetto dell'interfaccia.

## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>Come un VSPackage utilizza un colorizer del servizio di linguaggioHow a VSPackage Uses a Language Service Colorizer

1. Il pacchetto VSPackage deve ottenere il servizio di linguaggio appropriato, che richiede il servizio di linguaggio VSPackage per eseguire le operazioni seguenti:The VSPackage must get the appropriate language service, which requires the language service VSPackage to do the following:

    1. Utilizzare un oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> che implementa l'interfaccia per ottenere il testo da colorare.

         Il testo viene in genere visualizzato <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> utilizzando un oggetto che implementa l'interfaccia .

    2. Ottenere il servizio di linguaggio eseguendo una query sul provider di servizi del pacchetto VSPackage per il GUID del servizio di linguaggio. I servizi di linguaggio sono identificati nel Registro di sistema dall'estensione del file.

    3. Associare il servizio <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> linguaggio a tramite la chiamata al relativo metodo.

2. Il pacchetto VSPackage può ora ottenere e utilizzare l'oggetto colorizer come indicato di seguito:The VSPackage can now obtain and use the colorizer object as follows:

    > [!NOTE]
    > VSPackage che utilizzano l'editor di base non è necessario ottenere gli oggetti colorizer di un servizio di linguaggio in modo esplicito. Non appena un'istanza dell'editor principale ottiene un servizio di linguaggio appropriato, esegue tutte le attività di colorazione illustrate di seguito.

    1. Ottenere l'oggetto colorizer del servizio <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> linguaggio, che <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> implementa le interfacce <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> e , chiamando il metodo sull'oggetto del servizio di linguaggio.

    2. Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> il metodo per ottenere le informazioni sul colorizer per un determinato intervallo di testo.

         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>restituisce una matrice di valori, uno per ogni carattere dell'intervallo di testo da colorare. I valori sono indici in un elenco di elementi colorabili che è l'elenco di elementi colorabili predefinito gestito dall'editor principale o un elenco di elementi colorabili personalizzato gestito dal servizio di linguaggio stesso.

    3. Utilizzare le informazioni di colorazione restituite dal <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodo per visualizzare il testo selezionato.

> [!NOTE]
> Oltre a usare un colorizer del servizio di linguaggio, un VSPackage può anche usare il meccanismo di colorazione del testo di Visual Studio di uso generale. Per ulteriori informazioni su questo meccanismo, consultate Utilizzo di tipi di [carattere e colori.](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015)

## <a name="in-this-section"></a>Contenuto della sezione
- [Implementazione della colorazione della sintassi](../../extensibility/internals/implementing-syntax-coloring.md)

 Viene illustrato come un editor accede alla colorazione della sintassi di un servizio di linguaggio e cosa deve implementare il servizio di linguaggio per supportare la colorazione della sintassi.

- [Procedura: Usare gli elementi colorabili incorporati](../../extensibility/internals/how-to-use-built-in-colorable-items.md)

 Viene illustrato come utilizzare gli elementi colorabili incorporati dal servizio di linguaggio.

- [Elementi colorabili personalizzati](../../extensibility/internals/custom-colorable-items.md)

 Viene illustrato come implementare elementi colorabili personalizzati.
