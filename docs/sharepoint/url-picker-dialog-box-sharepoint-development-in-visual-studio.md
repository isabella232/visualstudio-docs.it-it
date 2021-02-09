---
title: Finestra di dialogo selezione URL (sviluppo per SharePoint)
description: Informazioni sulla finestra di dialogo di selezione URL, che consente a un utente di scegliere i file che si trovano nel progetto o nel server locale in cui è in esecuzione SharePoint.
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
ms.workload:
- office
ms.openlocfilehash: d04857f0e61e5d9f293d73902cd090f718c65cd0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892216"
---
# <a name="url-picker-dialog-box-sharepoint-development-in-visual-studio"></a>Finestra di dialogo selezione URL (sviluppo per SharePoint in Visual Studio)
  Nella finestra di dialogo di selezione URL è possibile scegliere i file come file di pagina master o file di immagine posizionati nel progetto o nel server locale in cui è in esecuzione SharePoint.

 Questa finestra di dialogo viene visualizzata se è possibile scegliere un file per impostare una proprietà. È possibile aprire questa finestra di dialogo scegliendo il pulsante con i puntini di sospensione (![ASP.NET Mobile Designer Ellipse](../sharepoint/media/mwellipsis.gif "Ellisse di ASP.NET Mobile Designer")) accanto a varie proprietà nella finestra **Proprietà** . Il pulsante con i puntini di sospensione viene visualizzato anche come prompt di IntelliSense quando si assegnano valori a determinati attributi nella visualizzazione **origine** della finestra di progettazione.

## <a name="uielement-list"></a>Elenco degli elementi di interfaccia
 **Cartelle di progetto** Visualizza un elenco delle cartelle definite nel progetto o nel server locale in cui è in esecuzione SharePoint. Scegliere il pulsante di espansione per visualizzare le sottocartelle.

 Espandere il nodo del **progetto** per scegliere i file nel progetto. Per visualizzare come selezionabile nella finestra di dialogo, i file del progetto devono soddisfare i criteri seguenti:

- Il file deve essere contenuto in una cartella mappata.

- Il file deve essere aggiunto al pacchetto della soluzione.

- Il file non può trovarsi in un altro progetto.

  Se si vuole fare riferimento a file che non soddisfano questi criteri, è necessario immettere manualmente il percorso del file.

  Espandere il nodo del **Server** per scegliere i file che si trovano nel server locale in cui è in esecuzione SharePoint. Per apparire come selezionabile nella finestra di dialogo, questi file devono soddisfare i criteri seguenti:

- Il file deve trovarsi in una delle cartelle mappate seguenti: **Immagini**, **layout** o **ControlTemplate**.

- Il file non può trovarsi nel database del contenuto di SharePoint.

  Se si vuole fare riferimento a file che non soddisfano questi criteri, è necessario immettere manualmente il percorso del file.

  **Contenuto della cartella** Visualizza un elenco di file nella cartella selezionata. Scegliere un file, quindi scegliere il pulsante **OK** per chiudere la finestra di dialogo e inviare la selezione al processo che lo ha chiamato.

  **Tipi di file** Consente di scegliere da un elenco di file appropriati per l'attività che si sta eseguendo.

## <a name="see-also"></a>Vedi anche
- [Creazione di pagine applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)
- [Creazione di Web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Creazione di controlli riutilizzabili per Web part o pagine applicazione](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
