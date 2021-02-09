---
title: Tastiera di Office Excel, impostazioni, finestra di dialogo Opzioni
description: Informazioni su come è possibile fare in modo che i comandi dei tasti di scelta rapida di Microsoft Excel ricevano lo stato attivo del documento selezionando lo schema della tastiera
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 914b86e6e2b27d18e2089d44ce97810f82294c5e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880346"
---
# <a name="microsoft-office-excel-keyboard-settings-options-dialog-box"></a>Tastiera Microsoft Office Excel, impostazioni, finestra di dialogo Opzioni
  Microsoft Office Excel e Visual Studio gestiscono entrambi i tasti di scelta rapida. La stessa combinazione di tasti di scelta rapida può essere conforme a comandi diversi in Excel e in Visual Studio. Quando Excel è aperto in un progetto a livello di documento in Visual Studio, solo un'applicazione alla volta riceve i comandi del tasto di scelta rapida. Per impostazione predefinita, Visual Studio riceve tutti i comandi dei tasti di scelta rapida, ma è possibile fare in modo che vengano ricevuti da Excel quando il documento ha lo stato attivo selezionando lo **schema della tastiera dinamica**

 Se si usa un tasto di scelta rapida che non è assegnato a un comando nell'applicazione che sta attualmente gestendo i tasti di scelta rapida, il tasto di scelta rapida viene passato all'altra applicazione.

 L'opzione selezionata rimarrà attiva per i progetti di Excel fino a quando non viene modificata. La selezione non influisce sui progetti Microsoft Office Word; è necessario apportare qualsiasi modifica per Word usando le opzioni di tastiera Microsoft Office Word.

## <a name="uielement-list"></a>Elenco degli elementi di interfaccia
 **Schema della tastiera di Visual Studio** Visual Studio riceve tutti i comandi del tasto di scelta rapida, anche se Excel ha lo stato attivo. Ad esempio, se si preme il tasto funzione **F5** mentre Excel ha lo stato attivo, Visual Studio avvia il debug della soluzione.

 **Schema della tastiera dinamica** Visual Studio riceve i comandi del tasto di scelta rapida solo quando ha lo stato attivo. Quando Excel ha lo stato attivo, Excel riceve tutti i comandi del tasto di scelta rapida. Se ad esempio si preme il tasto funzione **F5** mentre Excel ha lo stato attivo, verrà visualizzata la finestra **di dialogo Vai a** . Se si preme **F5** mentre Visual Studio ha lo stato attivo, Visual Studio avvia il debug della soluzione.

## <a name="see-also"></a>Vedi anche
- [Tastiera Microsoft Office Word, impostazioni della tastiera Microsoft Office, finestra di dialogo Opzioni](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)
