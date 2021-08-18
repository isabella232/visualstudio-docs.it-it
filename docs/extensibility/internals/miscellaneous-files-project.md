---
title: File esterni Project | Microsoft Docs
description: Informazioni sui due tipi di editor che è possibile usare per aprire i file in un progetto Visual Studio e sul ruolo del progetto per determinare l'editor da usare.
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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 2a3c372e80b9c0843d63c1ed6e674cf9cc5c1bb6d1d68bec4f6fa1e06b4476dc
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121337890"
---
# <a name="miscellaneous-files-project"></a>Progetto di file esterni
Quando un utente apre elementi di progetto, l'IDE assegna al progetto File esterni tutti gli elementi che non sono membri di progetti in una soluzione.

 I progetti svolgono un ruolo significativo nel determinare quale editor viene usato quando un utente apre un elemento di progetto. Un progetto può essere progettato per aprire determinati file usando un editor specifico del progetto o un editor standard.

 Un editor specifico del progetto richiede in genere che l'utente abbia conoscenze speciali o usi interfacce speciali del progetto. Per altre informazioni, [vedere Procedura: Aprire Project-Specific editor .](../../extensibility/how-to-open-project-specific-editors.md)

 Un editor standard può aprire qualsiasi file di un'estensione specifica in qualsiasi progetto. L'utente può personalizzare alcuni editor standard, ad esempio l'editor di testo, per i progetti, mantenendo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] comunque il carattere pubblico. Gli editor standard vengono creati usando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodo .

 Se nessun progetto nella soluzione risponde che può aprire un elemento di progetto, l'IDE fornisce un progetto speciale denominato progetto File esterni che apre qualsiasi file.

 Questo progetto speciale consente l'apertura di un file all'esterno del contesto di un progetto. Durante l'elaborazione del metodo, il progetto File esterni risponde sempre <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> con una priorità molto bassa. Di conseguenza, il progetto File esterni restituisce sempre qualsiasi progetto con priorità più alta in grado di aprire i file.

 Il progetto File esterni non richiede all'utente di crearlo in modo esplicito con la finestra Project **finestra** di dialogo. Inoltre, il progetto File esterni non gestisce in modo permanente un elenco di membri del progetto. Usa una funzionalità facoltativa per registrare un elenco dei file usati più di recente per ogni utente.

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>
- <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>
- [Procedura: Aprire gli editor specifici del progetto](../../extensibility/how-to-open-project-specific-editors.md)
- [Procedura: Aprire gli editor standard](../../extensibility/how-to-open-standard-editors.md)
- [Aggiunta di modelli di progetto e di elementi di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Aggiunta di modelli di progetto e di elementi di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md)
