---
title: Associare controlli alle immagini di un database
description: Usare la finestra Origini dati per associare un'immagine in un database a un controllo nell Visual Studio app Visual Studio dati.
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
ms.openlocfilehash: e472eeeb961096a5e1cbeb01323121dc77353bc29ef33a8ab06f5c9e3f09a625
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121240666"
---
# <a name="bind-controls-to-pictures-from-a-database"></a>Associare controlli alle immagini di un database

È possibile usare la **finestra Origini dati** per associare un'immagine di un database a un controllo nell'applicazione. Ad esempio, è possibile associare un'immagine a un controllo in un'applicazione WPF o a un <xref:System.Windows.Controls.Image> controllo in un'applicazione Windows <xref:System.Windows.Forms.PictureBox> Form.

Le immagini in un database vengono in genere archiviate come matrici di byte. Il tipo  di controllo degli elementi nella finestra Origini dati archiviati come matrici di byte è impostato su Nessuno per impostazione predefinita, perché le matrici di byte possono contenere qualsiasi elemento, da una semplice matrice di byte al file **eseguibile** di un'applicazione di grandi dimensioni. Per creare un controllo associato a dati  per un elemento della matrice di byte nella finestra Origini dati che rappresenta un'immagine, è necessario selezionare il controllo da creare.

Nella procedura seguente si presuppone che **la finestra Origini** dati sia già popolata con un elemento associato all'immagine.

## <a name="to-bind-a-picture-in-a-database-to-a-control"></a>Per associare un'immagine di un database a un controllo

1. Assicurarsi che l'area di progettazione a cui si vuole aggiungere il controllo sia aperta in WPF Designer o Windows Form.

2. Nella finestra **Origini dati** espandere la tabella o l'oggetto desiderato per visualizzarne le colonne o le proprietà.

   > [!TIP]
   > Se la **finestra Origini** dati non è aperta, aprirla selezionando Visualizza altre Windows  >    >  **dati**.

3. Selezionare la colonna o la proprietà che contiene i dati dell'immagine e selezionare uno dei controlli seguenti nell'elenco a discesa:

    - Se WPF Designer è aperto, selezionare **Immagine.**

    - Se la finestra Windows Forms è aperta, selezionare **PictureBox.**

    - In alternativa, è possibile selezionare un controllo diverso che supporta data binding e che può visualizzare le immagini. Se il controllo che si vuole usare non è presente nell'elenco dei controlli disponibili, è possibile aggiungerlo all'elenco e quindi selezionarlo. Per altre informazioni, vedere [Aggiungere controlli personalizzati alla finestra Origini dati](../data-tools/add-custom-controls-to-the-data-sources-window.md).

## <a name="see-also"></a>Vedi anche

- [Associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
