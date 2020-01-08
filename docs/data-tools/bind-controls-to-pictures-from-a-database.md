---
title: Associare controlli alle immagini di un database
ms.date: 11/04/2016
ms.topic: conceptual
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: a4155a246516bef074a56e5644712912b2ce5af6
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587004"
---
# <a name="bind-controls-to-pictures-from-a-database"></a>Associare controlli alle immagini di un database

È possibile utilizzare la finestra **origini dati** per associare un'immagine di un database a un controllo nell'applicazione. Ad esempio, è possibile associare un'immagine a un controllo <xref:System.Windows.Controls.Image> in un'applicazione WPF o a un controllo <xref:System.Windows.Forms.PictureBox> in un Windows Forms Application.

Le immagini in un database vengono in genere archiviate come matrici di byte. Per impostazione predefinita, gli elementi della finestra **origini dati** archiviati come matrici di byte hanno il tipo di controllo impostato su **None** , perché le matrici di byte possono contenere qualsiasi elemento di una semplice matrice di byte nel file eseguibile di un'applicazione di grandi dimensioni. Per creare un controllo con associazione a dati per un elemento della matrice di byte nella finestra **origini dati** che rappresenta un'immagine, è necessario selezionare il controllo da creare.

Nella procedura seguente si presuppone che la finestra **origini dati** sia già popolata con un elemento associato all'immagine.

## <a name="to-bind-a-picture-in-a-database-to-a-control"></a>Per associare un'immagine di un database a un controllo

1. Assicurarsi che l'area di progettazione a cui si desidera aggiungere il controllo sia aperta in WPF Designer o nella Progettazione Windows Form.

2. Nella finestra **origini dati** espandere la tabella o l'oggetto desiderato per visualizzare le relative colonne o proprietà.

   > [!TIP]
   > Se la finestra **origini dati** non è aperta, aprirla selezionando **Visualizza** > **altre** **origini dati** > di Windows.

3. Selezionare la colonna o la proprietà che contiene i dati dell'immagine e selezionare uno dei controlli seguenti dall'elenco di controllo a discesa:

    - Se Progettazione WPF è aperto, selezionare **immagine**.

    - Se la finestra di progettazione Windows Forms è aperta, selezionare **PictureBox**.

    - In alternativa, è possibile selezionare un controllo diverso che supporti data binding e che possa visualizzare immagini. Se il controllo che si desidera utilizzare non è presente nell'elenco dei controlli disponibili, è possibile aggiungerlo all'elenco e quindi selezionarlo. Per altre informazioni, vedere [aggiungere controlli personalizzati alla finestra Origini dati](../data-tools/add-custom-controls-to-the-data-sources-window.md).

## <a name="see-also"></a>Vedere anche

- [Associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
