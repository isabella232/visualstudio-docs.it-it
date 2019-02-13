---
title: "Procedura: Specificare l'icona di un'applicazione (Visual Basic, C#)"
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f2903821c0e0843de43f68d67cc64c344ab95e02
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55924573"
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Procedura: Specificare l'icona di un'applicazione (Visual Basic, C#)

La proprietà `Icon` per un progetto specifica il file icona (*.ico*) che verrà visualizzato per l'applicazione compilata in **Esplora file** e nella barra delle applicazioni di Windows.

È possibile accedere alla proprietà `Icon` nel riquadro **Applicazione** di **Creazione progetti**. Contiene un elenco delle icone aggiunte a un progetto come risorse o come file di contenuto.

> [!NOTE]
> Dopo aver impostato la proprietà dell'icona per un'applicazione, è anche possibile impostare la proprietà `Icon` di ogni **Finestra** o **Modulo** nell'applicazione. Per informazioni sulle icone della finestra per applicazioni autonome WPF (Windows Presentation Foundation), vedere la proprietà <xref:System.Windows.Window.Icon%2A>.

## <a name="to-specify-an-application-icon"></a>Per specificare l'icona di un'applicazione

1. In **Esplora soluzioni** scegliere un nodo progetto, non il nodo **Soluzione**.

1. Sulla barra dei menu scegliere **Progetto** > **Proprietà**.

1. Quando si apre **Creazione progetti**, scegliere la scheda **Applicazione**.

1. **(Visual Basic)**&mdash;Nell'elenco **Icona** scegliere un file icona (*.ico*).

    **C#**&mdash;Accanto all'elenco **Icona** scegliere il pulsante **\<Sfoglia>** e quindi selezionare il percorso del file icona desiderato.

## <a name="see-also"></a>Vedere anche

- [Pagina Applicazione, Creazione progetti (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [Applicazione (pagina), Creazione progetti (C#)](../ide/reference/application-page-project-designer-csharp.md)