---
title: Finestra di dialogo Selezione URL (SharePoint sviluppo)
description: Informazioni sulla finestra di dialogo Selezione URL, che consente a un utente di scegliere i file presenti nel progetto o nel server locale che esegue SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.VWD.URLPicker
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, URL picker
- SharePoint development in Visual Studio, designer
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 22f05833ca2937a44d5d731bdef06d8971a3e57d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122156201"
---
# <a name="url-picker-dialog-box-sharepoint-development-in-visual-studio"></a>Finestra di dialogo Selezione URL (SharePoint sviluppo in Visual Studio)
  Nella finestra di dialogo di selezione URL è possibile scegliere i file come file di pagina master o file di immagine posizionati nel progetto o nel server locale in cui è in esecuzione SharePoint.

 Questa finestra di dialogo viene visualizzata se è possibile scegliere un file per impostare una proprietà. È possibile aprire questa finestra di dialogo scegliendo il pulsante con i puntini di sospensione ( ASP.NET ![Mobile Designer](../sharepoint/media/mwellipsis.gif "Ellisse di ASP.NET Mobile Designer")) accanto a varie proprietà nella **finestra** Proprietà. Il pulsante con i puntini di sospensione viene visualizzato anche come prompt intelliSense quando si assegnano valori a determinati attributi nella **visualizzazione Origine** della finestra di progettazione.

## <a name="uielement-list"></a>Elenco degli elementi di interfaccia
 **Project cartelle** Visualizza un elenco delle cartelle definite nel progetto o nel server locale che esegue SharePoint. Scegliere il pulsante di espansione per visualizzare le sottocartelle.

 Espandere il **Project** per scegliere i file nel progetto. Per essere visualizzati come selezionabili nella finestra di dialogo, i file nel progetto devono soddisfare i criteri seguenti:

- Il file deve essere contenuto in una cartella mappata.

- Il file deve essere aggiunto al pacchetto della soluzione.

- Il file non può trovarsi in un altro progetto.

  Se si desidera fare riferimento a file che non soddisfano questi criteri, è necessario immettere manualmente il percorso del file.

  Espandere il **nodo Server** per scegliere i file che si trovano nel server locale che esegue SharePoint. Per essere visualizzati come selezionabili nella finestra di dialogo, questi file devono soddisfare i criteri seguenti:

- Il file deve trovarsi in una delle cartelle mappate seguenti: **Images,** **Layouts** o **ControlTemplates.**

- Il file non può essere posizionato nel database SharePoint contenuto.

  Se si desidera fare riferimento a file che non soddisfano questi criteri, è necessario immettere manualmente il percorso del file.

  **Contenuto della cartella** Visualizza un elenco di file nella cartella selezionata. Scegliere un file e quindi fare clic sul **pulsante OK** per chiudere la finestra di dialogo e inviare la selezione al processo che lo ha chiamato.

  **File di tipo** Consente di scegliere da un elenco di file appropriati per l'attività che si sta eseguendo.

## <a name="see-also"></a>Vedi anche
- [Creare pagine dell'applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)
- [Creare web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Creare controlli riutilizzabili per web part o pagine dell'applicazione](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
