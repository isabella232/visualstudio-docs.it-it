---
title: 'Procedura: Aprire editor per documenti aperti | Microsoft Docs'
description: Informazioni su come aprire un file in un editor standard o specifico del progetto. Quando un progetto apre una finestra del documento, deve determinare se il file è già aperto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], opening for open documents
ms.assetid: 1a0fa49c-efa4-4dcc-bdc0-299b7052acdc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: aa669bae8cd178f70ff843c309fdbdaf9ed1bed9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122124945"
---
# <a name="how-to-open-editors-for-open-documents"></a>Procedura: Aprire editor per documenti aperti
Prima che un progetto apra una finestra del documento, il progetto deve prima determinare se il file è già aperto nella finestra del documento per un altro editor. Il file può essere aperto in un editor specifico del progetto o in uno degli editor standard registrati con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="open-a-project-specific-editor"></a>Aprire un editor specifico del progetto
 Usare la procedura seguente per aprire un editor specifico del progetto per un file già aperto.

### <a name="to-open-a-project-specific-editor-for-an-open-file"></a>Per aprire un editor specifico del progetto per un file aperto

1. Chiamare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> .

    Questa chiamata restituisce puntatori alla gerarchia, all'elemento della gerarchia e alla cornice della finestra del documento, se appropriato.

2. Se il documento è aperto, il progetto deve verificare se esiste solo un oggetto dati del documento o se è presente anche un oggetto visualizzazione documento.

   - Se esiste un oggetto visualizzazione documento e questa visualizzazione è per un elemento di gerarchia o gerarchia diverso, il progetto usa il puntatore alla cornice della finestra della visualizzazione per riaccesare la finestra esistente.

   - Se esiste un oggetto visualizzazione documento e questa visualizzazione è per lo stesso elemento gerarchia e gerarchia, il progetto può aprire una seconda visualizzazione se può connettersi all'oggetto dati del documento sottostante. In caso contrario, il progetto deve usare il puntatore alla cornice della finestra della visualizzazione per riaserire la finestra esistente.

   - Se esiste solo l'oggetto dati del documento, il progetto deve determinare se può usare l'oggetto dati del documento per la relativa visualizzazione. Se l'oggetto dati del documento è compatibile, completare i passaggi descritti in [Aprire un editor specifico del progetto](../extensibility/how-to-open-project-specific-editors.md).

     Se l'oggetto dati del documento non è compatibile, verrà visualizzato un errore che indica che il file è attualmente in uso. Questo errore deve essere visualizzato solo in casi temporanei, ad esempio quando un file viene compilato nello stesso momento in cui l'utente tenta di aprire il file usando un editor diverso dall'editor di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] testo principale. L'editor di testo principale può condividere l'oggetto dati del documento con il compilatore.

3. Se il documento non è aperto perché non è presente alcun oggetto dati del documento o oggetto visualizzazione documento, completare i passaggi descritti in [Aprire un editor specifico del progetto](../extensibility/how-to-open-project-specific-editors.md).

## <a name="open-a-standard-editor"></a>Aprire un editor standard
 Usare la procedura seguente per aprire un editor standard per un file già aperto.

### <a name="to-open-a-standard-editor-for-an-open-file"></a>Per aprire un editor standard per un file aperto

1. Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>.

     Questo metodo verifica innanzitutto che il documento non sia già aperto chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> . Se il documento è già aperto, viene riaperta la relativa finestra dell'editor.

2. Se il documento non è aperto, completare la procedura descritta in [Procedura: Aprire gli editor standard](../extensibility/how-to-open-standard-editors.md).

## <a name="see-also"></a>Vedi anche
- [Aprire e salvare elementi di progetto](../extensibility/internals/opening-and-saving-project-items.md)
- [Procedura: Aprire editor specifici del progetto](../extensibility/how-to-open-project-specific-editors.md)
- [Procedura: Aprire editor standard](../extensibility/how-to-open-standard-editors.md)
