---
title: Controllo Glyph (VSPackage di controllo codice sorgente) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- glyphs, source control packages
- source control packages, glyphs
ms.assetid: b9413b08-b3c3-4fc3-a6e0-3dc0db3652d7
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ad922a083e11007bb20ab83006a04726a38a034e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49267605"
---
# <a name="glyph-control-source-control-vspackage"></a>Controllo Glyph (VSPackage di controllo del codice sorgente)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Parte della stretta integrazione disponibile per pacchetti VSPackage di controllo del codice sorgente è la possibilità di visualizzare le proprie icone per indicare lo stato degli elementi nel controllo del codice sorgente.  
  
## <a name="levels-of-glyph-control"></a>Livelli di controllo Glyph  
 Un glifo con stato è presente un'icona che indica lo stato corrente dell'elemento quando è visualizzato, ad esempio nella **Esplora soluzioni** o nella **Visualizzazione classi**. Un controllo del codice sorgente VSPackage può applicare due livelli di controllo del glifo. È possibile limitare la scelta di glifi a un set predefinito di glifi fornito dal [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE, o è possibile definire un set personalizzato di glifi da visualizzare.  
  
### <a name="default-set-of-glyphs"></a>Set predefinito di glifi  
 Per determinare i glifi dello stato associati a un elemento in **Esplora soluzioni**, un progetto richiede l'icona di stato dal controllo di origine usando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A>. Un controllo origine pacchetto VSPackage può decidere di mantenere la scelta di glifi limitato per i glifi predefiniti forniti dall'IDE. In questo caso, il pacchetto VSPackage passati nuovamente una matrice di valori che rappresentano le enumerazioni del glifo che vengano definite in vsshell. idl. Per altre informazioni, vedere <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon> . Si tratta di un set predefinito di glifi impostato dall'IDE, ad esempio un lucchetto per il glifo "Selezionata In" e un segno di spunta come il glifo "Estratto".  
  
### <a name="custom-set-of-glyphs"></a>Insieme di glifi personalizzati  
 Un pacchetto VSPackage di controllo di origine è possibile usare i proprio glifi per un "un aspetto univoco" quando viene installato. Quando un nuovo controllo del codice sorgente VSPackage è attivo, deve essere in grado di iniziare a usare i proprio glifi anche se VSPackage controllo del codice sorgente precedente ancora viene caricato ma inattiva. In questa modalità, il controllo del codice sorgente VSPackage ancora possibile usare le icone esistente per mantenere un aspetto coerente con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] se sceglie.  
  
 Il <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> il servizio supporta un'interfaccia, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>, che il pacchetto VSPackage può implementare facoltativamente e che verrà richiesto dall'IDE. Quando l'IDE effettua una richiesta, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] proverà a sua volta a ottenere questa interfaccia dal pacchetto VSPackage di controllo del codice sorgente attualmente registrata. Se l'interfaccia esiste nel pacchetto VSPackage registrato, la richiesta dell'IDE per i glifi personalizzati ha esito positivo; in caso contrario, il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE Usa il set predefinito di glifi.  
  
 Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A> metodo viene utilizzato da [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] per ottenere un elenco di immagini che illustrano il controllo del codice sorgente diversi gli stati. Il controllo del codice sorgente VSPackage restituisce all'IDE di un handle all'elenco di immagini per le icone personalizzate. L'IDE crea una copia dell'elenco immagini a questo punto e viene utilizzato in un secondo momento per scegliere le icone da visualizzare. Se non è supportata la nuova interfaccia o la `IVsSccGlyphs::GetCustomGlyphList` metodo restituisce E_NOTIMPL, quindi l'IDE ottenute relativo glifi nell'elenco predefinito di glifi forniti da [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>

