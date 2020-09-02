---
title: Controllo Glyph (VSPackage del controllo del codice sorgente) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- glyphs, source control packages
- source control packages, glyphs
ms.assetid: b9413b08-b3c3-4fc3-a6e0-3dc0db3652d7
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b0960209b67c8d2f111296840119807d95bb2e2d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538421"
---
# <a name="glyph-control-source-control-vspackage"></a>Controllo Glyph (VSPackage di controllo del codice sorgente)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Parte dell'integrazione completa disponibile per i pacchetti VSPackage del controllo del codice sorgente è la possibilità di visualizzare i propri glifi per indicare lo stato degli elementi nel controllo del codice sorgente.  
  
## <a name="levels-of-glyph-control"></a>Livelli del controllo Glyph  
 Un glifo di stato è un'icona che indica lo stato corrente di un elemento quando viene visualizzato, ad esempio in **Esplora soluzioni** o in **Visualizzazione classi**. Un VSPackage del controllo del codice sorgente può esercitare due livelli di controllo Glyph. Può limitare la scelta dei glifi a un set predefinito di glifi fornito dall' [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE oppure può definire un set di glifi personalizzato da visualizzare...  
  
### <a name="default-set-of-glyphs"></a>Set di glifi predefinito  
 Per determinare i glifi di stato associati a un elemento in **Esplora soluzioni**, un progetto richiede il glifo di stato dal controllo del codice sorgente usando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A> . Un pacchetto VSPackage del controllo del codice sorgente può decidere di evitare la scelta dei glifi limitati a glifi predefiniti forniti dall'IDE. In questo caso, il pacchetto VSPackage restituisce una matrice di valori che rappresentano le enumerazioni dei glifi definite in vsshell. idl. Per ulteriori informazioni, vedere <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon> . Si tratta di un set predefinito di glifi impostati dall'IDE, ad esempio un lucchetto per il glifo "archiviato" e un segno di spunta come glifo "Estratto".  
  
### <a name="custom-set-of-glyphs"></a>Set personalizzato di glifi  
 Un VSPackage del controllo del codice sorgente può usare i propri glifi per un "aspetto" univoco quando viene installato. Quando un nuovo VSPackage del controllo del codice sorgente è attivo, dovrebbe essere in grado di iniziare a usare i propri glifi anche se un pacchetto VSPackage del controllo del codice sorgente precedente è ancora caricato ma inattivo. In questa modalità, il pacchetto VSPackage del controllo del codice sorgente può ancora usare le icone esistenti per mantenere un aspetto coerente con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] se sceglie.  
  
 Il <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> servizio supporta un'interfaccia, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs> , che il pacchetto VSPackage può implementare facoltativamente e che verrà richiesto dall'IDE. Quando l'IDE esegue una richiesta, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] tenterà a sua volta di ottenere questa interfaccia dal pacchetto VSPackage del controllo del codice sorgente attualmente registrato. Se l'interfaccia esiste nel pacchetto VSPackage registrato, la richiesta dell'IDE per i glifi personalizzati viene completata. in caso contrario, l' [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE utilizzerà il set di glifi predefinito.  
  
 Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A> metodo viene utilizzato da [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] per ottenere un elenco di immagini che mostrano diversi Stati del controllo del codice sorgente. Il pacchetto VSPackage del controllo del codice sorgente restituisce all'IDE un handle per l'elenco di immagini per le icone personalizzate. L'IDE crea una copia dell'elenco di immagini in questa fase e la utilizza in un secondo momento per scegliere i glifi da visualizzare. Se la nuova interfaccia non è supportata o il `IVsSccGlyphs::GetCustomGlyphList` metodo restituisce E_NOTIMPL, l'IDE ottiene i relativi glifi dall'elenco predefinito di glifi forniti da [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>
