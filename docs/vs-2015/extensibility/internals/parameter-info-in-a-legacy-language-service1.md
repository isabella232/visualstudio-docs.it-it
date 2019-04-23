---
title: Informazioni sui parametri in un tipo di linguaggio legacy1 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, method tips
- method tips
- language services, parameter info tooltip
- IVsMethodData interface
- Parameter Info (IntelliSense)
ms.assetid: f367295e-45b6-45d2-9ec8-77481743beef
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b02db44cef8734f70f81847b224bc007fe1b4500
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60114002"
---
# <a name="parameter-info-in-a-legacy-language-service"></a>Informazioni sui parametri in un servizio di linguaggio Legacy
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La descrizione comando informazioni sul parametro di IntelliSense offre agli utenti con suggerimenti su dove si trovano in un costrutto di linguaggio.  
  
 Servizi di linguaggio legacy vengono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'usare le estensioni MEF. Per altre informazioni, vedere [estensione dell'Editor e servizi di linguaggio](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  È consigliabile che si inizia a usare il nuovo editor delle API appena possibile. Verrà migliorare le prestazioni del servizio di linguaggio e consentono di sfruttare nuove funzionalità dell'editor.  
  
## <a name="how-parameter-info-tooltips-work"></a>Come funzionano le descrizioni comandi informazioni parametro  
 Quando si digita un'istruzione nell'editor, il pacchetto VSPackage Visualizza una finestra piccola della descrizione comando contenente la definizione dell'istruzione la digitazione. Ad esempio, se si digita un'istruzione di Microsoft Foundation Classes (MFC) (ad esempio `pMainFrame ->UpdateWindow`) e premere un tasto della parentesi di apertura per iniziare a elencare i parametri, viene visualizzato un suggerimento sul metodo visualizzazione della definizione del `UpdateWindow` (metodo).  
  
 Le descrizioni comandi informazioni di parametro vengono in genere usate in combinazione con il completamento delle istruzioni. Sono particolarmente utili per linguaggi che dispongono di parametri o altra informazione formattata dopo la parola chiave o il nome del metodo.  
  
 Le descrizioni comandi informazioni sul parametro possono essere avviate dal servizio di linguaggio tramite intercettazione dei comandi. Per intercettare i caratteri di utente, è necessario implementare l'oggetto servizio di linguaggio il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> l'interfaccia e passare un puntatore per la visualizzazione di testo il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implementazione, chiamando la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metodo nella <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaccia. Il filtro di comando intercetta comandi digitati nella finestra del codice. Monitorare le informazioni sui comandi per sapere quando visualizzare informazioni sui parametri per l'utente. È possibile usare lo stesso filtro di comando per il completamento delle istruzioni, i marcatori di errore e così via.  
  
 Quando si digita una parola chiave per il quale il servizio di linguaggio consente di fornire suggerimenti, quindi il servizio di linguaggio crea un' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> oggetto e chiama il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> metodo nella <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaccia per notificare l'IDE per visualizzare un suggerimento. Creare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> dell'oggetto usando `VSLocalCreateInstance` e specificando la coclasse `CLSID_VsMethodTipWindow`. `VsLocalCreateInstance` è una funzione definita nel vsdoc.h di file di intestazione che chiama `QueryService` per il Registro di sistema locale e chiama `CreateInstance` tohoto objektu per il `CLSID_VsMethodTipWindow`.  
  
## <a name="providing-a-method-tip"></a>Fornire un suggerimento sul metodo  
 Per fornire un suggerimento sul metodo, chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> metodo nella <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> interfaccia, passandogli l'implementazione del <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> interfaccia.  
  
 Quando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> classe viene richiamata, i relativi metodi vengono chiamati nell'ordine seguente:  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>  
  
     Restituisce la posizione e lunghezza dei dati rilevanti nel buffer di testo corrente. Questo indica all'IDE di non nasconda tali dati con la finestra di descrizione comando.  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>  
  
     Restituisce il numero di metodo (indice in base zero), che si dovrà essere visualizzato inizialmente. Ad esempio, se si restituisce zero, quindi il primo metodo di overload viene inizialmente visualizzato.  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>  
  
     Restituisce il numero di metodi di overload applicabili nel contesto corrente. Se si restituisce un valore maggiore di 1 per questo metodo, quindi la visualizzazione di testo Visualizza frecce su e giù per l'utente. Se si fa clic sulla freccia in giù, l'IDE chiama il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A> (metodo). Se si fa clic sulla freccia in su, l'IDE chiama il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A> (metodo).  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>  
  
     Il testo della descrizione comando informazioni sul parametro è stato costruito durante diverse chiamate per il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A> metodi.  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>  
  
     Restituisce il numero di parametri da visualizzare nel metodo.  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>  
  
     Se si restituisce un numero di metodo corrispondente con l'overload che si desidera visualizzare, questo metodo viene chiamato, seguita da una chiamata al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> (metodo).  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>  
  
     Informa il servizio di linguaggio per aggiornare l'editor quando viene visualizzato un suggerimento di metodo. Nel <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> metodo, chiamare il comando seguente:  
  
    ```  
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).  
    ```  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>  
  
     Si riceve una chiamata al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> metodo quando si chiude la finestra di suggerimento di metodo.
