---
title: Tastiera di Office Word, impostazioni della tastiera, finestra di dialogo Opzioni
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Word.Keyboard
- VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Word_Keyboard
- VST.WordOptions.KeyboardMappingScheme
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
ms.openlocfilehash: 5180aa2f4c5022cedcba2c5377d2ff2ac14ffb28
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "66835985"
---
# <a name="microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box"></a>Tastiera Microsoft Office Word, impostazioni della tastiera Microsoft Office, finestra di dialogo Opzioni
  Microsoft Office Word e Visual Studio gestiscono entrambi i tasti di scelta rapida. La stessa combinazione di tasti di scelta rapida può basarsi su comandi diversi in Word e in Visual Studio. Quando Word è aperto in un progetto a livello di documento in Visual Studio, solo un'applicazione alla volta riceve i comandi del tasto di scelta rapida. Per impostazione predefinita, Visual Studio riceve tutti i comandi dei tasti di scelta rapida, ma è possibile fare in modo che vengano ricevuti da Word quando il documento ha lo stato attivo selezionando lo **schema della tastiera dinamica**

 Se si usa un tasto di scelta rapida che non è assegnato a un comando nell'applicazione che sta attualmente gestendo i tasti di scelta rapida, il tasto di scelta rapida viene passato all'altra applicazione.

 L'opzione selezionata rimarrà attiva per i progetti Word finché non viene modificata. La selezione non influisce sui progetti Microsoft Office Excel; è necessario apportare modifiche per Excel usando le opzioni di tastiera Microsoft Office Excel.

## <a name="uielement-list"></a>Elenco degli elementi di interfaccia
 **Schema della tastiera di Visual Studio** Visual Studio riceve tutti i comandi dei tasti di scelta rapida, anche se il documento di Word ha lo stato attivo. Ad esempio, se si preme il tasto funzione **F5** mentre il documento ha lo stato attivo, Visual Studio avvia il debug della soluzione.

 **Schema della tastiera dinamica** Visual Studio riceve i comandi del tasto di scelta rapida solo quando ha lo stato attivo. Quando il documento di Word ha lo stato attivo, Word riceve tutti i comandi del tasto di scelta rapida. Se, ad esempio, si preme il tasto funzione **F5** mentre il documento di Word ha lo stato attivo, in Word verrà visualizzata la finestra di dialogo **trova e Sostituisci** con la scheda **Vai a** selezionata. Se si preme **F5** mentre Visual Studio ha lo stato attivo, Visual Studio avvia il debug della soluzione.

## <a name="see-also"></a>Vedere anche
- [Tastiera Microsoft Office Excel, impostazioni della tastiera Microsoft Office, finestra di dialogo Opzioni](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)
