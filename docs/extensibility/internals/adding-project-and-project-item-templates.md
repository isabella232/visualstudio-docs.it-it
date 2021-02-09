---
title: Aggiunta di modelli di progetti e di elementi di progetto | Microsoft Docs
description: Informazioni sull'aggiunta di modelli di progetto e di elementi di progetto nelle finestre di dialogo di Visual Studio Integrated Development Environment (IDE).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8ff54e24408577ba8bfbf553a5c641eab2d15814
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906231"
---
# <a name="add-project-and-project-item-templates"></a>Aggiungere modelli di progetti e di elementi di progetto
Quando si creano tipi di progetto personalizzati, è necessario fornire supporto per l'aggiunta di nuovi progetti ed elementi di progetto utilizzando le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] finestre di dialogo standard Integrated Development Environment (IDE). Negli argomenti seguenti vengono illustrate diverse tecniche per l'aggiunta di progetti ed elementi di progetto.

## <a name="in-this-section"></a>Contenuto della sezione
- [Contesto del progetto](../../extensibility/internals/project-context.md)

 Viene illustrato come il progetto fornisca la maggior parte delle informazioni di contesto relative a ciò che traspare nell'ambiente.

- [Priorità progetto](../../extensibility/internals/project-priority.md)

 Viene illustrato che un elemento del progetto è in genere un membro di un progetto per evitare ambiguità sul progetto utilizzato per aprire l'elemento.

- [Progetto di file esterni](../../extensibility/internals/miscellaneous-files-project.md)

 Vengono fornite informazioni sui due tipi di editor che possono essere utilizzati per aprire i file in un progetto e il ruolo riprodotto dal progetto per determinare quale editor utilizzare quando viene aperto un elemento del progetto.

- [Registrare modelli di progetti e di elementi](../../extensibility/internals/registering-project-and-item-templates.md)

 Viene illustrato cosa accade quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] viene creato un progetto.

- [Aggiungi elementi alla finestra di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)

 Viene illustrato il processo per l'aggiunta di elementi alla finestra di dialogo **Aggiungi nuovo elemento** .

- [Aggiungi directory alla finestra di dialogo nuovo progetto](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)

 Viene fornito un esempio di registrazione di una nuova directory che contiene modelli personalizzati resi disponibili da un pacchetto VSPackage.

- [Aggiungere directory alla finestra di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)

 Viene fornito un esempio di registrazione di un nuovo set di directory per la finestra di dialogo **Aggiungi nuovo elemento** .

- [Comandi definiti dall'IDE per l'estensione dei sistemi di progetto](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)

 Elenca i diversi tipi di elementi di comando utilizzati per estendere i sistemi di progetto.

- [CATID per gli oggetti che in genere vengono usati per estendere i progetti](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)

 Elenca CATID per gli oggetti utilizzati per estendere i [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] sistemi di progetto, e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] .

## <a name="related-sections"></a>Sezioni correlate
- [Procedura: aprire editor specifici del progetto](../../extensibility/how-to-open-project-specific-editors.md)

 Vengono fornite istruzioni dettagliate per l'apertura di un elemento associato in modo intrinseco a un editor specifico per un progetto.

- [Procedura: aprire gli editor standard](../../extensibility/how-to-open-standard-editors.md)

 Vengono fornite istruzioni dettagliate per l'apertura di un editor standard.

- [Sottotipi di progetto](../../extensibility/internals/project-subtypes.md)

 Vengono forniti collegamenti agli argomenti concettuali del sottotipo di progetto. I sottotipi di progetto estendono i [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] progetti e esistenti [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] .

- [Tipi di progetto](../../extensibility/internals/project-types.md)

 Fornisce collegamenti ad argomenti aggiuntivi che offrono informazioni su come progettare nuovi tipi di progetto.
