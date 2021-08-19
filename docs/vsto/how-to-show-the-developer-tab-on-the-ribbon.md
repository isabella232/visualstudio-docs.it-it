---
title: 'Procedura: Visualizzare la scheda Sviluppatore sulla barra multifunzione'
description: Informazioni su come usare Visual Studio per visualizzare a livello di codice la scheda Sviluppo sulla barra multifunzione in un Microsoft Word documento.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- Developer tab [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 382f9f62367734785c997989fb96ccf6414e9360
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122083028"
---
# <a name="how-to-show-the-developer-tab-on-the-ribbon"></a>Procedura: Visualizzare la scheda Sviluppatore sulla barra multifunzione
  Per accedere alla **scheda Sviluppatore** sulla barra multifunzione di un'applicazione Office, è necessario configurarla per visualizzare tale scheda perché non viene visualizzata per impostazione predefinita. Ad esempio, è necessario visualizzare tale scheda per aggiungere un oggetto <xref:Microsoft.Office.Tools.Word.GroupContentControl> a una personalizzazione a livello di documento per Word.

> [!NOTE]
> Questo materiale sussidiario si applica solo alle applicazioni di Office 2010 o versioni successive. Per visualizzare questa scheda nel sistema Microsoft Office 2007, vedere la versione seguente di questo argomento [Procedura:](https://web.archive.org/web/20140303033431/msdn.microsoft.com/library/bb608625(v=vs.90).aspx
)Visualizzare la scheda Sviluppatore sulla barra multifunzione .

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

> [!NOTE]
> Access non ha una **scheda Sviluppatore.**

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="to-show-the-developer-tab"></a>Per visualizzare la scheda Sviluppo

1. Avviare un'applicazione Office supportata da questo argomento. Vedere la **nota Si applica a:** più indietro in questo argomento.

2. Nella scheda **File** scegliere il **pulsante** Opzioni.

     La figura seguente mostra la **scheda File** e **il pulsante** Opzioni in Office 2010.

     ![Scelta di file, opzioni di Outlook 2010](../vsto/media/vsto-office-file-tab.png "Scelta di file, opzioni di Outlook 2010")

     La figura seguente illustra la **scheda File** in Office 2013.

     ![Scheda File in Outlook 2013](../vsto/media/vsto-office2013-filetab.png "Scheda File in Outlook 2013")

     La figura seguente mostra il **pulsante** Opzioni in Office 2013.

     ![Pulsante Opzioni di Outlook 2013 Preview](../vsto/media/vsto-office2013-optionsbutton.png "Pulsante Opzioni di Outlook 2013 Preview")

3. Nella finestra _di dialogo Opzioni_**Nome** Applicazione scegliere il pulsante **Personalizza barra** multifunzione.

     La figura seguente illustra la **finestra di** dialogo Opzioni e il **pulsante** Personalizza barra multifunzione in Excel 2010. La posizione di questo pulsante è simile in tutte le altre applicazioni elencate nella sezione "Applica a" quasi all'inizio di questo argomento.

     ![Pulsante Personalizzazione barra multifunzione](../vsto/media/vsto-office2010-customizeribbonbutton.png "Pulsante Personalizzazione barra multifunzione")

4. Nell'elenco delle schede principali selezionare la **casella di controllo** Sviluppatore.

     La figura seguente illustra la **casella di** controllo Sviluppatore in Word 2010 e [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] . La posizione di questa casella di controllo è simile in tutte le altre applicazioni elencate nella sezione "Si applica a" quasi all'inizio di questo argomento.

     ![Casella di controllo Sviluppatore nella finestra di dialogo Opzioni di Word](../vsto/media/vsto-office2010-developercheckbox.png "Casella di controllo Sviluppatore nella finestra di dialogo Opzioni di Word")

5. Fare clic **sul pulsante OK** per chiudere la finestra di **dialogo** Opzioni.

## <a name="see-also"></a>Vedi anche
- [Office Personalizzazione dell'interfaccia utente](../vsto/office-ui-customization.md)
