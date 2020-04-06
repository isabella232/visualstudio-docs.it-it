---
title: Controllo glifo (controllo del codice sorgente VSPackage) Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glyphs, source control packages
- source control packages, glyphs
ms.assetid: b9413b08-b3c3-4fc3-a6e0-3dc0db3652d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9db1b4542eae293e39cda674fac3eb984aa77d3e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708313"
---
# <a name="glyph-control-source-control-vspackage"></a>Controllo glifo (controllo del codice sorgente VSPackage)Glyph control (source control VSPackage)
Parte dell'integrazione completa disponibile per il controllo del codice sorgente VSPackage è la possibilità di visualizzare i propri glifi per indicare lo stato degli elementi nel controllo del codice sorgente.

## <a name="levels-of-glyph-control"></a>Livelli del controllo glifo
 Un glifo di stato è un'icona che indica lo stato corrente di un elemento quando viene visualizzato, ad esempio in **Esplora soluzioni** o in **Visualizzazione classi**. Un controllo del codice sorgente VSPackage può esercitare due livelli di controllo glifo. Può limitare la scelta dei glifi a un set [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] predefinito di glifi forniti dall'IDE oppure può definire un set personalizzato di glifi da visualizzare.

### <a name="default-set-of-glyphs"></a>Set predefinito di glifi
 Per determinare i glifi di stato associati a un elemento in **Esplora soluzioni,** un progetto richiede il glifo dello stato dal controllo del codice sorgente utilizzando l'estensione <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A>. Un controllo del codice sorgente VSPackage può decidere di mantenere la scelta dei glifi limitata ai glifi predefiniti forniti dall'IDE. In questo caso, il pacchetto VSPackage passa nuovamente una matrice di valori che rappresentano le enumerazioni di glifi definiti in *vsshell.idl*. Per altre informazioni, vedere <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>. Si tratta di un set predefinito di glifi impostato dall'IDE, ad esempio un lucchetto per il glifo archiviato e un segno di spunta per il glifo estratto.

### <a name="custom-set-of-glyphs"></a>Set personalizzato di glifi
 Un controllo del codice sorgente VSPackage può utilizzare i propri glifi per un aspetto univoco quando viene installato. Quando un nuovo controllo del codice sorgente VSPackage è attivo, dovrebbe essere in grado di iniziare a utilizzare i propri glifi anche se un controllo del codice sorgente precedente VSPackage è ancora caricato ma inattivo. In questa modalità, il controllo del codice sorgente VSPackage ancora [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] possibile utilizzare le icone esistenti per mantenere un aspetto coerente con se sceglie.

 Il <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> servizio supporta un'interfaccia, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>, che il pacchetto VSPackage può implementare facoltativamente e che verrà richiesto dall'IDE. Quando l'IDE effettua [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] una richiesta, a sua volta tenterà di ottenere questa interfaccia dal controllo del codice sorgente attualmente registrato VSPackage.When the IDE makes a request, will in turn try to get this interface from the currently registered source control VSPackage. Se l'interfaccia esiste nel pacchetto VSPackage registrato, la richiesta dell'IDE per glifi personalizzati ha esito positivo; in caso [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] contrario, l'IDE utilizza il set predefinito di glifi.

 Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A> metodo viene [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilizzato da per ottenere un elenco di immagini che mostrano vari stati del controllo del codice sorgente. Il controllo del codice sorgente VSPackage restituisce all'IDE un handle per l'elenco di immagini per i glifi personalizzati. L'IDE crea una copia dell'elenco di immagini a questo punto e lo usa in un secondo momento per scegliere i glifi da visualizzare. Se la nuova interfaccia non `IVsSccGlyphs::GetCustomGlyphList` è `E_NOTIMPL`supportata o il metodo restituisce , l'IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ottiene i glifi dall'elenco predefinito di glifi fornito da .

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>
- <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>
