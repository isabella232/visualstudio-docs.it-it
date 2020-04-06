---
title: Contribuire al modello di automazione Documenti Microsoft
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
ms.openlocfilehash: d660edc740229c3e91b99e1f59eb37b4e9312098
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709261"
---
# <a name="contribute-to-the-automation-model"></a>Contribuire al modello di automazione
Visual Studio fornisce un set di interfacce di automazione per la personalizzazione dell'ambiente. Il modello di automazione è il modello a oggetti che consente agli utenti finali di creare componenti aggiuntivi ed estensioni di Visual Studio.The automation model is the object model that enables end users to create Visual Studio add-ins and extensions.

 Inoltre, è appropriato per l'utente, come sviluppatore VSPackage, per contribuire al modello di automazione; In questo modo, si consente agli utenti finali del pacchetto VSPackage per creare componenti aggiuntivi e [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]in genere fornire un'esperienza coerente del modello utente quando utilizzano il pacchetto VSPackage in .

 Per rendere coerente l'esperienza dell'utente finale, è possibile seguire una serie di linee guida durante [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]la progettazione del pacchetto VSPackage in modo che il modello di automazione per il pacchetto VSPackage segue le idee in .

## <a name="in-this-section"></a>Contenuto della sezione
- [Panoramica del modello di automazione](../../extensibility/internals/automation-model-overview.md)

 Definisce il modello di automazione come un gruppo correlato di oggetti che controllano i principali aspetti dell'ambiente comune. Questo set di oggetti è illustrato in un diagramma del modello di automazione.

- [Fornire l'automazione per i pacchetti VSPackageProvide automation for VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md)

 Vengono illustrati i due modi principali per fornire l'automazione per il pacchetto VSPackage.

- [Esporre gli oggetti del progetto](../../extensibility/internals/exposing-project-objects.md)

 Fornisce istruzioni dettagliate per la creazione di oggetti specifici di VSPackage.

- [Modellazione del progetto](../../extensibility/internals/project-modeling.md)

 Vengono illustrati gli oggetti di progetto standard necessari per creare l'automazione per il nuovo tipo di progetto e viene illustrato il percorso che segue l'automazione del progetto. In questo argomento vengono inoltre forniti elenchi di dichiarazioni e implementazione per le classi.

- [Esporre eventi](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)

 Vengono fornite istruzioni dettagliate per la creazione di eventi per il modello di automazione.

- [Supporto di automazione per le pagine di opzioni](../../extensibility/internals/automation-support-for-options-pages.md)

 Viene descritto come restituire un oggetto di automazione per il supporto delle proprietà di `DTE.Properties` un VSPackage personalizzato **Opzioni** finestra di dialogo il **strumento** menu estendendo l'oggetto.

- [Fornire l'automazione per il codiceProvide automation for code](../../extensibility/internals/providing-automation-for-code.md)

 Viene illustrato che la creazione di un modello di automazione per il codice non è necessaria. Tuttavia, in questo argomento viene fornito un collegamento che fornisce informazioni dettagliate nei modelli di codice.

- [Procedura: fornire l'automazione per WindowsHow to: Provide automation for Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md)

 Viene illustrato che fornire l'automazione è una buona idea ogni volta che si desidera rendere disponibili gli oggetti di automazione in una finestra e l'ambiente non fornisce già un oggetto di automazione già pronto. Viene illustrata l'automazione per le finestre degli strumenti e le finestre dei documenti.

- [Utilizzare il modello di automazione](../../extensibility/internals/using-the-automation-model.md)

 Vengono forniti due esempi di codice che illustrano come un consumer di automazione ottiene gli oggetti di automazione del progetto iniziale.

- [Automazione per gli oggetti Configuration e SelectedItem](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)

 Fornisce informazioni sull'automazione per gli oggetti Configuration e SelectedItems.

## <a name="reference"></a>Informazioni di riferimento
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>Fornisce un esempio di codice che mostra come un VSPackage partecipa al modello a oggetti di automazione DTE. Elenca i parametri, i valori restituiti e le osservazioni selezionate.
