---
title: 'Procedura: non visualizzare le notifiche di modifica del file | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - suppress file change notification
ms.assetid: 891c1eb4-f6d0-4073-8df0-2859dbd417ca
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3f045175eae165b75a887ada2716b19f34fc228b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204085"
---
# <a name="how-to-suppress-file-change-notifications"></a>Procedura: Eliminare le notifiche di modifica file
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando il file fisico che rappresenta il buffer di testo è stato modificato, viene visualizzata una finestra di dialogo con il messaggio in cui **si desidera salvare le modifiche apportate agli elementi seguenti?** Questa operazione è nota come notifica di modifica del file. Se molte modifiche verranno apportate al file, tuttavia, questa finestra di dialogo visualizzata più volte può diventare fastidioso.  
  
 Questa finestra di dialogo può essere disattivata a livello di codice utilizzando la procedura riportata di seguito. In questo modo, è possibile ricaricare un file immediatamente senza dover richiedere all'utente di salvare ogni volta le modifiche.  
  
### <a name="to-suppress-file-change-notification"></a>Per disattivare la notifica di modifica del file  
  
1. Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> metodo per determinare quale oggetto del buffer di testo è associato al file aperto.  
  
2. Indirizzare l' <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> oggetto in memoria per ignorare le modifiche del file di monitoraggio ottenendo l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> interfaccia dall' <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> oggetto (dati del documento), quindi implementando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> metodo con il `fIgnore` parametro impostato su `true` .  
  
3. Chiamare i metodi su <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> e le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interfacce per aggiornare l'oggetto in memoria <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> con le modifiche al file, ad esempio quando un campo viene aggiunto al componente.  
  
4. Aggiornare il file su disco con le modifiche senza considerare le eventuali modifiche in sospeso che l'utente potrebbe avere in corso.  
  
     In questo modo, quando si indirizza l' <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> oggetto per riprendere il monitoraggio per le notifiche di modifica dei file, il buffer di testo in memoria riflette le modifiche generate e tutte le altre modifiche in sospeso. Il file su disco riflette il codice più recente generato dall'utente e tutte le modifiche precedentemente salvate dall'utente nel codice modificato dall'utente.  
  
5. Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> metodo per notificare all' <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> oggetto di riprendere il monitoraggio per le notifiche di modifica dei file impostando il `fIgnore` parametro su `false` .  
  
6. Se si prevede di apportare diverse modifiche al file, come nel caso del controllo del codice sorgente (SCC), è necessario indicare al servizio Global file Change di sospendere temporaneamente le notifiche di modifica dei file.  
  
     Ad esempio, se si riscrive il file e quindi si modifica il timestamp, è necessario sospendere le notifiche di modifica del file, in quanto le operazioni di riscrittura e di timestample ogni conteggio come un evento di modifica del file separato. Per abilitare la notifica di modifica del file globale, è necessario chiamare invece il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx.IgnoreFile%2A> metodo.  
  
## <a name="example"></a>Esempio  
 Di seguito viene illustrato come disattivare la notifica di modifica del file.  
  
```cpp#  
//Misc. helper classes  
  
CSuspendFileChanges::CSuspendFileChanges(  
    /* [in] */ const CString& strMkDocument,   
    /* [in] */ BOOL fSuspendNow /* = TRUE */)   
:  
    m_strMkDocument(strMkDocument),  
    m_fFileChangeSuspended(FALSE)  
{  
    if(fSuspendNow)  
        Suspend();  
}  
CSuspendFileChanges::~CSuspendFileChanges()  
{  
    Resume();  
}  
void CSuspendFileChanges::Suspend()  
{  
    USES_CONVERSION;  
  
    // Prevent suspend from suspending more than once.  
    if(m_fFileChangeSuspended)  
        return;  
  
    IVsRunningDocumentTable* pRDT =   
      _VxModule.GetIVsRunningDocumentTable();  
    ASSERT(pRDT);  
    if (!pRDT)  
        return;  
  
    CComPtr<IUnknown> srpDocData;  
    VSCOOKIE vscookie = VSCOOKIE_NIL;  
    pRDT->FindAndLockDocument(RDT_NoLock, T2COLE(m_strMkDocument),    
      NULL, NULL, &srpDocData, &vscookie);  
    if ( (vscookie == VSCOOKIE_NIL) || !srpDocData)  
        return;  
    CComPtr<IVsFileChangeEx> srpIVsFileChangeEx;  
    HRESULT hr = _VxModule.QueryService(SID_SVsFileChangeEx,   
      IID_IVsFileChangeEx, (void **)&srpIVsFileChangeEx);  
    if (SUCCEEDED(hr) && srpIVsFileChangeEx)  
    {  
        m_fFileChangeSuspended = TRUE;  
        srpIVsFileChangeEx->IgnoreFile(NULL, m_strMkDocument, TRUE);   
        srpDocData->QueryInterface(IID_IVsDocDataFileChangeControl,   
          (void**)&m_srpIVsDocDataFileChangeControl);  
        if(m_srpIVsDocDataFileChangeControl)  
            m_srpIVsDocDataFileChangeControl->IgnoreFileChanges(TRUE);  
    }  
}  
void CSuspendFileChanges::Resume()  
{  
    if(!m_fFileChangeSuspended)  
        return;  
  
    CComPtr<IVsFileChangeEx> srpIVsFileChangeEx;  
    HRESULT hr = _VxModule.QueryService(SID_SVsFileChangeEx,   
      IID_IVsFileChangeEx, (void **)&srpIVsFileChangeEx);  
    if (SUCCEEDED(hr) && srpIVsFileChangeEx)  
  
    srpIVsFileChangeEx->IgnoreFile(NULL, m_strMkDocument, FALSE);   
    if(m_srpIVsDocDataFileChangeControl)  
        m_srpIVsDocDataFileChangeControl->IgnoreFileChanges(FALSE);  
    m_fFileChangeSuspended = FALSE;  
    m_srpIVsDocDataFileChangeControl.Release();  
}  
// Misc. helper classes  
```  
  
## <a name="robust-programming"></a>Programmazione efficiente  
 Se il caso riguarda più modifiche al file, come nel caso di SCC, è importante riprendere le notifiche di modifica del file globale prima di inviare un avviso ai dati del documento per riprendere il monitoraggio delle modifiche dei file.
