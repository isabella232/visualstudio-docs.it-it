---
title: Associare controlli alle immagini da un database | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- images [Visual Basic], displaying on Windows Forms
- data binding [Windows Forms], pictures
- images [Visual Basic], data binding
- pictures, data binding
- pictures, dragging from Data Sources window
- Data Sources Window, setting controls to display images
- PictureBox control [Windows Forms], data binding
- images [Visual Basic], dragging from Data Sources window
ms.assetid: 9748815e-3556-49e8-86b1-c6aa593c6163
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ab997b01c0155b48cb9dd3033e5bbfd4724d7ba6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47530235"
---
# <a name="bind-controls-to-pictures-from-a-database"></a>Associare controlli alle immagini di un database
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [associare controlli alle immagini da un database](https://docs.microsoft.com/visualstudio/data-tools/bind-controls-to-pictures-from-a-database).  
  
  
È possibile usare la **Zdroje dat** finestra per associare un'immagine in un database a un controllo nell'applicazione. Ad esempio, è possibile associare un'immagine da un <xref:System.Windows.Controls.Image> controllo in un'applicazione WPF o a un <xref:System.Windows.Forms.PictureBox> controllo in un'applicazione Windows Form.  
  
 Le immagini in un database sono in genere archiviate come matrici di byte. Gli elementi nel **Zdroje dat** finestra in cui vengono archiviati come matrici di byte avere il controllo tipo impostato su **None** per impostazione predefinita, poiché le matrici di byte possono contenere qualsiasi elemento da una semplice matrice di byte del file eseguibile un'applicazione di grandi dimensioni. Per creare un controllo con associazione a dati per un elemento di matrice di byte nel **Zdroje dat** finestra che rappresenta un'immagine, è necessario selezionare il controllo da creare.  
  
 La procedura seguente si presuppone che il **Zdroje dat** finestra sia già popolata con un elemento che è associato all'immagine. Per altre informazioni, vedere [procedura: connettersi ai dati in un Database](../data-tools/how-to-connect-to-data-in-a-database.md).  
  
### <a name="to-bind-a-picture-in-a-database-to-a-control"></a>Per associare un'immagine in un database a un controllo  
  
1.  Assicurarsi che l'area di progettazione che si desidera aggiungere il controllo viene aperto in WPF Designer o in Progettazione Windows Form.  
  
2.  Nel **Zdroje dat** finestra, espandere la tabella desiderata o per visualizzare le colonne o proprietà dell'oggetto.  
  
3.  Selezionare la colonna o proprietà che contiene i dati di immagine e selezionare uno dei seguenti controlli dal relativo elenco di controllo elenco a discesa:  
  
    -   Se la finestra di progettazione WPF è aperto, selezionare **immagine**.  
  
    -   Se la finestra di progettazione Windows Form è aperto, selezionare **PictureBox**.  
  
    -   In alternativa, è possibile selezionare un altro controllo che supporta il data binding e in grado di visualizzare immagini. Se il controllo che si desidera utilizzare non è presente nell'elenco dei controlli disponibili, è possibile aggiungerlo all'elenco e quindi selezionarlo. Per altre informazioni, vedere [aggiungere controlli personalizzati alla finestra Origini dei dati](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)

