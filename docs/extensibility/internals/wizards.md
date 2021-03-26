---
title: Procedure guidate | Microsoft Docs
description: Informazioni su come elencare la procedura guidata tra le procedure guidate e i modelli disponibili in Visual Studio e sui requisiti che la procedura guidata deve soddisfare nell'IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], providing wizard support
ms.assetid: 59d9a77f-ee80-474b-a14f-90f477ab717b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b5c5cb9649689f711844f97e0b57ab23248e9a00
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074158"
---
# <a name="wizards"></a>Procedure guidate
Dopo aver creato una procedura guidata, in genere si vuole aggiungerla al [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Integrated Development Environment (IDE) in modo che altri utenti possano usarlo. La procedura guidata aggiunta viene quindi visualizzata nelle finestre di dialogo **Aggiungi nuovo progetto** o **Aggiungi nuovo elemento** . Per visualizzare le finestre di dialogo **Aggiungi nuovo progetto** o **Aggiungi nuovo elemento** , fare clic con il pulsante destro del mouse su una soluzione aperta in **Esplora soluzioni**, scegliere **Aggiungi**, quindi fare clic su **nuovo progetto** o **nuovo elemento**.

 È possibile implementare procedure guidate in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per consentire agli utenti di selezionare una visualizzazione albero dei valori disponibili quando aprono la finestra di dialogo **Aggiungi nuovo progetto** o **Aggiungi nuovo elemento** oppure facendo clic con il pulsante destro del mouse su un elemento in **Esplora soluzioni**.

 Nella procedura guidata è possibile specificare la possibilità di localizzare il nome di un nuovo progetto o ites ed è possibile determinare l'icona che verrà visualizzata dagli utenti quando selezionano la procedura guidata. È anche possibile controllare l'ordine in cui vengono visualizzati i nuovi elementi rispetto ad altri elementi disponibili; gli elementi non devono essere organizzati in ordine alfabetico.

 È anche possibile fornire una procedura guidata che viene avviata in modo diverso, in base ai parametri personalizzati passati alla procedura guidata quando viene aperta.

 Negli argomenti di questa sezione vengono illustrati i file implementati per fare in modo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] che le finestre di dialogo **Aggiungi nuovo progetto** e **Aggiungi nuovo elemento** elenchino la procedura guidata tra le procedure guidate e i modelli disponibili e i requisiti che la procedura guidata deve soddisfare per funzionare correttamente nell'IDE.

## <a name="in-this-section"></a>Contenuto della sezione
- [File (con estensione vsdir) di descrizione della directory dei modelli](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)

 Viene fornita una panoramica dei file di descrizione della directory dei modelli e viene illustrata la relativa funzione nell'IDE per la visualizzazione di cartelle, file con estensione vsz della procedura guidata e file di modello associati a un progetto nelle finestre di dialogo.

- [File (con estensione vsz) della procedura guidata](../../extensibility/internals/wizard-dot-vsz-file.md)

 Viene illustrato il modo in cui l'IDE avvia le procedure guidate ed elenca le tre parti del file con estensione vsz.

- [Interfaccia della procedura guidata (IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)

 Descrive l' `IDTWizard` interfaccia che deve essere implementata dalle procedure guidate per lavorare nell'IDE.

- [Parametri di contesto](../../extensibility/internals/context-parameters.md)

 Illustra il modo in cui vengono implementate le procedure guidate e cosa accade quando l'IDE passa parametri di contesto all'implementazione.

- [Parametri personalizzati](../../extensibility/internals/custom-parameters.md)

 Viene illustrato come utilizzare parametri personalizzati per controllare l'operazione della procedura guidata dopo l'avvio della procedura guidata.

## <a name="related-sections"></a>Sezioni correlate
- [Project Types](../../extensibility/internals/project-types.md) (Tipi di progetto)

 Fornisce collegamenti ad argomenti aggiuntivi che offrono informazioni su come progettare nuovi tipi di progetto.

- [Estensione dei progetti](../../extensibility/extending-projects.md)

 Descrive come usare i progetti e le soluzioni di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per organizzare file di codice e file di risorse e come implementare il controllo del codice sorgente.
