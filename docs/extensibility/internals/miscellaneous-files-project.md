---
title: Progetto di file vari Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 95cc1312fb7b381e1e20df834698480295fadcc8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707091"
---
# <a name="miscellaneous-files-project"></a>Progetto di file esterni
Quando un utente apre gli elementi di progetto, l'IDE assegna al file esterni progetto tutti gli elementi che non sono membri di alcun progetto in una soluzione.

 I progetti svolgono un ruolo significativo nel determinare quale editor viene utilizzato quando un utente apre un elemento di progetto. Un progetto può essere progettato per aprire determinati file utilizzando un editor specifico del progetto o un editor standard.

 Un editor specifico del progetto richiede in genere che l'utente disponga di conoscenze speciali o utilizzi interfacce speciali del progetto. Per ulteriori informazioni, vedere [Procedura: aprire editor specifici](../../extensibility/how-to-open-project-specific-editors.md)del progetto .

 Un editor standard può aprire qualsiasi file di un'estensione specifica in qualsiasi progetto. L'utente può personalizzare alcuni editor [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] standard, ad esempio l'editor di testo, per i progetti, mantenendo comunque il carattere pubblico. Gli editor standard vengono <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> creati utilizzando il metodo .

 Se nessun progetto nella soluzione risponde che è possibile aprire un elemento di progetto, l'IDE fornisce un progetto speciale denominato il progetto File esterni che apre qualsiasi file.

 Questo progetto speciale prevede l'apertura di un file al di fuori del contesto di un progetto. Durante l'elaborazione <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> del metodo, il progetto File vari risponde sempre con una priorità molto bassa. Di conseguenza, il progetto File esterni cede sempre a qualsiasi progetto con priorità più alta in grado di aprire i file.

 Il progetto File esterni non richiede all'utente di crearlo in modo esplicito con la finestra di dialogo **Nuovo progetto.** Inoltre, il progetto File esterni non gestisce in modo permanente un elenco di membri del progetto. Utilizza una funzionalità facoltativa per registrare un elenco dei file utilizzati più di recente per ogni utente.

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>
- <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>
- [Procedura: Aprire gli editor specifici del progetto](../../extensibility/how-to-open-project-specific-editors.md)
- [Procedura: Aprire gli editor standard](../../extensibility/how-to-open-standard-editors.md)
- [Aggiunta di modelli di progetto e di elementi di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Aggiunta di modelli di progetto e di elementi di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md)
