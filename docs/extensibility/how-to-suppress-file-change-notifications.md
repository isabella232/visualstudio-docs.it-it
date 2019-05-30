---
title: 'Procedura: Non visualizzare notifiche di cambiamento File | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - suppress file change notification
ms.assetid: 891c1eb4-f6d0-4073-8df0-2859dbd417ca
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d7acfb4a5a680aa4be6e93187560cd66b68fa3b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324918"
---
# <a name="how-to-suppress-file-change-notifications"></a>Procedura: Eliminare le notifiche di modifica di file
Quando è stato modificato il file fisico che rappresenta il buffer di testo, consente di visualizzare una finestra di dialogo con il messaggio **si desidera salvare le modifiche apportate ai seguenti elementi?** Questo è noto come notifica di modifica di file. Se sono condividono molte modifiche al file, tuttavia, questa finestra di dialogo ripetutamente la visualizzazione può diventare rapidamente fastidiosa.

 A livello di codice, è possibile eliminare questa finestra di dialogo mediante la procedura seguente. Eliminando la finestra di dialogo, è possibile ricaricare un file immediatamente senza dover richiedere all'utente di salvare le modifiche ogni volta.

## <a name="to-suppress-file-change-notification"></a>Per eliminare la notifica delle modifiche file

1. Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> metodo per determinare quale oggetto buffer di testo è associato il file aperto.

2. Diretto il <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> oggetto monitorato in memoria per ignorare le modifiche ai file ottenendo il <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> dell'interfaccia dal <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> oggetto (dati del documento) e quindi implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> metodo con il `fIgnore` parametro Impostare su `true`.

3. Chiamano i metodi per la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> e il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interfacce per aggiornare la memoria in <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> oggetto con le modifiche ai file (ad esempio, quando si aggiunge un campo al componente).

4. Aggiornare il file su disco con le modifiche senza considerare eventuali modifiche, che l'utente potrebbe essere in corso in sospeso.

     In questo modo, quando si indirizzano le <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> notifiche delle modifiche dell'oggetto per riprendere il monitoraggio per il file, il buffer di testo in memoria riflette le modifiche che è stato generato. Il buffer di testo in memoria riflette anche tutte le altre modifiche in sospeso. Il file su disco rifletta il codice più recente generato dall'utente e qualsiasi precedentemente salvato le modifiche apportate dall'utente nel codice utente ha modificato.

5. Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> metodo per notificare il <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> oggetto per riprendere il monitoraggio per le notifiche di modifica di file, impostando il `fIgnore` parametro per `false`.

6. Se si prevede di apportare diverse modifiche al file, come nel caso del controllo del codice sorgente (SCC), è necessario indicare al servizio di modifica globale file di sospendere temporaneamente le notifiche di modifica di file.

     Ad esempio, se si riscrive il file e quindi modifica il timestamp, è necessario sospendere le notifiche di cambiamento file perché le operazioni riscrittura e timestamp contano come un evento di modifica di file separato. Per abilitare la notifica della modifica file globale, è necessario chiamare invece il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx.IgnoreFile%2A> (metodo).

## <a name="example"></a>Esempio
 Il codice seguente viene illustrato come eliminare una notifica di cambiamento file.

```cpp
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
 Se il caso riguarda più modifiche al file, come nel caso del controllo del codice sorgente, quindi è importante riprendere le notifiche di modifica file globale prima di inviare i dati del documento per riprendere il monitoraggio delle modifiche ai file di avviso.