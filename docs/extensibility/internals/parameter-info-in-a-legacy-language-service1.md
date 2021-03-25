---
title: Informazioni sui parametri in un oggetto Service1 della lingua legacy | Microsoft Docs
description: Informazioni su come implementare la descrizione comando di IntelliSense per informazioni sul parametro, che fornisce agli utenti gli hint in un servizio di linguaggio legacy.
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
ms.workload:
- vssdk
ms.openlocfilehash: 4dade924ef89be22161c598ba0ae64084c0697ea
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105061147"
---
# <a name="parameter-info-in-a-legacy-language-service-1"></a>Informazioni sui parametri in un servizio di linguaggio Legacy 1
La descrizione comando informazioni parametri IntelliSense fornisce agli utenti suggerimenti sulla posizione in cui si trovano in un costrutto di linguaggio.

 I servizi di linguaggio legacy sono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'usare le estensioni MEF. Per ulteriori informazioni, vedere [estensione dei servizi di editor e di linguaggio](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Si consiglia di iniziare a usare la nuova API editor appena possibile. Ciò consente di migliorare le prestazioni del servizio di linguaggio e di sfruttare i vantaggi delle nuove funzionalità dell'editor.

## <a name="how-parameter-info-tooltips-work"></a>Funzionamento delle descrizioni comandi delle informazioni sui parametri
 Quando si digita un'istruzione nell'editor, il pacchetto VSPackage Visualizza una piccola finestra descrizione comando contenente la definizione dell'istruzione digitata. Se ad esempio si digita un'istruzione Microsoft Foundation Classes (MFC), ad esempio, `pMainFrame ->UpdateWindow` e si preme il tasto parentesi di apertura per iniziare a elencare i parametri, viene visualizzato un suggerimento sul metodo che visualizza la definizione del `UpdateWindow` metodo.

 Le descrizioni comandi delle informazioni sui parametri vengono in genere utilizzate in combinazione con il completamento delle istruzioni. Sono particolarmente utili per i linguaggi con parametri o altre informazioni formattate dopo il nome del metodo o la parola chiave.

 Le descrizioni comandi delle informazioni sui parametri vengono avviate dal servizio di linguaggio tramite l'intercettazione dei comandi. Per intercettare i caratteri utente, l'oggetto servizio di linguaggio deve implementare l' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia e passare la visualizzazione di testo un puntatore all' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implementazione, chiamando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metodo nell' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaccia. Il filtro comandi intercetta i comandi digitati nella finestra del codice. Monitorare le informazioni sul comando per stabilire quando visualizzare le informazioni sui parametri per l'utente. È possibile utilizzare lo stesso filtro di comando per il completamento delle istruzioni, i marcatori di errore e così via.

 Quando si digita una parola chiave per la quale il servizio di linguaggio può fornire hint, il servizio di linguaggio crea un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> oggetto e chiama il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> metodo nell' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaccia per notificare all'IDE di visualizzare un suggerimento. Creare l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> oggetto usando `VSLocalCreateInstance` e specificando la coclasse `CLSID_VsMethodTipWindow` . `VsLocalCreateInstance` è una funzione definita nel file di intestazione vsdoc. h che chiama `QueryService` il registro di sistema locale e chiama `CreateInstance` su questo oggetto per `CLSID_VsMethodTipWindow` .

## <a name="providing-a-method-tip"></a>Fornire un suggerimento sul metodo
 Per fornire un suggerimento sul metodo, chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> metodo nell' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> interfaccia e passargli l'implementazione dell' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> interfaccia.

 Quando la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> classe viene richiamata, i relativi metodi vengono chiamati nell'ordine seguente:

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>

     Restituisce la posizione e la lunghezza dei dati rilevanti nel buffer di testo corrente. Ciò indica all'IDE di non nascondere i dati con la finestra della descrizione comando.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>

     Restituisce il numero di metodo (indice in base zero) che si desidera visualizzare inizialmente. Se, ad esempio, si restituisce zero, viene inizialmente presentato il primo metodo di overload.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>

     Restituisce il numero di metodi di overload applicabili nel contesto corrente. Se si restituisce un valore maggiore di 1 per questo metodo, la visualizzazione di testo Visualizza le frecce verso l'alto e verso il basso. Se si fa clic sulla freccia verso il basso, l'IDE chiama il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A> metodo. Se si fa clic sulla freccia rivolta verso l'alto, l'IDE chiama il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A> metodo.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>

     Il testo della descrizione comando informazioni parametri viene costruito durante varie chiamate ai <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A> metodi e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A> .

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>

     Restituisce il numero di parametri da visualizzare nel metodo.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>

     Se si restituisce un numero di metodo corrispondente all'overload che si vuole visualizzare, questo metodo viene chiamato, seguito da una chiamata al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> metodo.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>

     Informa il servizio di linguaggio di aggiornare l'editor quando viene visualizzato un suggerimento sul metodo. Nel <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> metodo chiamare quanto segue:

    ```
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).
    ```

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>

     Si riceve una chiamata al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> metodo quando si chiude la finestra del suggerimento sul metodo.
