---
title: Informazioni sui parametri in un servizio di linguaggio legacy Service1 | Microsoft Docs
description: Informazioni su come implementare la descrizione comando Informazioni sui parametri di IntelliSense, che fornisce suggerimenti agli utenti, in un servizio di linguaggio legacy.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, method tips
- method tips
- language services, parameter info tooltip
- IVsMethodData interface
- Parameter Info (IntelliSense)
ms.assetid: f367295e-45b6-45d2-9ec8-77481743beef
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 715b9c5aa672fae29b349f30470e1f6e210f1ff926cf447c08bc4e0528eca416
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121275476"
---
# <a name="parameter-info-in-a-legacy-language-service-1"></a>Informazioni sui parametri in un servizio di linguaggio legacy 1
La descrizione comando Informazioni sui parametri di IntelliSense fornisce agli utenti suggerimenti sulla posizione in cui si trova in un costrutto di linguaggio.

 I servizi di linguaggio legacy vengono implementati come parte di un PACCHETTO VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio è usare le estensioni MEF. Per altre informazioni, vedere Estensione [dell'editor e dei servizi di linguaggio.](../../extensibility/extending-the-editor-and-language-services.md)

> [!NOTE]
> È consigliabile iniziare a usare la nuova API dell'editor appena possibile. Ciò consente di migliorare le prestazioni del servizio di linguaggio e di sfruttare le nuove funzionalità dell'editor.

## <a name="how-parameter-info-tooltips-work"></a>Funzionamento delle descrizioni comando delle informazioni sui parametri
 Quando si digita un'istruzione nell'editor, il pacchetto VSPackage visualizza una piccola finestra della descrizione comando contenente la definizione dell'istruzione digitata. Ad esempio, se si digita un'istruzione Microsoft Foundation Classes (MFC) (ad esempio ) e si preme la parentesi di apertura per iniziare a elencare i parametri, viene visualizzata una descrizione del metodo con la definizione del `pMainFrame ->UpdateWindow` `UpdateWindow` metodo.

 Le descrizioni comando delle informazioni sui parametri vengono in genere usate in combinazione con il completamento delle istruzioni. Sono particolarmente utili per i linguaggi che dispongono di parametri o altre informazioni formattate dopo il nome del metodo o la parola chiave .

 Le descrizioni comando delle informazioni sui parametri vengono avviate dal servizio di linguaggio tramite l'intercettazione dei comandi. Per intercettare i caratteri utente, l'oggetto del servizio di linguaggio deve implementare l'interfaccia e passare alla visualizzazione testo un puntatore all'implementazione chiamando il metodo <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> nell'interfaccia . Il filtro comandi intercetta i comandi digitati nella finestra del codice. Monitorare le informazioni sui comandi per sapere quando visualizzare le informazioni sui parametri all'utente. È possibile usare lo stesso filtro di comando per il completamento delle istruzioni, i marcatori di errore e così via.

 Quando si digita una parola chiave per la quale il servizio di linguaggio può fornire suggerimenti, il servizio di linguaggio crea un oggetto e chiama il metodo nell'interfaccia per notificare all'IDE di visualizzare un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> suggerimento. Creare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> l'oggetto `VSLocalCreateInstance` usando e specificando la coclasse `CLSID_VsMethodTipWindow` . `VsLocalCreateInstance` è una funzione definita nel file di intestazione vsdoc.h che chiama per il Registro di sistema locale e chiama su `QueryService` `CreateInstance` questo oggetto per `CLSID_VsMethodTipWindow` .

## <a name="providing-a-method-tip"></a>Fornire un suggerimento sul metodo
 Per fornire una descrizione del metodo, chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> il metodo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> nell'interfaccia , passando l'implementazione <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> dell'interfaccia .

 Quando la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> classe viene richiamata, i relativi metodi vengono chiamati nell'ordine seguente:

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>

     Restituisce la posizione e la lunghezza dei dati pertinenti nel buffer di testo corrente. Questo indica all'IDE di non nascondere i dati con la finestra della descrizione comando.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>

     Restituisce il numero del metodo (indice in base zero) che si desidera visualizzare inizialmente. Ad esempio, se si restituisce zero, viene inizialmente presentato il primo metodo di overload.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>

     Restituisce il numero di metodi di overload applicabili nel contesto corrente. Se si restituisce un valore maggiore di 1 per questo metodo, la visualizzazione testo visualizza automaticamente le frecce su e giù. Se si fa clic sulla freccia verso il basso, l'IDE chiama il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A> metodo . Se si fa clic sulla freccia in su, l'IDE chiama il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A> metodo .

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>

     Il testo della descrizione comando Informazioni parametro viene costruito durante diverse chiamate ai <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A> metodi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A> e .

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>

     Restituisce il numero di parametri da visualizzare nel metodo.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>

     Se si restituisce un numero di metodo corrispondente all'overload da visualizzare, questo metodo viene chiamato, seguito da una chiamata al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> metodo .

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>

     Informa il servizio di linguaggio di aggiornare l'editor quando viene visualizzata una descrizione del metodo. Nel metodo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> chiamare quanto segue:

    ```
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).
    ```

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>

     Si riceve una chiamata al metodo quando si chiude la finestra del <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> suggerimento del metodo.
