---
title: "Procedura: Specificare l'icona di un'applicazione (Visual Basic, C#)"
description: Informazioni su come usare la proprietà Icon per specificare l'icona visualizzata Esplora file e la barra Windows barra delle applicazioni per l'applicazione compilata.
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
ms.technology: vs-ide-general
ms.workload:
- dotnet
ms.openlocfilehash: 0f986be76b22e89d6038e9331da0f2892b866a4425e8324d6f3da963add6ca7c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121357856"
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Procedura: Specificare l'icona di un'applicazione (Visual Basic, C#)

La proprietà `Icon` per un progetto specifica il file icona (*.ico*) che verrà visualizzato per l'applicazione compilata in **Esplora file** e nella barra delle applicazioni di Windows.

È possibile accedere alla proprietà `Icon` nel riquadro **Applicazione** di **Creazione progetti**. Contiene un elenco delle icone aggiunte a un progetto come risorse o come file di contenuto.

> [!NOTE]
> Dopo aver impostato la proprietà dell'icona per un'applicazione, è anche possibile impostare la proprietà `Icon` di ogni **Finestra** o **Modulo** nell'applicazione. Per informazioni sulle icone della finestra per applicazioni autonome WPF (Windows Presentation Foundation), vedere la proprietà <xref:System.Windows.Window.Icon%2A>.

## <a name="to-specify-an-application-icon"></a>Per specificare l'icona di un'applicazione

1. In **Esplora soluzioni** scegliere un nodo progetto, non il nodo **Soluzione**.

1. Sulla barra dei menu scegliere **Project**  >  **proprietà**.

1. Quando si apre **Creazione progetti**, scegliere la scheda **Applicazione**.

1. **(Visual Basic)** &mdash; **Nell'elenco** Icona scegliere un file di icona (*con estensione ico).*

    **C#** &mdash; Accanto **all'elenco** Icona scegliere il pulsante e quindi passare al percorso del **\<Browse...>** file dell'icona desiderato.

## <a name="see-also"></a>Vedi anche

- [Pagina Applicazione, Project Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [Pagina Applicazione, Project Designer (C#)](../ide/reference/application-page-project-designer-csharp.md)
