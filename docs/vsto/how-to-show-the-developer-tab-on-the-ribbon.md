---
title: 'Procedura: Mostra la scheda Developer sulla barra multifunzione'
ms.date: 08/14/2019
ms.topic: conceptual
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
ms.openlocfilehash: 7b6641cca4ef2288452b2f6959482b311a5b07a4
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551783"
---
# <a name="how-to-show-the-developer-tab-on-the-ribbon"></a>Procedura: Mostra la scheda Developer sulla barra multifunzione
  Per accedere alla scheda **Developer** sulla barra multifunzione di un'applicazione di Office, è necessario configurarla in modo da visualizzare la scheda perché non è visualizzata per impostazione predefinita. Ad esempio, è necessario visualizzare tale scheda per aggiungere un oggetto <xref:Microsoft.Office.Tools.Word.GroupContentControl> a una personalizzazione a livello di documento per Word.

> [!NOTE]
> Questo materiale sussidiario si applica solo alle applicazioni di Office 2010 o versioni successive. Se si vuole visualizzare questa scheda nel sistema di Microsoft Office 2007, vedere la seguente versione di questo argomento [procedura: Mostra la scheda Developer sulla barra multifunzione](https://web.archive.org/web/20140303033431/msdn.microsoft.com/library/bb608625(v=vs.90).aspx
).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

> [!NOTE]
> L'accesso non dispone di una scheda per **sviluppatori** .

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="to-show-the-developer-tab"></a>Per visualizzare la scheda Sviluppo

1. Avviare un'applicazione Office supportata da questo argomento. Vedere la Nota **si applica a:** riportata in precedenza in questo argomento.

2. Nella scheda **file** scegliere il pulsante **Opzioni** .

     La figura seguente mostra la scheda **file** e il pulsante **opzioni** in Office 2010.

     ![Scelta di file, opzioni in Outlook 2010](../vsto/media/vsto-office-file-tab.png "Scelta di file, opzioni in Outlook 2010")

     La figura seguente mostra la scheda **file** in Office 2013.

     ![Scheda file in Outlook 2013](../vsto/media/vsto-office2013-filetab.png "Scheda file in Outlook 2013")

     Nella figura seguente viene illustrato il pulsante **Opzioni** in Office 2013.

     ![Pulsante Opzioni in Outlook 2013 Preview](../vsto/media/vsto-office2013-optionsbutton.png "Pulsante Opzioni in Outlook 2013 Preview")

3. Nella finestra di dialogo**Opzioni** di _ApplicationName_scegliere il pulsante **Personalizza barra multifunzione** .

     Nella figura seguente sono illustrate la finestra di dialogo **Opzioni** e il pulsante **Personalizza barra multifunzione** in Excel 2010. La posizione di questo pulsante è simile in tutte le altre applicazioni elencate nella sezione "Applica a" quasi all'inizio di questo argomento.

     ![Pulsante Personalizza barra multifunzione](../vsto/media/vsto-office2010-customizeribbonbutton.png "Pulsante Personalizza barra multifunzione")

4. Nell'elenco delle schede principali selezionare la casella di controllo **Developer** .

     Nella figura seguente viene illustrata la casella di controllo **Developer** in [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)]Word 2010 e. La posizione di questa casella di controllo è simile in tutte le altre applicazioni elencate nella sezione "Si applica a" quasi all'inizio di questo argomento.

     ![Casella di controllo sviluppatore nella finestra di dialogo Opzioni di Word](../vsto/media/vsto-office2010-developercheckbox.png "Casella di controllo sviluppatore nella finestra di dialogo Opzioni di Word")

5. Scegliere il pulsante **OK** per chiudere la finestra di dialogo **Opzioni** .

## <a name="see-also"></a>Vedere anche
- [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md)
