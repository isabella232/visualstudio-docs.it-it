---
title: Controllo Glyph (VSPackage del controllo del codice sorgente) | Microsoft Docs
description: Informazioni su come visualizzare glifi personalizzati in un VSPackage del controllo del codice sorgente in modo che sia possibile usare icone personalizzate per indicare lo stato degli elementi nel controllo del codice sorgente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glyphs, source control packages
- source control packages, glyphs
ms.assetid: b9413b08-b3c3-4fc3-a6e0-3dc0db3652d7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 8a692473176843730f8cb9c1acfeb90ed164e4ad
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634571"
---
# <a name="glyph-control-source-control-vspackage"></a>Controllo Glyph (VSPackage del controllo del codice sorgente)
Parte dell'integrazione completa disponibile per i pacchetti VSPackage del controllo del codice sorgente è la possibilità di visualizzare i propri glifi per indicare lo stato degli elementi nel controllo del codice sorgente.

## <a name="levels-of-glyph-control"></a>Livelli di controllo del glifo
 Un glifo di stato è un'icona che indica lo stato corrente di un elemento quando viene visualizzato, ad esempio **in** Esplora soluzioni o in **Visualizzazione classi**. Un VSPackage di controllo del codice sorgente può esercitare due livelli di controllo del glifo. Può limitare la scelta dei glifi a un set predefinito di glifi forniti dall'IDE oppure può definire un set personalizzato di glifi da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] visualizzare.

### <a name="default-set-of-glyphs"></a>Set predefinito di glifi
 Per determinare i glifi di stato associati a un elemento in **Esplora soluzioni**, un progetto richiede il glifo di stato al controllo del codice sorgente usando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A> . Un VSPackage del controllo del codice sorgente può decidere di mantenere la scelta dei glifi limitata ai glifi predefiniti forniti dall'IDE. In questo caso, il pacchetto VSPackage passa di nuovo una matrice di valori che rappresentano le enumerazioni di glifi definite in *vsshell.idl.* Per altre informazioni, vedere <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>. Si tratta di un set predefinito di glifi impostati dall'IDE, ad esempio un lucchetto per il glifo archiviato e un segno di spunta per il glifo estratto.

### <a name="custom-set-of-glyphs"></a>Set personalizzato di glifi
 Un VSPackage del controllo del codice sorgente può usare i propri glifi per un aspetto univoco quando viene installato. Quando un nuovo VSPackage del controllo del codice sorgente è attivo, dovrebbe essere in grado di iniziare a usare i propri glifi anche se un VSPackage del controllo del codice sorgente precedente è ancora caricato ma inattivo. In questa modalità, il pacchetto VSPackage del controllo del codice sorgente può comunque usare le icone esistenti per mantenere un aspetto coerente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] con se lo sceglie.

 Il servizio supporta un'interfaccia, , che il VSPackage può implementare facoltativamente e <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs> che verrà richiesta dall'IDE. Quando l'IDE effettua una richiesta, tenterà a sua volta di ottenere questa interfaccia dal pacchetto VSPackage del controllo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] del codice sorgente attualmente registrato. Se l'interfaccia esiste nel VSPackage registrato, la richiesta dell'IDE per i glifi personalizzati ha esito positivo; In caso contrario, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l'IDE usa il set predefinito di glifi.

 Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A> metodo viene usato da per ottenere un elenco di immagini che mostrano vari stati del controllo del codice [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sorgente. Il pacchetto VSPackage del controllo del codice sorgente restituisce all'IDE un handle per l'elenco di immagini per i glifi personalizzati. L'IDE crea una copia dell'elenco di immagini a questo punto e la usa in un secondo momento per scegliere i glifi da visualizzare. Se la nuova interfaccia non è supportata o il metodo restituisce , l'IDE ottiene i glifi dall'elenco predefinito di glifi fornito `IVsSccGlyphs::GetCustomGlyphList` `E_NOTIMPL` da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>
- <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>
