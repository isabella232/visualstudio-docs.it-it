---
title: Aggiunta Project e Project modelli di elemento | Microsoft Docs
description: Informazioni sull'aggiunta di modelli di progetto e di elemento di progetto alle finestre di dialogo nell'ambiente Visual Studio di sviluppo integrato (IDE).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: ae29f7d2d2e15cacc56d7c3fb42e7b86ee31be903032dc55dd5a61276360449d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121376430"
---
# <a name="add-project-and-project-item-templates"></a>Aggiungere modelli di progetto e di elemento di progetto
Quando si creano tipi di progetto personalizzati, è necessario fornire il supporto per l'aggiunta di nuovi progetti ed elementi di progetto tramite le finestre di dialogo dell'ambiente di sviluppo integrato [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (IDE) standard. Negli argomenti seguenti vengono illustrate diverse tecniche per l'aggiunta di progetti ed elementi di progetto.

## <a name="in-this-section"></a>Contenuto della sezione
- [Project contesto](../../extensibility/internals/project-context.md)

 Spiega che il progetto fornisce la maggior parte delle informazioni di contesto per ciò che traspira nell'ambiente.

- [Project priorità](../../extensibility/internals/project-priority.md)

 Spiega che un elemento di progetto è in genere membro di un progetto per evitare ambiguità sul progetto usato per aprire l'elemento.

- [Progetto File esterni](../../extensibility/internals/miscellaneous-files-project.md)

 Fornisce informazioni sui due tipi di editor che è possibile usare per aprire i file in un progetto e sul ruolo del progetto per determinare quale editor usare quando viene aperto un elemento di progetto.

- [Registrare modelli di progetto e di elemento](../../extensibility/internals/registering-project-and-item-templates.md)

 Spiega cosa accade quando viene [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] creato un progetto.

- [Aggiungere elementi alla finestra di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)

 Viene illustrato il processo per l'aggiunta di elementi alla **finestra di dialogo Aggiungi** nuovo elemento .

- [Aggiungere directory alla finestra di dialogo Project nuova cartella](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)

 Fornisce un esempio di registrazione di una nuova directory che contiene modelli personalizzati resi disponibili da un VSPackage.

- [Aggiungere directory alla finestra di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)

 Viene fornito un esempio di registrazione di un nuovo set di directory per la **finestra di** dialogo Aggiungi nuovo elemento .

- [Comandi definiti dall'IDE per l'estensione di sistemi di progetto](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)

 Elenca i diversi tipi di elementi di comando usati per l'estensione dei sistemi di progetto.

- [CATID per gli oggetti in genere usati per estendere i progetti](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)

 Elenca i CATID per gli oggetti utilizzati per estendere [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] i sistemi di progetto , e [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] .

## <a name="related-sections"></a>Sezioni correlate
- [Procedura: Aprire editor specifici del progetto](../../extensibility/how-to-open-project-specific-editors.md)

 Fornisce istruzioni dettagliate per l'apertura intrinseca di un elemento associato a un editor specifico per un progetto.

- [Procedura: Aprire editor standard](../../extensibility/how-to-open-standard-editors.md)

 Fornisce istruzioni dettagliate per l'apertura di un editor standard.

- [Project sottotipi](../../extensibility/internals/project-subtypes.md)

 Vengono forniti collegamenti ad argomenti concettuali relativi al sottotipo di progetto. Project sottotipi estendono i [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] progetti e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] esistenti.

- [Project tipi](../../extensibility/internals/project-types.md)

 Vengono forniti collegamenti ad argomenti aggiuntivi che offrono informazioni su come progettare nuovi tipi di progetto.
