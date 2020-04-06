---
title: 'Procedura: Aprire gli editor per i documenti aperti . Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], opening for open documents
ms.assetid: 1a0fa49c-efa4-4dcc-bdc0-299b7052acdc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03d0986573ac0d53427f6490370be2bfa1c4cbe7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710920"
---
# <a name="how-to-open-editors-for-open-documents"></a>Procedura: aprire gli editor per i documenti apertiHow to: Open editors for open documents
Prima che un progetto apra una finestra del documento, il progetto deve prima determinare se il file è già aperto nella finestra del documento per un altro editor. Il file può essere aperto in un editor specifico del progetto [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]o in uno degli editor standard registrati con .

## <a name="open-a-project-specific-editor"></a>Aprire un editor specifico del progettoOpen a project-specific editor
 Utilizzare la procedura seguente per aprire un editor specifico del progetto per un file già aperto.

### <a name="to-open-a-project-specific-editor-for-an-open-file"></a>Per aprire un editor specifico del progetto per un file apertoTo open a project-specific editor for an open file

1. Chiamare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> .

    Questa chiamata restituisce i puntatori alla gerarchia del documento, all'elemento della gerarchia e alla cornice della finestra, se appropriato.

2. Se il documento è aperto, il progetto deve verificare se esiste solo un oggetto dati del documento o se è presente anche un oggetto visualizzazione documento.

   - Se esiste un oggetto visualizzazione documento e questa visualizzazione è per una gerarchia diversa o un elemento della gerarchia, il progetto utilizza il puntatore alla cornice della finestra della visualizzazione per riaffiorare la finestra esistente.

   - Se esiste un oggetto visualizzazione documento e questa visualizzazione è per la stessa gerarchia e l'elemento della gerarchia, il progetto può aprire una seconda visualizzazione se è possibile collegare all'oggetto dati del documento sottostante. In caso contrario, il progetto deve utilizzare il puntatore alla cornice della finestra della visualizzazione per riaffiorare la finestra esistente.

   - Se esiste solo l'oggetto dati del documento, il progetto deve determinare se è possibile utilizzare l'oggetto dati del documento per la visualizzazione. Se l'oggetto dati del documento è compatibile, completare i passaggi descritti in Aprire un editor specifico del [progetto.](../extensibility/how-to-open-project-specific-editors.md)

     Se l'oggetto dati del documento non è compatibile, deve essere visualizzato un errore per l'utente che indica che il file è attualmente in uso. Questo errore deve essere visualizzato solo in casi temporanei, ad esempio quando un file viene compilato contemporaneamente l'utente [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sta tentando di aprire il file utilizzando un editor diverso dall'editor di testo principale. L'editor di testo principale può condividere l'oggetto dati del documento con il compilatore.

3. Se il documento non è aperto perché non è presente alcun oggetto dati del documento o oggetto visualizzazione documento, completare i passaggi descritti in Aprire un editor specifico del [progetto.](../extensibility/how-to-open-project-specific-editors.md)

## <a name="open-a-standard-editor"></a>Aprire un editor standard
 Utilizzare la procedura seguente per aprire un editor standard per un file già aperto.

### <a name="to-open-a-standard-editor-for-an-open-file"></a>Per aprire un editor standard per un file aperto

1. Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>.

     Questo metodo verifica innanzitutto che il documento <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>non sia già aperto chiamando . Se il documento è già aperto, la finestra dell'editor viene nuovamente visualizzata.

2. Se il documento non è aperto, completare i passaggi descritti in [Procedura: aprire gli editor standard.](../extensibility/how-to-open-standard-editors.md)

## <a name="see-also"></a>Vedere anche
- [Aprire e salvare elementi di progetto](../extensibility/internals/opening-and-saving-project-items.md)
- [Procedura: aprire editor specifici del progettoHow to: Open project-specific editors](../extensibility/how-to-open-project-specific-editors.md)
- [Procedura: aprire gli editor standardHow to: Open standard editors](../extensibility/how-to-open-standard-editors.md)
