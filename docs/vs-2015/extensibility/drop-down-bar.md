---
title: Barra a discesa | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - drop-down bar
ms.assetid: 4bb621bd-72f5-43d5-916f-9f66617da049
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7db4296a8fa4146a52d167bce3d8b051aa3ca073
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204639"
---
# <a name="drop-down-bar"></a>Barra a discesa
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La barra a discesa è disponibile nella parte superiore della finestra del codice e contiene due elenchi a discesa.  
  
## <a name="drop-down-bar-interfaces"></a>Interfacce della barra a discesa  
 In [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] , ad esempio, la barra a discesa contiene elenchi per le [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] funzioni membro Items e [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] Items, come illustrato nell'immagine seguente.  
  
 ![Elimina&#45;barre giù](../extensibility/media/vsdropdown-bar.gif "vsDropdown_bar")  
Barra a discesa  
  
 Quando si implementa una barra a discesa, sono disponibili quattro interfacce di importanza primaria:  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient>  
  
     Implementare questa interfaccia per inserire il contenuto della barra a discesa. Ogni combinazione di menu a discesa può contenere testo normale o testo (in grassetto, sottolineatura o corsivo), può avere una colorazione dei tipi di carattere del testo della finestra o colorazione dei tipi di carattere in grigio e facoltativamente può fornire una piccola bitmap accanto all'elemento a discesa. Analogamente all' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> interfaccia, le immagini bitmap vengono fornite negli elenchi di immagini. Ogni combinazione a discesa può avere un elenco di immagini diverso; ogni elenco di immagini, tuttavia, deve contenere immagini della stessa altezza. Inoltre, utilizzando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient.GetComboTipText%2A> metodo, è possibile fornire una descrizione comando per ogni combinazione.  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>  
  
     Chiamare questa interfaccia per creare o eliminare definitivamente la barra a discesa per una finestra del codice. Questa interfaccia può essere utilizzata anche per determinare se una barra a discesa è già collegata a una finestra del codice chiamando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> metodo. Chiamare <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> per <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> da <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> .  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>  
  
     Chiamare questa interfaccia per comunicare direttamente con la barra a discesa. È possibile utilizzare questa interfaccia per forzare un aggiornamento del contenuto della barra a discesa o per modificare la selezione in una delle caselle di riepilogo.  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents>  
  
     Se la `ShowDropdownBarOption` nella chiave del registro di sistema del servizio di linguaggio è stata registrata, è necessario che il gestore della finestra del codice esegua il monitoraggio di questo evento per la sincronizzazione con le preferenze dell'utente in merito all'eventuale visualizzazione della barra a discesa. Se questa opzione non viene registrata nella chiave del servizio di linguaggio, l'opzione per visualizzare o nascondere la barra a discesa è disabilitata nel menu **Opzioni** .  
  
## <a name="attaching-a-drop-down-bar-to-a-code-window"></a>Connessione di una barra a discesa a una finestra del codice  
 Per allineare una barra a discesa alla finestra del codice quando viene creata, un servizio di linguaggio deve collegarsi alla barra a discesa quando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> viene chiamato il metodo. Se una chiamata al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> metodo indica che una barra a discesa non esiste già, chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.AddDropdownBar%2A> . Per accedere all' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> interfaccia, chiamare <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> dal <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> puntatore restituito quando l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> implementazione è stata collegata.  
  
## <a name="see-also"></a>Vedere anche  
 [Personalizzazione delle finestre di codice tramite l'API legacy](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)   
 [Supporto per la barra di spostamento in un servizio di linguaggio legacy](../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)
