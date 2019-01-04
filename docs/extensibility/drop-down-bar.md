---
title: Barra di riepilogo a discesa | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - drop-down bar
ms.assetid: 4bb621bd-72f5-43d5-916f-9f66617da049
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0a23249a80b87c55e3065abb7cca192182aad4fb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53968063"
---
# <a name="drop-down-bar"></a>Barra di riepilogo a discesa
La barra di riepilogo a discesa viene fornita nella parte superiore della finestra del codice e contiene due elenchi a discesa.  
  
## <a name="drop-down-bar-interfaces"></a>Interfacce dell'elenco a discesa barra  
 Nelle [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], ad esempio, la barra di riepilogo a discesa contiene gli elenchi per [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] gli elementi e [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] le funzioni membro di elementi, come illustrato nell'immagine seguente.  
  
 ![Eliminare&#45;verso il basso le barre](../extensibility/media/vsdropdown_bar.gif "vsDropdown_bar")  
Barra di riepilogo a discesa  
  
 Quando si implementa una barra di riepilogo a discesa, esistono quattro interfacce di primaria importanza:  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient>  
  
     Implementare questa interfaccia per inserire il contenuto della barra di riepilogo a discesa. Ogni combinazione di elenco a discesa può contenere testo artistico o testo normale (grassetto, sottolineatura o corsivo), può disporre di colorazione del tipo di carattere del testo finestra o tipo di carattere grigio colorazione e può facoltativamente specificare una bitmap di ridotte dimensioni accanto alla voce dell'elenco a discesa. Simile al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> interfaccia, le immagini bitmap sono fornite negli elenchi di immagini. Ogni combinazione di elenco a discesa può avere un elenco di immagini diverse; Tuttavia, ogni elenco di immagini deve contenere le immagini della stessa altezza. Inoltre, tramite il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient.GetComboTipText%2A> metodo, è possibile fornire una descrizione comando per ogni combinazione.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>  
  
     Chiamare questa interfaccia per creare o eliminare definitivamente la barra di riepilogo a discesa di una finestra del codice. L'interfaccia può essere utilizzata anche per determinare se una barra di riepilogo a discesa è già collegata a una finestra del codice tramite la chiamata di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> (metodo). Chiamare <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> per <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> da <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>  
  
     Chiamare questa interfaccia per comunicare direttamente con la barra di riepilogo a discesa. È possibile utilizzare questa interfaccia per forzare un aggiornamento dell'elenco a discesa della barra di contenuto o per modificare la selezione in una delle caselle di riepilogo.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents>  
  
     Se è stato registrato il `ShowDropdownBarOption` chiave del Registro di sistema del servizio linguaggio, quindi la gestione di finestre di codice deve monitorare questo evento per la sincronizzazione con le preferenze dell'utente relative alle indica se deve essere visualizzata la barra di elenco a discesa. Se questa opzione non si registrano la chiave di servizio di linguaggio, quindi l'opzione per mostrare o nascondere la barra di riepilogo a discesa è disabilitata nel **opzioni** menu.  
  
## <a name="attach-a-drop-down-bar-to-a-code-window"></a>Collegare una barra di riepilogo a discesa a una finestra del codice  
 Per collegare una barra di riepilogo a discesa per la finestra del codice quando viene creato, un servizio di linguaggio deve essere connesso al menu a discesa barra quando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> viene chiamato il metodo. Se una chiamata ai <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> metodo indica che una barra di riepilogo a discesa non è già presente, quindi chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.AddDropdownBar%2A>. Per l'accesso di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> l'interfaccia, chiamare <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> dal <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> puntatore restituito all'utente quando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> implementazione è stata collegata.  
  
## <a name="see-also"></a>Vedere anche  
 [Personalizzare le finestre di codice usando l'API legacy](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)   
 [Supporto per la barra di spostamento in un servizio di linguaggio legacy](../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)