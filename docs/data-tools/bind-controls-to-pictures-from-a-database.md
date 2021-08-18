---
title: Associare controlli alle immagini di un database
description: Usare la finestra Origini dati per associare un'immagine in un database a un controllo nell'applicazione Visual Studio dati.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: f1f1db5a2d98b6e55b0da97e7550bc33698ff072
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122154953"
---
# <a name="bind-controls-to-pictures-from-a-database"></a>Associare controlli alle immagini di un database

È possibile usare la **finestra Origini dati** per associare un'immagine in un database a un controllo nell'applicazione. Ad esempio, è possibile associare un'immagine a un controllo in un'applicazione WPF o a un <xref:System.Windows.Controls.Image> controllo in un'applicazione Windows <xref:System.Windows.Forms.PictureBox> Form.

Le immagini in un database vengono in genere archiviate come matrici di byte. Gli elementi  nella finestra Origini dati archiviati come matrici di byte hanno il tipo di controllo impostato su Nessuno per impostazione predefinita, perché le matrici di byte possono contenere qualsiasi elemento, da una semplice matrice di byte al file **eseguibile** di un'applicazione di grandi dimensioni. Per creare un controllo associato a dati  per un elemento della matrice di byte nella finestra Origini dati che rappresenta un'immagine, è necessario selezionare il controllo da creare.

La procedura seguente presuppone che la **finestra Origini** dati sia già popolata con un elemento associato all'immagine.

## <a name="to-bind-a-picture-in-a-database-to-a-control"></a>Per associare un'immagine di un database a un controllo

1. Assicurarsi che l'area di progettazione a cui si vuole aggiungere il controllo sia aperta in Wpf Designer o in Progettazione Windows Form.

2. Nella finestra **Origini dati** espandere la tabella o l'oggetto desiderato per visualizzarne le colonne o le proprietà.

   > [!TIP]
   > Se la **finestra Origini** dati non è aperta, aprirla selezionando Visualizza Windows  >    >  **origini dati**.

3. Selezionare la colonna o la proprietà che contiene i dati dell'immagine e selezionare uno dei controlli seguenti nell'elenco a discesa:

    - Se la finestra di progettazione WPF è aperta, selezionare **Immagine**.

    - Se la finestra Windows Forms è aperta, selezionare **PictureBox**.

    - In alternativa, è possibile selezionare un controllo diverso che supporta data binding e che può visualizzare le immagini. Se il controllo da usare non è presente nell'elenco dei controlli disponibili, è possibile aggiungerlo all'elenco e quindi selezionarlo. Per altre informazioni, vedere [Aggiungere controlli personalizzati alla finestra Origini dati](../data-tools/add-custom-controls-to-the-data-sources-window.md).

## <a name="see-also"></a>Vedi anche

- [Associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
