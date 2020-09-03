---
title: "Procedura: Specificare l'icona di un'applicazione (Visual Basic, C#) | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
ms.assetid: ad8e14ed-adc2-45b6-a0be-818b16d5616f
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 136fd00bea736af0f0c589c28eae597ff8fd558e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670695"
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Procedura: specificare l'icona di un'applicazione (Visual Basic, C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La proprietà `Icon` per un progetto specifica il file icona (.ico) che verrà visualizzato per l'applicazione compilata in Esplora file e nella barra delle applicazioni di Windows.

 È possibile accedere alla proprietà `Icon` nel riquadro **Applicazione** di **Creazione progetti**. Contiene un elenco delle icone aggiunte a un progetto come risorse o come file di contenuto.

> [!NOTE]
> Dopo aver impostato la proprietà dell'icona per un'applicazione, è anche possibile impostare la proprietà `Icon` di ogni **Finestra** o **Modulo** nell'applicazione. Per informazioni sulle icone della finestra per applicazioni autonome WPF (Windows Presentation Foundation), vedere la proprietà <xref:System.Windows.Window.Icon%2A>.

### <a name="to-specify-an-application-icon"></a>Per specificare l'icona di un'applicazione

1. In **Esplora soluzioni** scegliere un nodo progetto, non il nodo **Soluzione**.

2. Sulla barra dei menu scegliere **progetto**, **Proprietà**.

3. Quando si apre **Creazione progetti**, scegliere la scheda **Applicazione**.

4. **(Visual Basic)** Nell'elenco **Icona** scegliere un file icona con estensione ico.

     **C#** Accanto all'elenco **icona** scegliere il **\<Browse...>** pulsante, quindi selezionare il percorso del file icona desiderato.

## <a name="see-also"></a>Vedere anche
 Pagina [applicazione, Progettazione progetti (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md) [pagina applicazione, Progettazione progetti (C#)](../ide/reference/application-page-project-designer-csharp.md) [gestione delle proprietà dell'applicazione](../ide/application-properties.md) [procedura: aggiungere o rimuovere risorse](https://msdn.microsoft.com/7b77bc06-3952-4799-b029-def3f8f7f88d)
