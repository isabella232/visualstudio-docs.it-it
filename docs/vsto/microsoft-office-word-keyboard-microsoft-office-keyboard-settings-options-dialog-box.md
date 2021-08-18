---
title: Office Tastiera di Word, Impostazioni, finestra di dialogo Opzioni
description: Informazioni su come fare in modo Microsoft Word comandi dei tasti di scelta rapida quando il documento ha lo stato attivo selezionando Schema della tastiera dinamico.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: ec9df6fb069994144503f89808d2b6cf64a14883
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122025940"
---
# <a name="microsoft-office-word-keyboard-settings-options-dialog-box"></a>Microsoft Office Tastiera di Word, Impostazioni, finestra di dialogo Opzioni
  Microsoft Office Word e Visual Studio entrambi gestiscono i tasti di scelta rapida. La stessa combinazione di tasti di scelta rapida può contenere comandi diversi in Word e Visual Studio. Quando Word è aperto in un progetto a livello di documento in Visual Studio, solo un'applicazione alla volta riceve i comandi dei tasti di scelta rapida. Per impostazione predefinita, Visual Studio tutti i comandi dei tasti di scelta rapida, ma è possibile fare in modo che Word li riceva quando il documento ha lo stato attivo selezionando Schema della **tastiera dinamico**.

 Se si usa un tasto di scelta rapida non assegnato a un comando nell'applicazione che attualmente gestisce i tasti di scelta rapida, il tasto di scelta rapida viene passato all'altra applicazione.

 L'opzione selezionata rimarrà attiva per i progetti Word fino a quando non viene cambiata. La selezione non influisce sui Microsoft Office Excel progetto. è necessario apportare qualsiasi modifica per Excel le opzioni Microsoft Office Excel tastiera.

## <a name="uielement-list"></a>Elenco degli elementi di interfaccia
 **Visual Studio combinazione di** tasti Visual Studio tutti i comandi dei tasti di scelta rapida, anche se il documento di Word ha lo stato attivo. Ad esempio, se si preme il tasto **funzione F5** mentre il documento ha lo stato attivo, Visual Studio avvia il debug della soluzione.

 **Lo schema della** tastiera Visual Studio i comandi dei tasti di scelta rapida solo quando ha lo stato attivo. Quando il documento di Word ha lo stato attivo, Word riceve tutti i comandi dei tasti di scelta rapida. Ad esempio, se si preme il tasto **funzione F5** mentre  il documento di Word ha lo stato attivo, Word apre la finestra di dialogo Trova e sostituisci con la **scheda** Vai a selezionata. Se si preme **F5** mentre Visual Studio lo stato attivo, Visual Studio avvia il debug della soluzione.

## <a name="see-also"></a>Vedi anche
- [Microsoft Office Excel tastiera, Microsoft Office tastiera Impostazioni finestra di dialogo Opzioni](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)
