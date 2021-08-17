---
title: Controllo glifi (VSPackage del controllo del codice sorgente) | Microsoft Docs
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
ms.openlocfilehash: 840ea85abfa995d9fc8df9e417ab13e78b25423e29d12684b3628760b5a61228
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121337968"
---
# <a name="glyph-control-source-control-vspackage"></a>Controllo glifo (VSPackage del controllo del codice sorgente)
Parte della completa integrazione disponibile per i pacchetti VSPackage del controllo del codice sorgente è la possibilità di visualizzare i propri glifi per indicare lo stato degli elementi nel controllo del codice sorgente.

## <a name="levels-of-glyph-control"></a>Livelli di controllo degli glifi
 Un glifo di stato è un'icona che indica lo stato corrente di un elemento quando viene visualizzato, ad esempio **in** Esplora soluzioni o in **Visualizzazione classi**. Un controllo del codice sorgente VSPackage può esercitare due livelli di controllo degli glifi. Può limitare la scelta dei glifi a un set predefinito di glifi forniti dall'IDE oppure può definire un set personalizzato di glifi da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] visualizzare.

### <a name="default-set-of-glyphs"></a>Set predefinito di glifi
 Per determinare i glifi di stato associati a un elemento in **Esplora soluzioni**, un progetto richiede il glifo di stato dal controllo del codice sorgente usando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A> . Un VSPackage del controllo del codice sorgente può decidere di mantenere la scelta dei glifi limitata ai glifi predefiniti forniti dall'IDE. In questo caso, il pacchetto VSPackage passa una matrice di valori che rappresentano le enumerazioni degli glifi definiti in *vsshell.idl.* Per altre informazioni, vedere <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>. Si tratta di un set predefinito di glifi impostati dall'IDE, ad esempio un lucchetto per il glifo archiviato e un segno di spunta per il glifo estratto.

### <a name="custom-set-of-glyphs"></a>Set personalizzato di glifi
 Un VSPackage del controllo del codice sorgente può usare i propri glifi per un aspetto univoco quando viene installato. Quando un nuovo vspackage del controllo del codice sorgente è attivo, dovrebbe essere in grado di iniziare a usare i propri glifi anche se un vsPackage del controllo del codice sorgente precedente è ancora caricato ma inattivo. In questa modalità, il controllo del codice sorgente VSPackage può comunque usare le icone esistenti per mantenere un aspetto coerente con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se lo sceglie.

 Il servizio supporta un'interfaccia , che il pacchetto VSPackage può implementare facoltativamente e che verrà richiesta <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs> dall'IDE. Quando l'IDE effettua una richiesta, tenterà a sua volta di ottenere questa interfaccia dal pacchetto VSPackage del controllo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] del codice sorgente attualmente registrato. Se l'interfaccia esiste nel VSPackage registrato, la richiesta dell'IDE per i glifi personalizzati ha esito positivo; In caso contrario, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l'IDE usa il set predefinito di glifi.

 Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A> metodo viene usato da per ottenere un elenco di immagini che mostrano vari stati del controllo del codice [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sorgente. Il controllo del codice sorgente VSPackage restituisce all'IDE un handle per l'elenco di immagini per i relativi glifi personalizzati. L'IDE crea una copia dell'elenco di immagini a questo punto e la usa in un secondo momento per scegliere i glifi da visualizzare. Se la nuova interfaccia non è supportata o il metodo restituisce , l'IDE ottiene i relativi glifi dall'elenco predefinito di glifi `IVsSccGlyphs::GetCustomGlyphList` `E_NOTIMPL` forniti da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>
- <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>
