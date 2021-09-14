---
title: Linee guida per l'importazione di flussi di lavoro riutilizzabili | Microsoft Docs
description: Esaminare le linee guida per l'importazione di flussi di lavoro riutilizzabili creati in SharePoint Designer in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- SharePoint development in Visual Studio, reusable workflows
- importing items [SharePoint development in Visual Studio]
- reusable workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: a65af6481b9cffbff268553f93acd7105066aa1c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625206"
---
# <a name="guidelines-for-importing-reusable-workflows"></a>Linee guida per l'importazione di flussi di lavoro riutilizzabili
  Per importare flussi di lavoro riutilizzabili creati in SharePoint Designer, utilizzare il modello di progetto Importa flusso di lavoro riutilizzabile di SharePoint 2010 in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Questo modello importa un *flusso di lavoro*  dichiarativo (solo ) e lo converte in un flusso di lavoro del codice , ovvero un flusso di lavoro che è possibile migliorare con il codice [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] o  [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] . [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Procedura dettagliata: Importare un flusso di lavoro riutilizzabile SharePoint Designer in Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).

 Tuttavia, con il modello Importa flusso di lavoro riutilizzabile di SharePoint 2010 è possibile importare solo soluzioni farm. Se si desidera distribuire il flusso di lavoro come soluzione creata mediante sandbox, importarlo con il modello Importa pacchetto di soluzione SharePoint 2010. Tuttavia, in questo caso, non è possibile convertirlo in un flusso di lavoro di codice e quindi non sarà possibile modificarlo.

## <a name="import-reusable-workflows-by-using-the-import-reusable-workflow-template"></a>Importare flussi di lavoro riutilizzabili usando il modello Importa flusso di lavoro riutilizzabile
 Se si importa un flusso di lavoro riutilizzabile tramite il modello Importa flusso di lavoro riutilizzabile di SharePoint 2010, sarà possibile eseguire o modificare la soluzione proprio come con qualsiasi altra soluzione di SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], tuttavia potrebbe essere necessario correggere manualmente alcuni elementi.

### <a name="import-task-forms"></a>Importare moduli attività
 Con il modello di progetto Importa flusso di lavoro riutilizzabile di SharePoint 2010 vengono importati tutti i form di avvio e associazione, ma viene importato un solo form di attività poiché lo schema del flusso di lavoro di codice consente la presenza di un solo form di questo tipo. Eventuali moduli attività aggiuntivi della soluzione del flusso di lavoro originale vengono inseriti nella cartella Altri **file** importati in **Esplora soluzioni**.

## <a name="import-reusable-workflows-by-using-the-import-sharepoint-2010-solution-package-template"></a>Importare flussi di lavoro riutilizzabili usando il modello Importa SharePoint pacchetto della soluzione 2010
 Se si importa un flusso di lavoro riutilizzabile tramite il modello Importa pacchetto di soluzione SharePoint 2010, è necessario considerare i problemi riportati di seguito.

- Dopo aver importato il flusso di lavoro, è possibile distribuirlo ed eseguirlo immediatamente in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] premendo **F5.** Tuttavia, se si modifica un elemento nel flusso di lavoro nella soluzione importata, potrebbe essere necessario correggere manualmente gli elementi nel progetto prima di poter distribuire ed eseguire il flusso di lavoro.

- Poiché il flusso di lavoro è dichiarativo, non è possibile aggiungere codice. Per convertire il flusso di lavoro in un flusso di lavoro del codice, è necessario importarlo in usando il modello Importa flusso di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] lavoro riutilizzabile SharePoint 2010.

- Anche se è possibile modificare il file di progettazione del flusso di lavoro (con estensione xoml) nella visualizzazione Progettazione, è consigliabile modificarlo nella visualizzazione Origine, perché in Progettazione flussi di lavoro vengono visualizzati errori falsi.

- Il debug nel flusso di lavoro non funziona per il contenuto dichiarativo. I punti di interruzione impostati in [!INCLUDE[wfd2](../sharepoint/includes/wfd2-md.md)] non vengono raggiunto.

## <a name="import-globally-reusable-workflow-solutions"></a>Importare soluzioni flusso di lavoro riutilizzabili a livello globale
 Non è possibile importare flussi di lavoro riutilizzabili globalmente tramite il modello Importa flusso di lavoro riutilizzabile di SharePoint 2010. Per importare un flusso di lavoro riutilizzabile globalmente, è necessario convertirlo in un flusso di lavoro riutilizzabile non globalmente o utilizzare il modello Importa pacchetto di soluzione SharePoint 2010.

 Per convertire il flusso di lavoro, creare una copia del flusso di lavoro riutilizzabile a livello globale in SharePoint Designer (aprendo il menu di scelta rapida per il flusso di lavoro e quindi scegliendo Salva come **copia).** Successivamente, importare il nuovo flusso di lavoro riutilizzabile con il modello Importa flusso di lavoro riutilizzabile di SharePoint 2010 in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

 Per importare il flusso di lavoro riutilizzabile globalmente senza modificarlo, utilizzare il modello Importa pacchetto di soluzione SharePoint 2010. Se si utilizza questo metodo, il flusso di lavoro non verrà convertito in un flusso di lavoro di codice e rimarrà un flusso di lavoro dichiarativo.

## <a name="see-also"></a>Vedi anche
- [Importare elementi da un sito SharePoint esistente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [Procedura dettagliata: Importare un flusso di lavoro riutilizzabile SharePoint Designer in Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)
