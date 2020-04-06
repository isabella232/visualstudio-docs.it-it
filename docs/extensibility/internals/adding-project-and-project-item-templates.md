---
title: Aggiunta di modelli di progetto e di elemento di progetto Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 14eb1a9e2e63fa6e63d3ba2efa4426421e6b5593
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710204"
---
# <a name="add-project-and-project-item-templates"></a>Aggiungere modelli di progetto e di elemento di progettoAdd project and project item templates
Quando si creano tipi di progetto personalizzati, è necessario fornire supporto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per l'aggiunta di nuovi progetti ed elementi di progetto utilizzando le finestre di dialogo dell'ambiente di sviluppo integrato (IDE) standard. Negli argomenti seguenti vengono illustrate diverse tecniche per l'aggiunta di progetti ed elementi di progetto.

## <a name="in-this-section"></a>Contenuto della sezione
- [Contesto del progetto](../../extensibility/internals/project-context.md)

 Spiega che il progetto fornisce la maggior parte delle informazioni di contesto per ciò che traspare nell'ambiente.

- [Priorità del progetto](../../extensibility/internals/project-priority.md)

 Viene illustrato che un elemento di progetto è in genere un membro di un progetto per evitare ambiguità sul progetto utilizzato per aprire l'elemento.

- [Progetto File vari](../../extensibility/internals/miscellaneous-files-project.md)

 Fornisce informazioni sui due tipi di editor che possono essere utilizzati per aprire i file in un progetto e sul ruolo del progetto nel determinare l'editor da utilizzare quando viene aperto un elemento di progetto.

- [Registrare modelli di progetto e di elemento](../../extensibility/internals/registering-project-and-item-templates.md)

 Viene illustrato ciò [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] che si verifica quando viene creato un progetto.

- [Aggiungere elementi alla finestra di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)

 Viene illustrato il processo di aggiunta di elementi alla finestra di dialogo **Aggiungi nuovo elemento.**

- [Aggiungere directory alla finestra di dialogo Nuovo progetto](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)

 Viene fornito un esempio di registrazione di una nuova directory che contiene modelli personalizzati resi disponibili da un pacchetto VSPackage.

- [Aggiungere directory alla finestra di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)

 Viene fornito un esempio di registrazione di un nuovo set di directory per la finestra di dialogo **Aggiungi nuovo elemento.**

- [Comandi definiti dall'IDE per l'estensione dei sistemi di progetto](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)

 Elenca diversi tipi di elementi di comando utilizzati per estendere i sistemi di progetto.

- [CATID per gli oggetti che vengono in genere utilizzati per estendere i progetti](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)

 Elenca i CATID per gli oggetti [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]utilizzati [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] per estendere i sistemi , e project.

## <a name="related-sections"></a>Sezioni correlate
- [Procedura: aprire editor specifici del progettoHow to: Open project-specific editors](../../extensibility/how-to-open-project-specific-editors.md)

 Vengono fornite istruzioni dettagliate per l'apertura di un elemento intrinsecamente associato a un editor specifico per un progetto.

- [Procedura: aprire gli editor standardHow to: Open standard editors](../../extensibility/how-to-open-standard-editors.md)

 Fornisce istruzioni dettagliate per l'apertura di un editor standard.

- [Sottotipi di progetto](../../extensibility/internals/project-subtypes.md)

 Vengono forniti collegamenti ad argomenti concettuali del sottotipo di progetto. I sottotipi [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] di [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] progetto estendono progetti e esistenti.

- [Tipi di progetto](../../extensibility/internals/project-types.md)

 Vengono forniti collegamenti ad argomenti aggiuntivi che offrono informazioni su come progettare nuovi tipi di progetto.
