---
title: Informazioni sui parametri in un servizio di linguaggio legacy1 | Microsoft Docs
description: Informazioni su come implementare la descrizione comando IntelliSense Parameter Info, che fornisce agli utenti suggerimenti, in un servizio di linguaggio legacy.
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
ms.openlocfilehash: b8c3a0cdec47be7ce5d29ff5b43ac6cd7e05cc07
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709530"
---
# <a name="parameter-info-in-a-legacy-language-service-1"></a>Informazioni sui parametri in un servizio di linguaggio legacy 1
La descrizione comando IntelliSense Parameter Info fornisce agli utenti suggerimenti sulla posizione in cui si trova in un costrutto di linguaggio.

 I servizi di linguaggio legacy vengono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio è usare le estensioni MEF. Per altre informazioni, vedere [Estensione dell'editor e di Servizi di linguaggio](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> È consigliabile iniziare a usare la nuova API dell'editor appena possibile. In questo modo si miglioreranno le prestazioni del servizio di linguaggio e si potranno sfruttare le nuove funzionalità dell'editor.

## <a name="how-parameter-info-tooltips-work"></a>Funzionamento delle descrizioni comando per le informazioni sui parametri
 Quando si digita un'istruzione nell'editor, il pacchetto VSPackage visualizza una piccola finestra della descrizione comando contenente la definizione dell'istruzione da digitare. Ad esempio, se si digita un'istruzione Microsoft Foundation Classes (MFC), ad esempio , e si preme la parentesi di apertura per iniziare a elencare i parametri, viene visualizzata una descrizione del metodo che visualizza la definizione del `pMainFrame ->UpdateWindow` `UpdateWindow` metodo.

 Le descrizioni comando relative alle informazioni sui parametri vengono in genere usate insieme al completamento dell'istruzione. Sono particolarmente utili per i linguaggi con parametri o altre informazioni formattate dopo il nome o la parola chiave del metodo.

 Le descrizioni comando relative alle informazioni sui parametri vengono avviate dal servizio di linguaggio tramite l'intercettazione dei comandi. Per intercettare i caratteri utente, l'oggetto del servizio di linguaggio deve implementare l'interfaccia e passare alla visualizzazione testo un puntatore all'implementazione chiamando il metodo <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> nell'interfaccia . Il filtro dei comandi intercetta i comandi digitati nella finestra del codice. Monitorare le informazioni sul comando per sapere quando visualizzare le informazioni sui parametri per l'utente. È possibile usare lo stesso filtro di comando per il completamento dell'istruzione, i marcatori di errore e così via.

 Quando si digita una parola chiave per cui il servizio di linguaggio può fornire suggerimenti, il servizio di linguaggio crea un oggetto e chiama il metodo nell'interfaccia per notificare all'IDE di visualizzare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> suggerimento. Creare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> l'oggetto `VSLocalCreateInstance` usando e specificando la coclasse `CLSID_VsMethodTipWindow` . `VsLocalCreateInstance` è una funzione definita nel file di intestazione vsdoc.h che chiama per il Registro di sistema locale e chiama su questo `QueryService` `CreateInstance` oggetto per `CLSID_VsMethodTipWindow` .

## <a name="providing-a-method-tip"></a>Fornire una descrizione comando per il metodo
 Per fornire una descrizione del metodo, chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> il metodo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> nell'interfaccia , passando l'implementazione <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> dell'interfaccia .

 Quando la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> classe viene richiamata, i relativi metodi vengono chiamati nell'ordine seguente:

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>

     Restituisce la posizione e la lunghezza dei dati rilevanti nel buffer di testo corrente. Questo indica all'IDE di non nascondere i dati con la finestra della descrizione comando.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>

     Restituisce il numero del metodo (indice in base zero) che si desidera visualizzare inizialmente. Ad esempio, se si restituisce zero, viene presentato inizialmente il primo metodo di overload.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>

     Restituisce il numero di metodi di overload applicabili nel contesto corrente. Se si restituisce un valore maggiore di 1 per questo metodo, nella visualizzazione testo vengono visualizzate automaticamente le frecce su e giù. Se si fa clic sulla freccia giù, l'IDE chiama il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A> metodo . Se si fa clic sulla freccia su, l'IDE chiama il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A> metodo .

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>

     Il testo della descrizione comando Informazioni parametro viene costruito durante diverse chiamate ai <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A> metodi e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A> .

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>

     Restituisce il numero di parametri da visualizzare nel metodo .

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>

     Se si restituisce un numero di metodo corrispondente all'overload da visualizzare, questo metodo viene chiamato, seguito da una chiamata al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> metodo .

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>

     Informa il servizio di linguaggio di aggiornare l'editor quando viene visualizzata una descrizione comando del metodo. Nel metodo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> chiamare quanto segue:

    ```
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).
    ```

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>

     Si riceve una chiamata al metodo quando si chiude la finestra di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> suggerimento del metodo.
