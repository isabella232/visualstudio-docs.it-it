---
title: 'Procedura: visualizzare la scheda Developer sulla barra multifunzione'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 41070c92d0c27c1ee8fbf480f7461c22421b8fdc
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545847"
---
# <a name="how-to-show-the-developer-tab-on-the-ribbon"></a>Procedura: visualizzare la scheda Developer sulla barra multifunzione
  Per accedere alla scheda **Developer** sulla barra multifunzione di un'applicazione di Office, è necessario configurarla in modo da visualizzare la scheda perché non è visualizzata per impostazione predefinita. Ad esempio, è necessario visualizzare tale scheda per aggiungere un oggetto <xref:Microsoft.Office.Tools.Word.GroupContentControl> a una personalizzazione a livello di documento per Word.

> [!NOTE]
> Questo materiale sussidiario si applica solo alle applicazioni di Office 2010 o versioni successive. Se si vuole visualizzare questa scheda nel sistema di Microsoft Office 2007, vedere la seguente versione di questo argomento [procedura: visualizzare la scheda Developer sulla barra multifunzione](https://web.archive.org/web/20140303033431/msdn.microsoft.com/library/bb608625(v=vs.90).aspx
).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

> [!NOTE]
> L'accesso non dispone di una scheda per **sviluppatori** .

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="to-show-the-developer-tab"></a>Per visualizzare la scheda Sviluppo

1. Avviare un'applicazione Office supportata da questo argomento. Vedere la Nota **si applica a:** riportata in precedenza in questo argomento.

2. Nella scheda **file** scegliere il pulsante **Opzioni** .

     La figura seguente mostra la scheda **file** e il pulsante **opzioni** in Office 2010.

     ![Scelta di file, opzioni di Outlook 2010](../vsto/media/vsto-office-file-tab.png "Scelta di file, opzioni di Outlook 2010")

     La figura seguente mostra la scheda **file** in Office 2013.

     ![Scheda File in Outlook 2013](../vsto/media/vsto-office2013-filetab.png "Scheda File in Outlook 2013")

     Nella figura seguente viene illustrato il pulsante **Opzioni** in Office 2013.

     ![Pulsante Opzioni di Outlook 2013 Preview](../vsto/media/vsto-office2013-optionsbutton.png "Pulsante Opzioni di Outlook 2013 Preview")

3. Nella finestra di dialogo**Opzioni** di _ApplicationName_scegliere il pulsante **Personalizza barra multifunzione** .

     Nella figura seguente sono illustrate la finestra di dialogo **Opzioni** e il pulsante **Personalizza barra multifunzione** in Excel 2010. La posizione di questo pulsante è simile in tutte le altre applicazioni elencate nella sezione "Applica a" quasi all'inizio di questo argomento.

     ![Pulsante Personalizzazione barra multifunzione](../vsto/media/vsto-office2010-customizeribbonbutton.png "Pulsante Personalizzazione barra multifunzione")

4. Nell'elenco delle schede principali selezionare la casella di controllo **Developer** .

     Nella figura seguente viene illustrata la casella di controllo **Developer** in Word 2010 e [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] . La posizione di questa casella di controllo è simile in tutte le altre applicazioni elencate nella sezione "Si applica a" quasi all'inizio di questo argomento.

     ![Casella di controllo Sviluppatore nella finestra di dialogo Opzioni di Word](../vsto/media/vsto-office2010-developercheckbox.png "Casella di controllo Sviluppatore nella finestra di dialogo Opzioni di Word")

5. Scegliere il pulsante **OK** per chiudere la finestra di dialogo **Opzioni** .

## <a name="see-also"></a>Vedere anche
- [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md)
