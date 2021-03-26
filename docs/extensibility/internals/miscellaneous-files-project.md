---
title: Progetto di file esterni | Microsoft Docs
description: Informazioni sui due tipi di editor che è possibile usare per aprire i file in un progetto di Visual Studio e il ruolo del progetto per determinare quale editor usare.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b79eaaeaf94954e2d3dc1bd855b56bee5b8bdae4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063279"
---
# <a name="miscellaneous-files-project"></a>Progetto di file esterni
Quando un utente apre gli elementi del progetto, l'IDE assegna al progetto di file esterni tutti gli elementi che non sono membri di alcun progetto in una soluzione.

 I progetti svolgono un ruolo significativo nella determinazione dell'editor da utilizzare quando un utente apre un elemento del progetto. Un progetto può essere progettato per aprire determinati file utilizzando un editor standard o un editor specifico del progetto.

 Un editor specifico del progetto richiede in genere che l'utente disponga di una conoscenza speciale o utilizzi interfacce speciali dal progetto. Per altre informazioni, vedere [procedura: aprire Project-Specific editor](../../extensibility/how-to-open-project-specific-editors.md).

 Un editor standard può aprire qualsiasi file di un'estensione specifica in qualsiasi progetto. L'utente può personalizzare alcuni editor standard, ad esempio l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] editor di testo, per i progetti, mantenendo comunque il carattere pubblico. Gli editor standard vengono creati tramite il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodo.

 Se nessun progetto nella soluzione risponde che è in grado di aprire un elemento del progetto, l'IDE fornisce un progetto speciale denominato progetto di file esterni che apre un file.

 Questo progetto speciale fornisce l'apertura di un file al di fuori del contesto di un progetto. Durante l'elaborazione del <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> metodo, il progetto di file esterni risponde sempre con una priorità molto bassa. Il progetto di file esterni restituisce pertanto sempre un progetto con priorità più alta in grado di aprire i file.

 Per il progetto di file esterni non è necessario che l'utente lo crei in modo esplicito con la finestra di dialogo **nuovo progetto** . Inoltre, il progetto di file esterni non gestisce in modo permanente un elenco di membri del progetto. Usa una funzionalità facoltativa per registrare un elenco dei file usati di recente per ogni utente.

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>
- <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>
- [Procedura: Aprire gli editor specifici del progetto](../../extensibility/how-to-open-project-specific-editors.md)
- [Procedura: Aprire gli editor standard](../../extensibility/how-to-open-standard-editors.md)
- [Aggiunta di modelli di progetto e di elementi di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Aggiunta di modelli di progetto e di elementi di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md)
