---
title: "Procedura: Specificare l'icona di un'applicazione (Visual Basic, C#)"
description: Informazioni su come usare la proprietà Icon per specificare l'icona visualizzata Esplora file la barra Windows barra delle applicazioni per l'applicazione compilata.
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
ms.openlocfilehash: 0c03ae786a3fd748177a776b6f2bc2a2e67cb802
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122109162"
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Procedura: Specificare l'icona di un'applicazione (Visual Basic, C#)

La proprietà `Icon` per un progetto specifica il file icona (*.ico*) che verrà visualizzato per l'applicazione compilata in **Esplora file** e nella barra delle applicazioni di Windows.

È possibile accedere alla proprietà `Icon` nel riquadro **Applicazione** di **Creazione progetti**. Contiene un elenco delle icone aggiunte a un progetto come risorse o come file di contenuto.

> [!NOTE]
> Dopo aver impostato la proprietà dell'icona per un'applicazione, è anche possibile impostare la proprietà `Icon` di ogni **Finestra** o **Modulo** nell'applicazione. Per informazioni sulle icone della finestra per applicazioni autonome WPF (Windows Presentation Foundation), vedere la proprietà <xref:System.Windows.Window.Icon%2A>.

## <a name="to-specify-an-application-icon"></a>Per specificare l'icona di un'applicazione

1. In **Esplora soluzioni** scegliere un nodo progetto, non il nodo **Soluzione**.

1. Nella barra dei menu scegliere **Project**  >  **proprietà**.

1. Quando si apre **Creazione progetti**, scegliere la scheda **Applicazione**.

1. **(Visual Basic)** &mdash; **Nell'elenco** Icona scegliere un file di icona *(con estensione ico).*

    **C#** &mdash; Accanto **all'elenco** Icona scegliere il pulsante e quindi passare al **\<Browse...>** percorso del file dell'icona desiderato.

## <a name="see-also"></a>Vedi anche

- [Pagina Applicazione, progettazione Project (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [Pagina Applicazione, progettazione Project (C#)](../ide/reference/application-page-project-designer-csharp.md)
