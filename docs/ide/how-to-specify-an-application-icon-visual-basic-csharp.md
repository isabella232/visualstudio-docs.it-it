---
title: "Procedura: Specificare l'icona di un'applicazione (Visual Basic, C#)"
description: Informazioni su come usare la proprietà Icon per specificare l'icona visualizzata in Esplora file e nella barra delle applicazioni di Windows per l'applicazione compilata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 77be1eefb4ea4da139bb536e9d838afecddd7202
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869297"
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Procedura: Specificare l'icona di un'applicazione (Visual Basic, C#)

La proprietà `Icon` per un progetto specifica il file icona (*.ico*) che verrà visualizzato per l'applicazione compilata in **Esplora file** e nella barra delle applicazioni di Windows.

È possibile accedere alla proprietà `Icon` nel riquadro **Applicazione** di **Creazione progetti**. Contiene un elenco delle icone aggiunte a un progetto come risorse o come file di contenuto.

> [!NOTE]
> Dopo aver impostato la proprietà dell'icona per un'applicazione, è anche possibile impostare la proprietà `Icon` di ogni **Finestra** o **Modulo** nell'applicazione. Per informazioni sulle icone della finestra per applicazioni autonome WPF (Windows Presentation Foundation), vedere la proprietà <xref:System.Windows.Window.Icon%2A>.

## <a name="to-specify-an-application-icon"></a>Per specificare l'icona di un'applicazione

1. In **Esplora soluzioni** scegliere un nodo progetto, non il nodo **Soluzione**.

1. Sulla barra dei menu scegliere proprietà **progetto**  >  .

1. Quando si apre **Creazione progetti**, scegliere la scheda **Applicazione**.

1. **(Visual Basic)** &mdash; Nell'elenco **icona** scegliere un file icona (*. ico*).

    **C#** &mdash; Accanto all'elenco **icona** scegliere il **\<Browse...>** pulsante, quindi selezionare il percorso del file icona desiderato.

## <a name="see-also"></a>Vedi anche

- [Pagina applicazione, Progettazione progetti (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [Pagina applicazione, Progettazione progetti (C#)](../ide/reference/application-page-project-designer-csharp.md)
