---
title: Contributo al modello di automazione | Microsoft Docs
description: Informazioni su come contribuire al modello di automazione Visual Studio seguendo un set di linee guida durante la progettazione di un VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 8b3cd5951b0ffe8a933c2920dfc1a7e107c5bf6f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122063590"
---
# <a name="contribute-to-the-automation-model"></a>Contribuire al modello di automazione
Visual Studio fornisce un set di interfacce di automazione per la personalizzazione dell'ambiente. Il modello di automazione è il modello a oggetti che consente agli utenti finali di creare Visual Studio componenti aggiuntivi ed estensioni.

 Inoltre, è opportuno che gli sviluppatori VSPackage contribuiscano al modello di automazione. In questo modo, si abilitano gli utenti finali del pacchetto VSPackage per creare componenti aggiuntivi e in genere offrono un'esperienza di modello utente coerente quando usano il pacchetto VSPackage in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

 Per rendere coerente l'esperienza dell'utente finale, è possibile seguire un set di linee guida durante la progettazione del vspackage in modo che il modello di automazione per il pacchetto VSPackage segua le idee in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="in-this-section"></a>Contenuto della sezione
- [Panoramica del modello di automazione](../../extensibility/internals/automation-model-overview.md)

 Definisce il modello di automazione come gruppi correlati di oggetti che controllano i facet principali dell'ambiente comune. Questo set di oggetti è riportato in un diagramma del modello di automazione.

- [Fornire automazione per VSPackage](../../extensibility/internals/providing-automation-for-vspackages.md)

 Vengono illustrati i due modi principali per fornire l'automazione per il pacchetto VSPackage.

- [Esporre oggetti di progetto](../../extensibility/internals/exposing-project-objects.md)

 Fornisce istruzioni dettagliate per la creazione di oggetti specifici di VSPackage.

- [Project modellazione](../../extensibility/internals/project-modeling.md)

 Illustra gli oggetti di progetto standard necessari per creare l'automazione per il nuovo tipo di progetto e illustra il percorso seguito dall'automazione del progetto. Questo argomento fornisce anche elenchi di dichiarazioni e implementazione per le classi.

- [Esporre gli eventi](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)

 Fornisce istruzioni dettagliate per la creazione di eventi per il modello di automazione.

- [Supporto dell'automazione per le pagine delle opzioni](../../extensibility/internals/automation-support-for-options-pages.md)

 Viene descritto come restituire un oggetto di automazione per  supportare le proprietà della finestra di dialogo Opzioni personalizzate di un pacchetto VSPackage nel **menu** Strumenti estendendo l'oggetto `DTE.Properties` .

- [Fornire automazione per il codice](../../extensibility/internals/providing-automation-for-code.md)

 Spiega che la creazione di un modello di automazione per il codice non è necessaria. In questo argomento viene tuttavia fornito un collegamento che fornisce informazioni dettagliate sui modelli di codice.

- [Procedura: Fornire automazione per Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md)

 Spiega che fornire automazione è una buona idea ogni volta che si vogliono rendere disponibili gli oggetti di automazione in una finestra e che l'ambiente non fornisce già un oggetto di automazione già pronto. Viene illustrata l'automazione per le finestre degli strumenti e le finestre dei documenti.

- [Usare il modello di automazione](../../extensibility/internals/using-the-automation-model.md)

 Vengono forniti due esempi di codice che illustrano come un consumer di automazione ottiene gli oggetti di automazione del progetto iniziali.

- [Automazione per gli oggetti Configuration e SelectedItem](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)

 Fornisce informazioni sull'automazione per gli oggetti Configuration e SelectedItems.

## <a name="reference"></a>Riferimento
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> Fornisce un esempio di codice che illustra come un VSPackage partecipa al modello a oggetti di automazione DTE. Elenca i parametri, i valori restituiti e le osservazioni selezionate.
