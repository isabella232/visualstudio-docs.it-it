---
title: Office Excel tastiera, Impostazioni, finestra di dialogo Opzioni
description: Informazioni su come fare in modo Microsoft Excel comandi dei tasti di scelta rapida quando il documento ha lo stato attivo selezionando Schema della tastiera dinamico.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: d33811c8b5fc38359e59a1ff2708ba05d2f2f1d5
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710611"
---
# <a name="microsoft-office-excel-keyboard-settings-options-dialog-box"></a>Microsoft Office Excel tastiera, Impostazioni, finestra di dialogo Opzioni
  Microsoft Office Excel e Visual Studio entrambi gestiscono i tasti di scelta rapida. La stessa combinazione di tasti di scelta rapida può contenere comandi diversi Excel e in Visual Studio. Quando Excel è aperto in un progetto a livello di documento in Visual Studio, solo un'applicazione alla volta riceve i comandi dei tasti di scelta rapida. Per impostazione predefinita, Visual Studio tutti i comandi dei tasti di scelta rapida, ma è possibile Excel riceverli quando il documento ha lo stato attivo selezionando Schema della tastiera **dinamico**.

 Se si usa un tasto di scelta rapida non assegnato a un comando nell'applicazione che attualmente gestisce i tasti di scelta rapida, il tasto di scelta rapida viene passato all'altra applicazione.

 L'opzione selezionata rimarrà attiva per i progetti Excel finché non viene modificato. La selezione non influisce sui Microsoft Office di Word. è necessario apportare modifiche a Word usando le opzioni Microsoft Office tastiera di Word.

## <a name="uielement-list"></a>Elenco degli elementi di interfaccia
 **Visual Studio tastiera Visual Studio** tutti i comandi dei tasti di scelta rapida, anche se Excel lo stato attivo. Ad esempio, se si preme il tasto **funzione F5** Excel stato attivo, Visual Studio avvia il debug della soluzione.

 **Lo schema della** tastiera Visual Studio i comandi dei tasti di scelta rapida solo quando ha lo stato attivo. Quando Excel ha lo stato attivo, Excel tutti i comandi dei tasti di scelta rapida. Ad esempio, se si preme il tasto funzione **F5** mentre Excel ha lo stato attivo, Excel apre la **finestra di dialogo** Vai a. Se si preme **F5 mentre** Visual Studio lo stato attivo, Visual Studio avvia il debug della soluzione.

## <a name="see-also"></a>Vedi anche
- [Microsoft Office Tastiera di Word, Microsoft Office tastiera Impostazioni finestra di dialogo Opzioni](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)
