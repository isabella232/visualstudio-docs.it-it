---
title: Wizards Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], providing wizard support
ms.assetid: 59d9a77f-ee80-474b-a14f-90f477ab717b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d65cf2dcc10380b0ac750c8e1b0e7fd56eab95b5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703204"
---
# <a name="wizards"></a>Procedure guidate
Dopo aver creato una procedura guidata, in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] genere si desidera aggiungerla all'ambiente di sviluppo integrato (IDE) in modo che altri utenti possano utilizzarla. La procedura guidata aggiunta viene quindi visualizzata nelle finestre di dialogo **Aggiungi nuovo progetto** o Aggiungi nuovo **elemento.** Per visualizzare le finestre di dialogo **Aggiungi nuovo progetto** o Aggiungi nuovo **elemento** , fare clic con il pulsante destro del mouse su una soluzione aperta in **Esplora soluzioni**, **scegliere Aggiungi**, quindi fare clic su Nuovo **progetto** o **Nuovo elemento**.

 Le procedure guidate [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] possono essere implementate in modo da consentire agli utenti di selezionare da una visualizzazione struttura ad albero dei valori disponibili quando aprono la finestra di dialogo **Aggiungi nuovo progetto** o Aggiungi nuovo **elemento** oppure quando fanno clic con il pulsante destro del mouse su un elemento in **Esplora soluzioni**.

 Nella procedura guidata è possibile fornire l'opzione di localizzazione del nome di un nuovo progetto o di un nuovo progetto ed è possibile determinare l'icona che gli utenti vedranno quando selezionano la procedura guidata. È inoltre possibile controllare l'ordine in cui i nuovi elementi vengono visualizzati rispetto ad altri elementi disponibili; gli elementi non devono essere organizzati in ordine alfabetico.

 È inoltre possibile fornire una procedura guidata che viene avviata in modo diverso, in base ai parametri personalizzati passati alla procedura guidata quando viene aperta.

 Negli argomenti di questa sezione vengono illustrati [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] i file implementati per causare le finestre di dialogo **Aggiungi nuovo progetto** e Aggiungi nuovo **elemento** per elencare la procedura guidata tra le procedure guidate e i modelli disponibili e i requisiti che la procedura guidata deve soddisfare per funzionare correttamente nell'IDE.

## <a name="in-this-section"></a>Contenuto della sezione
- [File (con estensione vsdir) di descrizione della directory dei modelli](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)

 Viene fornita una panoramica dei file di descrizione della directory dei modelli e viene illustrato il funzionamento dell'IDE per visualizzare cartelle, file vsz della procedura guidata e file modello associati a un progetto nelle finestre di dialogo.

- [File (con estensione vsz) della procedura guidata](../../extensibility/internals/wizard-dot-vsz-file.md)

 Viene illustrato come l'IDE avvia procedure guidate ed elenca le tre parti del file vsz.

- [Interfaccia della procedura guidata (IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)

 Viene descritta l'interfaccia `IDTWizard` che le procedure guidate devono implementare per funzionare nell'IDE.

- [Parametri di contesto](../../extensibility/internals/context-parameters.md)

 Viene illustrato come vengono implementate le procedure guidate e cosa si verifica quando l'IDE passa i parametri di contesto all'implementazione.

- [Parametri personalizzati](../../extensibility/internals/custom-parameters.md)

 Viene illustrato come utilizzare i parametri personalizzati per controllare il funzionamento della procedura guidata dopo l'avvio della procedura guidata.

## <a name="related-sections"></a>Sezioni correlate
- [Tipi di progetto](../../extensibility/internals/project-types.md)

 Vengono forniti collegamenti ad argomenti aggiuntivi che offrono informazioni su come progettare nuovi tipi di progetto.

- [Estensione dei progetti](../../extensibility/extending-projects.md)

 Descrive come usare i progetti e le soluzioni di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per organizzare file di codice e file di risorse e come implementare il controllo del codice sorgente.
