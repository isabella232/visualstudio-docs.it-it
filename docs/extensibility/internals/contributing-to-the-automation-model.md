---
title: Contribuire al modello di automazione | Microsoft Docs
description: Per informazioni su come contribuire al modello di automazione di Visual Studio, seguire una serie di linee guida per la progettazione di un pacchetto VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab43da108a8d4a3339c54973f60bf1bef6a74780
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305594"
---
# <a name="contribute-to-the-automation-model"></a>Contribuire al modello di automazione
Visual Studio fornisce un set di interfacce di automazione per la personalizzazione dell'ambiente. Il modello di automazione è il modello a oggetti che consente agli utenti finali di creare componenti aggiuntivi ed estensioni di Visual Studio.

 Inoltre, è appropriato per gli sviluppatori di pacchetti VSPackage per contribuire al modello di automazione. in questo modo si consente agli utenti finali del pacchetto VSPackage di creare componenti aggiuntivi e di offrire in genere un'esperienza coerente con un modello utente quando usano il pacchetto VSPackage in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

 Per garantire la coerenza dell'esperienza dell'utente finale, è possibile seguire un set di linee guida durante la progettazione del pacchetto VSPackage in modo che il modello di automazione per il pacchetto VSPackage segua le idee in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="in-this-section"></a>Contenuto della sezione
- [Panoramica del modello di automazione](../../extensibility/internals/automation-model-overview.md)

 Definisce il modello di automazione come gruppi di oggetti correlati che controllano i facet principali dell'ambiente comune. Questo set di oggetti è illustrato in un diagramma del modello di automazione.

- [Fornire l'automazione per i pacchetti VSPackage](../../extensibility/internals/providing-automation-for-vspackages.md)

 Vengono illustrati i due modi principali per fornire l'automazione per il pacchetto VSPackage.

- [Esporre oggetti progetto](../../extensibility/internals/exposing-project-objects.md)

 Vengono fornite istruzioni dettagliate per la creazione di oggetti specifici di VSPackage.

- [Modellazione del progetto](../../extensibility/internals/project-modeling.md)

 Vengono illustrati gli oggetti di progetto standard necessari per creare l'automazione per il nuovo tipo di progetto e viene illustrato il percorso seguito da automazione del progetto. In questo argomento vengono inoltre forniti elenchi di dichiarazioni e implementazione per le classi.

- [Esporre eventi](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)

 Vengono fornite istruzioni dettagliate per la creazione di eventi per il modello di automazione.

- [Supporto di automazione per le pagine opzioni](../../extensibility/internals/automation-support-for-options-pages.md)

 Viene descritto come restituire un oggetto di automazione per supportare le proprietà della finestra di dialogo **Opzioni** personalizzate di un VSPackage dal menu **strumenti** estendendo l' `DTE.Properties` oggetto.

- [Fornire l'automazione per il codice](../../extensibility/internals/providing-automation-for-code.md)

 Spiega che la creazione di un modello di automazione per il codice non è obbligatoria. In questo argomento viene tuttavia fornito un collegamento che fornisce informazioni dettagliate nei modelli di codice.

- [Procedura: fornire l'automazione per Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md)

 Spiega che la fornitura di automazione è una scelta consigliata quando si desidera rendere disponibili oggetti di automazione in una finestra e l'ambiente non fornisce già un oggetto di automazione pronto. Descrive l'automazione per le finestre degli strumenti e le finestre dei documenti.

- [Usare il modello di automazione](../../extensibility/internals/using-the-automation-model.md)

 In sono disponibili due esempi di codice che illustrano come un consumer di automazione ottiene gli oggetti di automazione del progetto iniziali.

- [Automazione per oggetti Configuration e SelectedItem](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)

 Fornisce informazioni sull'automazione per gli oggetti Configuration e SelectedItems.

## <a name="reference"></a>Informazioni di riferimento
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> Fornisce un esempio di codice che illustra il modo in cui un VSPackage partecipa al modello a oggetti di automazione DTE. Elenca i parametri, i valori restituiti e le osservazioni selezionate.
