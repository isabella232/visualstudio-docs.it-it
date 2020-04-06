---
title: Informazioni sui parametri in un servizio di linguaggio Legacy1 Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, method tips
- method tips
- language services, parameter info tooltip
- IVsMethodData interface
- Parameter Info (IntelliSense)
ms.assetid: f367295e-45b6-45d2-9ec8-77481743beef
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c26073252aae5434ba5a8197955948d0d9ec883d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706793"
---
# <a name="parameter-info-in-a-legacy-language-service"></a>Informazioni sui parametri in un servizio di linguaggio legacy
La descrizione comando Informazioni sui parametri IntelliSense fornisce agli utenti suggerimenti sulla posizione in cui si trovano in un costrutto di linguaggio.

 Servizi di linguaggio legacy vengono implementati come parte di un VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'utilizzare le estensioni MEF. Per ulteriori informazioni, vedere [Estensione dell'editor e](../../extensibility/extending-the-editor-and-language-services.md)dei servizi di linguaggio .

> [!NOTE]
> Si consiglia di iniziare a utilizzare la nuova API dell'editor il prima possibile. Ciò migliorerà le prestazioni del servizio di linguaggio e consentirà di sfruttare le nuove funzionalità dell'editor.

## <a name="how-parameter-info-tooltips-work"></a>Funzionamento delle descrizioni comandi delle informazioni sui parametri
 Quando si digita un'istruzione nell'editor, il pacchetto VSPackage viene visualizzata una piccola finestra di descrizione comando contenente la definizione dell'istruzione da digitare. Se ad esempio si digita un'istruzione MFC (Microsoft Foundation Classes) (ad `pMainFrame ->UpdateWindow`esempio ) e si preme la `UpdateWindow` parentesi di apertura per iniziare a elencare i parametri, viene visualizzato un suggerimento per il metodo che visualizza la definizione del metodo.

 Le descrizioni comandi Informazioni parametro vengono in genere utilizzate insieme al completamento delle istruzioni. Sono particolarmente utili per le lingue che dispongono di parametri o altre informazioni formattate dopo il nome del metodo o la parola chiave.

 Le descrizioni comandi Di informazioni parametro vengono avviate dal servizio di linguaggio tramite l'intercettazione dei comandi. Per intercettare i caratteri utente, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> l'oggetto servizio di linguaggio <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> deve implementare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> l'interfaccia e passare la visualizzazione di testo un puntatore all'implementazione, chiamando il metodo nell'interfaccia. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Il comando filter intercetta i comandi digitati nella finestra del codice. Monitorare le informazioni sul comando per sapere quando visualizzare le informazioni sui parametri all'utente. È possibile utilizzare lo stesso filtro di comando per il completamento delle istruzioni, gli indicatori di errore e così via.

 Quando si digita una parola chiave per cui il servizio di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> linguaggio <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> può fornire <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> suggerimenti, il servizio di linguaggio crea un oggetto e chiama il metodo nell'interfaccia per notificare all'IDE di visualizzare un suggerimento. Creare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> l'oggetto utilizzando `VSLocalCreateInstance` e `CLSID_VsMethodTipWindow`specificando la coclasse . `VsLocalCreateInstance`è una funzione definita nel file di `QueryService` intestazione vsdoc.h che richiede il Registro di sistema locale e le chiamate `CreateInstance` su questo oggetto per l'oggetto `CLSID_VsMethodTipWindow`.

## <a name="providing-a-method-tip"></a>Fornire un suggerimento per il metodo
 Per fornire un suggerimento <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> per <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> il metodo, chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> metodo nell'interfaccia, passandol'implementazione dell'interfaccia.

 Quando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> la classe viene richiamata, i relativi metodi vengono chiamati nel seguente ordine:

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>

     Restituisce la posizione e la lunghezza dei dati rilevanti nel buffer di testo corrente. In questo modo l'IDE non nascondere i dati con la finestra della descrizione comandi.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>

     Restituisce il numero del metodo (indice in base zero) che si desidera visualizzare inizialmente. Ad esempio, se si restituisce zero, viene inizialmente presentato il primo metodo di overload.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>

     Restituisce il numero di metodi di overload applicabili nel contesto corrente. Se si restituisce un valore maggiore di 1 per questo metodo, la visualizzazione di testo visualizza le frecce su e giù per l'utente. Se si fa clic sulla freccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A> giù, l'IDE chiama il metodo. Se si fa clic sulla freccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A> su, l'IDE chiama il metodo.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>

     Il testo della descrizione comando Informazioni parametro <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A> viene costruito durante diverse chiamate ai metodi e .

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>

     Restituisce il numero di parametri da visualizzare nel metodo.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>

     Se si restituisce un numero di metodo corrispondente all'overload che si desidera <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> visualizzare, viene chiamato questo metodo, seguito da una chiamata al metodo.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>

     Informa il servizio di linguaggio per aggiornare l'editor quando viene visualizzato un suggerimento per il metodo. Nel <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> metodo, chiamare quanto segue:

    ```
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).
    ```

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>

     Si riceve una <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> chiamata al metodo quando si chiude la finestra di suggerimento metodo.
