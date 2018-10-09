---
title: 'Procedura: fornire il contesto per gli editor | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - provide context
ms.assetid: 12df4d06-df6b-4eaf-a7bf-c83655a0c683
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9509dfeef5af4866531af96fce6f4c1717100a94
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47531166"
---
# <a name="how-to-provide-context-for-editors"></a>Procedura: fornire il contesto per gli editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura: fornire contesto per gli editor](https://docs.microsoft.com/visualstudio/extensibility/how-to-provide-context-for-editors).  
  
Per un editor, il contesto è attivo solo quando l'editor ha lo stato attivo o lo stato attivo immediatamente prima che lo stato attivo è stato spostato in una finestra degli strumenti. È possibile fornire contesto per un editor eseguendo queste operazioni:  
  
1.  Creare un contenitore di contesto.  
  
2.  Pubblicare il contenitore di contesto per l'identificatore di elemento di selezione (SEID).  
  
3.  Mantenere il contesto nel contenitore.  
  
 Queste attività sono coperte da procedure riportate di seguito. Per altre informazioni su come fornire contesto, vedere **programmazione efficiente** più avanti in questo argomento.  
  
### <a name="to-create-a-context-bag-for-an-editor-or-a-designer"></a>Per creare un contenitore di contesto per un editor o una finestra di progettazione  
  
1.  Chiamare `QueryService` sul <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interfaccia di amministrazione del <xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext> servizio.  
  
     Un puntatore al <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext> interfaccia viene restituita.  
  
2.  Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext.CreateEmptyContext%2A> metodo per creare un nuovo contenitore di contesto o sottocontesto.  
  
     Un puntatore al <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> interfaccia viene restituita.  
  
3.  Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> metodo per aggiungere gli attributi, le parole chiave di ricerca o le parole chiave F1 per il contenitore di contesto o sottocontesto.  
  
4.  Se si sta creando un elenco di sottocontesti, chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddSubcontext%2A> metodo per collegare l'elenco di sottocontesti a di contesti padre.  
  
5.  Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> per ricevere una notifica quando il **Guida dinamica** finestra sta per aggiornare.  
  
     Con il **Guida dinamica** finestra chiamare l'editor quando è pronto per l'aggiornamento ti offre la possibilità di ritardare la modifica del contesto fino a quando non si verifica l'aggiornamento. Questa operazione può migliorare le prestazioni poiché consente di ritardare l'esecuzione di algoritmi che richiedono molto tempo fino a quando non è disponibile tempo di inattività del sistema.  
  
### <a name="to-publish-the-context-bag-to-the-seid"></a>Per pubblicare l'elenco di contesti di SEID  
  
1.  Chiamare `QueryService` nella <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> servizio di restituire un puntatore al <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> interfaccia.  
  
2.  Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>, specificando un identificatore di elemento (`elementid` parametro) valore di SEID_UserContext per indicare che si sta passando contesto a livello globale.  
  
3.  Quando l'editor o finestra di progettazione diventa attivo, i valori nel relativo <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> oggetto vengono propagate alla selezione globale. È sufficiente completare il processo una volta per sessione e quindi archiviare il puntatore al contesto globale creato durante la chiamata <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>.  
  
### <a name="to-maintain-the-context-bag"></a>Per mantenere il contenitore di contesto  
  
1.  Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> per assicurarsi che il **Guida dinamica** chiamate nella finestra di editor o finestra di progettazione prima viene aggiornata.  
  
     Per ogni contenitore di contesto che ha chiamato <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> dopo che il contenitore di contesto viene creato e ha implementato <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>, le chiamate IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> per notificare il provider di contesto che il contenitore di contesto verrà aggiornato. È possibile usare questa chiamata per modificare gli attributi e parole chiave nel contenitore di contesto e in qualsiasi elenchi di sottocontesti, prima che il **Guida dinamica** finestra aggiornamento viene eseguito.  
  
2.  Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A> nel contenitore di contesto per indicare che l'editor o finestra di progettazione ha nuovo contesto.  
  
     Quando la **Guida dinamica** chiamate finestra <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> per indicare che l'aggiornamento, l'editor o finestra di progettazione può aggiornare il contesto in modo appropriato per il contenitore di contesti padre e qualsiasi elenchi di sottocontesti in quel momento.  
  
    > [!NOTE]
    >  Il `SetDirty` flag è impostato automaticamente su `true` ogni volta che contesto viene aggiunto o rimosso dall'elenco di contesti. Il **Guida dinamica** solo chiamate nella finestra <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> nel contenitore del contesto se il `SetDirty` flag è impostato su `true`. Viene reimpostato su `false` dopo l'aggiornamento.  
  
3.  Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> per aggiungere contesto alla raccolta di contesto attivo o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A> rimuovere contesto.  
  
## <a name="robust-programming"></a>Programmazione efficiente  
 Se si sta scrivendo un editor personalizzato, è necessario completare tutti e tre le procedure descritte in questo argomento per fornire il contesto per l'editor.  
  
> [!NOTE]
>  Per attivare correttamente una finestra dell'editor o finestra di progettazione e per garantire che il routing di comandi è stato aggiornato correttamente, è necessario chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> sul componente per renderlo la finestra di stato attivo.  
  
 Il SEID è una raccolta di proprietà che cambiano in base alla selezione. SEID informazioni sono disponibili tramite la selezione globale. La selezione globale è stata evidenziata in eventi attivati dal <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> interfaccia, e ha un elenco di tutti gli elementi che è selezionato (editor corrente, finestra degli strumenti corrente, gerarchia corrente e così via).  
  
 Per gli editor e finestre di progettazione, nel cui contesto può cambiare ogni volta che il cursore si sposta all'interno di una parola, non è efficiente per aggiornare continuamente il contenitore di contesto. Per rendere l'aggiornamento di ogni volta che viene rilevato il cursore di spostamento all'interno dell'editor o finestra di progettazione più efficiente, è possibile chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>. Questa operazione consente di mantenere il contesto viene modificato fino a quando non vi è tempo di inattività e il servizio di contesto dell'IDE invia notifica per l'editor o finestra di progettazione che il **Guida dinamica** finestra sta aggiornando. Questo approccio viene usato nella procedura "per mantenere il contenitore di contesto" in questo argomento.  
  
 Dopo aver fornito contesto per le attività all'interno dell'editor o finestra di progettazione, è necessario fornire una parola chiave F1 specifica per consentire agli utenti di visualizzare la Guida per l'editor o finestra di progettazione se stesso.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>
