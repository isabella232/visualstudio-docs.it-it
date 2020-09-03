---
title: 'Procedura: aggiungere un nuovo elemento a un progetto flusso di lavoro (legacy) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- sequential workflows, adding to workflow projects
- workflows, adding new items
- state machine workflows, adding to workflow projects
- activities, adding to workflow projects
ms.assetid: 130cd83d-942d-437b-bbb5-8088ec0a6d79
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 46f6e9daafc2688b9bea75cba9eddd8c8a53c9bb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656666"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project-legacy"></a>Procedura: aggiungere un nuovo elemento a un progetto flusso di lavoro [legacy]
Dopo avere creato un progetto flusso di lavoro usando la [!INCLUDE[wfd1](../includes/wfd1-md.md)] legacy fornita da [!INCLUDE[vs2010](../includes/vs2010-md.md)] che si riferisce a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)], è possibile aggiungere elementi [!INCLUDE[wf](../includes/wf-md.md)] e altri elementi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] comuni al progetto.

 Nella tabella seguente sono elencati gli elementi [!INCLUDE[wf2](../includes/wf2-md.md)] che è possibile aggiungere a un progetto flusso di lavoro.

|Elemento|Descrizione|
|----------|-----------------|
|Attività|Attività con definizione di attività in un file di codice della finestra di progettazione e codice utente in un file di codice separato.|
|Attività (con separazione del codice)|Definizione di attività espressa come markup del flusso di lavoro e codice utente in un file di codice separato.|
|Flusso di lavoro sequenziale (codice)|Flusso di lavoro sequenziale con definizione del flusso di lavoro in un file di codice della finestra di progettazione e codice utente in un file di codice separato.|
|Flusso di lavoro sequenziale (con separazione del codice)|Flusso di lavoro sequenziale con definizione del flusso di lavoro espressa come markup del flusso di lavoro e codice utente in un file di codice separato.|
|Flusso di lavoro di una macchina a stati (codice)|Flusso di lavoro di una macchina a stati con definizione del flusso di lavoro in un file di codice della finestra di progettazione e codice utente in un file di codice separato.|
|Flusso di lavoro della macchina a stati (con separazione del codice)|Flusso di lavoro della macchina a stati con definizione del flusso di lavoro espressa come markup del flusso di lavoro e codice utente in un file di codice separato.|

### <a name="to-add-a-new-item-to-a-workflow-project"></a>Per aggiungere un nuovo elemento a un progetto flusso di lavoro

1. Scegliere **Aggiungi nuovo elemento**dal menu **progetto** .

     Verrà visualizzata la finestra **di dialogo Aggiungi nuovo elemento** .

2. Selezionare un elemento.

     La tabella precedente elenca le selezioni di Windows Workflow Foundation disponibili.

3. Fare clic su **Aggiungi** per aggiungere l'elemento al progetto flusso di lavoro.

## <a name="see-also"></a>Vedere anche
 [Creazione di progetti flusso di lavoro legacy](../workflow-designer/creating-legacy-workflow-projects.md)