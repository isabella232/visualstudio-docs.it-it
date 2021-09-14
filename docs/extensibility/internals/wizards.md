---
title: Procedure guidate | Microsoft Docs
description: Informazioni su come elencare la procedura guidata tra le procedure guidate e i modelli disponibili Visual Studio e sui requisiti che la procedura guidata deve soddisfare nell'IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], providing wizard support
ms.assetid: 59d9a77f-ee80-474b-a14f-90f477ab717b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 8c652e67db103350a9e3fa92e08212422caae424
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126711722"
---
# <a name="wizards"></a>Procedure guidate
Dopo aver creato una procedura guidata, in genere si vuole aggiungerla all'ambiente di sviluppo integrato (IDE) in modo che altri utenti [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] possano usarla. La procedura guidata aggiunta viene quindi visualizzata nelle **finestre di dialogo Aggiungi nuovo Project** o Aggiungi **nuovo** elemento. Per visualizzare le finestre di  dialogo Aggiungi nuovo **Project** o Aggiungi nuovo elemento, fare clic con il pulsante destro del mouse su una soluzione aperta **in Esplora soluzioni**, scegliere Aggiungi **e** quindi fare clic su Nuovo **Project** o **Nuovo elemento**.

 Le procedure guidate possono essere implementate in per consentire agli utenti di selezionare da una visualizzazione albero dei valori disponibili quando aprono la finestra di dialogo Aggiungi nuovo Project o Aggiungi nuovo elemento oppure quando fanno clic con il pulsante destro del mouse su un elemento [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] in **Esplora soluzioni**.  

 Nella procedura guidata è possibile specificare l'opzione per la localizzazione del nome di un nuovo progetto o di esso ed è possibile determinare l'icona che verrà visualizzata dagli utenti quando selezionano la procedura guidata. È anche possibile controllare l'ordine di visualizzazione dei nuovi elementi rispetto ad altri elementi disponibili. Gli elementi non devono essere organizzati in ordine alfabetico.

 È anche possibile specificare una procedura guidata che viene avviata in modo diverso, in base ai parametri personalizzati passati alla procedura guidata quando viene aperta.

 Negli argomenti di questa sezione vengono illustrati i file implementati per fare in modo che le finestre di dialogo Aggiungi nuovo Project e Aggiungi nuovo elemento elenchino la procedura guidata tra le procedure guidate e i modelli disponibili e i requisiti che la procedura guidata deve soddisfare per funzionare correttamente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]  nell'IDE. 

## <a name="in-this-section"></a>Contenuto della sezione
- [File (con estensione vsdir) di descrizione della directory dei modelli](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)

 Fornisce una panoramica dei file di descrizione della directory dei modelli e spiega come funzionano nell'IDE per visualizzare le cartelle, i file vsz della procedura guidata e i file modello associati a un progetto nelle finestre di dialogo.

- [File (con estensione vsz) della procedura guidata](../../extensibility/internals/wizard-dot-vsz-file.md)

 Illustra come l'IDE avvia le procedure guidate ed elenca le tre parti del file vsz.

- [Interfaccia della procedura guidata (IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)

 Descrive `IDTWizard` l'interfaccia che le procedure guidate devono implementare per funzionare nell'IDE.

- [Parametri di contesto](../../extensibility/internals/context-parameters.md)

 Illustra come vengono implementate le procedure guidate e cosa accade quando l'IDE passa parametri di contesto all'implementazione.

- [Parametri personalizzati](../../extensibility/internals/custom-parameters.md)

 Viene illustrato come usare i parametri personalizzati per controllare il funzionamento della procedura guidata dopo l'avvio della procedura guidata.

## <a name="related-sections"></a>Sezioni correlate
- [Project Types](../../extensibility/internals/project-types.md) (Tipi di progetto)

 Vengono forniti collegamenti ad argomenti aggiuntivi che offrono informazioni su come progettare nuovi tipi di progetto.

- [Estensione dei progetti](../../extensibility/extending-projects.md)

 Descrive come usare i progetti e le soluzioni di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per organizzare file di codice e file di risorse e come implementare il controllo del codice sorgente.
