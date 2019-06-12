---
title: Tastiera di Office Excel, impostazioni della tastiera, finestra di dialogo Opzioni
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ExcelOptions.KeyboardMappingScheme
- VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Excel_Keyboard
- VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Excel.Keyboard
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- keyboard shortcuts, Office development in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 090e943df2b61352c2342218c3c71c8f0e60eaad
ms.sourcegitcommit: cc5fd59e5dc99181601b7db8b28d7f8a83a36bab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2019
ms.locfileid: "66836041"
---
# <a name="microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box"></a>Finestra di dialogo Opzioni di tastiera di Microsoft Office Excel, impostazioni tastiera Microsoft Office,
  Sia Microsoft Office Excel e Visual Studio consentono di gestire i tasti di scelta rapida. La stessa combinazione di tasti di scelta rapida possa attivare comandi diversi, in Excel e in Visual Studio. Quando Excel è aperto in un progetto a livello di documento in Visual Studio, solo un'applicazione in un momento riceve i comandi dei tasti di scelta rapida. Per impostazione predefinita, Visual Studio riceve tutti i comandi dei tasti di scelta rapida, ma è possibile rendere Excel riceverli quando il documento dispone dello stato attivo selezionando **schema della tastiera dinamico**.

 Se si usa un tasto di scelta rapida che non è assegnato a un comando nell'applicazione che sta gestendo i tasti di scelta rapida, il tasto di scelta rapida viene passato a altra applicazione.

 L'opzione selezionata rimarranno in vigore per i progetti di Excel fino alla successiva modifica. La selezione non influenza i progetti di Microsoft Office Word. è necessario apportare qualsiasi modifica di Word usando le opzioni della tastiera di Microsoft Office Word.

## <a name="uielement-list"></a>Elenco UIElement
 **Lo schema della tastiera di Visual Studio** Visual Studio riceve tutti i comandi dei tasti di scelta rapida, anche se Excel ha lo stato attivo. Ad esempio, se si preme il tasto funzione **F5** mentre Excel ha lo stato attivo, Visual Studio avvia il debug della soluzione.

 **Schema della tastiera dinamico** Visual Studio riceve comandi dei tasti di scelta rapida solo quando lo stato attivo. Quando Excel ha lo stato attivo, il programma riceve tutti i comandi dei tasti di scelta rapida. Ad esempio, se si preme il tasto funzione **F5** anche se Excel ha lo stato attivo, in Excel viene aperto il **Vai a** nella finestra di dialogo. Se si preme **F5** mentre Visual Studio ha lo stato attivo, Visual Studio avvia il debug della soluzione.

## <a name="see-also"></a>Vedere anche
- [Finestra di dialogo Opzioni di tastiera di Microsoft Office Word, impostazioni tastiera Microsoft Office,](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)
