---
title: 'Procedura: fornire il contesto per gli editor | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - provide context
ms.assetid: 12df4d06-df6b-4eaf-a7bf-c83655a0c683
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 11a98599a9812cd00650d113170ff55c01ac44db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839612"
---
# <a name="how-to-provide-context-for-editors"></a>Procedura: Fornire il contesto per gli editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per un editor, il contesto è attivo solo quando l'editor ha lo stato attivo o ha avuto lo stato attivo immediatamente prima che lo stato attivo venisse spostato in una finestra degli strumenti. È possibile fornire il contesto per un editor eseguendo le operazioni seguenti:  
  
1. Creare un contenitore di contesti.  
  
2. Pubblicare il contenitore del contesto nell'identificatore dell'elemento Selection (SEID).  
  
3. Mantenere il contesto nel contenitore.  
  
   Queste attività sono descritte nelle procedure riportate di seguito. Per ulteriori informazioni su come fornire il contesto, vedere **programmazione affidabile** più avanti in questo argomento.  
  
### <a name="to-create-a-context-bag-for-an-editor-or-a-designer"></a>Per creare un contenitore di contesti per un editor o una finestra di progettazione  
  
1. Chiamare `QueryService` sull' <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interfaccia per il <xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext> servizio.  
  
     Viene restituito un puntatore all' <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext> interfaccia.  
  
2. Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext.CreateEmptyContext%2A> metodo per creare un nuovo contenitore di contesto o sottocontesto.  
  
     Viene restituito un puntatore all' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> interfaccia.  
  
3. Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> metodo per aggiungere attributi, parole chiave di ricerca o parole chiave F1 al contenitore di contesto o sottocontesto.  
  
4. Se si crea un contenitore di sottocontesto, chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddSubcontext%2A> metodo per collegare il contenitore del sottocontesto all'elenco di contesti padre.  
  
5. Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> per ricevere una notifica quando la finestra della **Guida dinamica** sta per essere aggiornata.  
  
     Se la finestra **Guida dinamica** chiama l'editor quando è pronto per l'aggiornamento, offre la possibilità di ritardare la modifica del contesto fino a quando non si verifica l'aggiornamento. Questa operazione può migliorare le prestazioni perché consente di ritardare l'esecuzione di algoritmi che richiedono molto tempo fino a quando non è disponibile il tempo di inattività del sistema.  
  
### <a name="to-publish-the-context-bag-to-the-seid"></a>Per pubblicare il contenitore di contesti in SEID  
  
1. Chiamare `QueryService` sul <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> servizio per restituire un puntatore all' <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> interfaccia.  
  
2. Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A> , specificando un `elementid` valore di identificatore di elemento (parametro) di SEID_UserContext per indicare che si passa il contesto al livello globale.  
  
3. Quando l'editor o la finestra di progettazione diventa attiva, i valori nell' <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> oggetto vengono propagati alla selezione globale. È sufficiente completare questo processo una volta per sessione e quindi archiviare il puntatore al contesto globale creato quando è stato chiamato <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A> .  
  
### <a name="to-maintain-the-context-bag"></a>Per gestire l'elenco dei contesti  
  
1. Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> per assicurarsi che la finestra **Guida dinamica** chiami l'editor o la finestra di progettazione prima di aggiornarla.  
  
     Per ogni contenitore di contesti che ha chiamato <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> dopo che l'elenco di contesti è stato creato ed è stato implementato <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate> , l'IDE chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> per notificare al provider di contesto che verrà aggiornato l'elenco dei contesti. È possibile utilizzare questa chiamata per modificare gli attributi e le parole chiave nell'elenco dei contesti e in tutti i sacchetti di sottocontesto prima che venga eseguito l'aggiornamento della finestra della **Guida dinamica** .  
  
2. Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A> sul contenitore di contesti per indicare che l'editor o la finestra di progettazione ha un nuovo contesto.  
  
     Quando la finestra **Guida dinamica** chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> per indicare che è in fase di aggiornamento, l'editor o la finestra di progettazione può aggiornare il contesto in modo appropriato sia per l'elenco di contesti padre che per tutti i contenitori di sottocontesto in quel momento.  
  
    > [!NOTE]
    > Il `SetDirty` flag viene impostato automaticamente su `true` ogni volta che il contesto viene aggiunto o rimosso dall'elenco dei contesti. La finestra **Guida dinamica** chiama solo <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> sul contenitore di contesti se il `SetDirty` flag è impostato su `true` . Viene reimpostato su `false` dopo l'aggiornamento.  
  
3. Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> per aggiungere il contesto alla raccolta di contesto attiva o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A> per rimuovere il contesto.  
  
## <a name="robust-programming"></a>Programmazione efficiente  
 Se si scrive un editor personalizzato, è necessario completare tutte e tre le procedure descritte in questo argomento per fornire il contesto per l'editor.  
  
> [!NOTE]
> Per attivare correttamente un editor o una finestra di progettazione e per assicurarsi che il routing dei comandi venga aggiornato correttamente, è necessario chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> sul componente per impostarlo come finestra di attivazione.  
  
 SEID è una raccolta di proprietà che cambiano in base alla selezione. Le informazioni SEID sono disponibili tramite la selezione globale. La selezione globale è collegata a eventi generati dall' <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> interfaccia e contiene un elenco di tutti gli elementi selezionati (editor corrente, finestra degli strumenti corrente, gerarchia corrente e così via).  
  
 Per gli editor e le finestre di progettazione, in cui il contesto può cambiare ogni volta che il cursore si sposta all'interno di una parola, non è efficiente aggiornare costantemente l'elenco dei contesti. Per rendere più efficiente l'aggiornamento ogni volta che si rileva il cursore che si muove all'interno dell'editor o della finestra di progettazione, è possibile chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A> . Questa operazione consente di mantenere le modifiche del contesto fino al tempo di inattività e il servizio del contesto dell'IDE invia una notifica all'editor o alla finestra di progettazione che la finestra **Guida dinamica** sta aggiornando. Questo approccio viene usato nella procedura "per gestire il contenitore dei contesti" in questo argomento.  
  
 Dopo aver fornito il contesto per le attività all'interno dell'editor o della finestra di progettazione, è necessario fornire una specifica parola chiave F1 per consentire agli utenti di ottenere la guida per l'editor o la finestra di progettazione.  
  
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
