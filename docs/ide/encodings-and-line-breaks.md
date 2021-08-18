---
title: Codifica e caratteri di interruzione di riga
description: Informazioni sui caratteri che Visual Studio interpretano come interruzioni di riga e su come vengono mantenuti i caratteri di codifica e di interruzione di riga originali.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.Encoding
helpviewer_keywords:
- line breaks
- encoding
- Visual Studio, encoding
- editors, line breaks
- line break characters
- Visual Studio, line break characters
ms.assetid: 8f9b3ffc-7b8d-44f4-87cb-dc29105be12d
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: db0efa149538d91c5123f6a973d5e8a455ff2e62
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122094373"
---
# <a name="encodings-and-line-endings"></a>Codifiche e interruzioni di riga

I caratteri seguenti vengono interpretati come interruzioni di riga in Visual Studio:

- CR LF: ritorno a capo + avanzamento riga, caratteri Unicode 000D + 000A

- LF: avanzamento riga, carattere Unicode 000A

- NEL:rRiga successiva, carattere Unicode 0085

- LF: separatore di riga, carattere Unicode 2028

- PS: separatore di paragrafo, carattere Unicode 2029

Il testo che viene copiato da altre applicazioni mantiene la codifica e i caratteri originali dell'interruzione di riga. Ad esempio, quando il testo viene copiato da Blocco note e incollato in un file di testo in Visual Studio, il testo mantiene le stesse impostazioni che aveva in Blocco note.

Quando si apre un file con caratteri di interruzione di riga diversi, è possibile che venga visualizzata una finestra di dialogo in cui si chiede se normalizzare i caratteri di interruzione di riga incoerenti e quale tipo di interruzione di riga scegliere.

## <a name="advanced-save-options"></a>Opzioni di salvataggio avanzate

È possibile usare la finestra di dialogo **Opzioni** di salvataggio avanzate file per  >   determinare il tipo di caratteri di interruzione di riga desiderati. Con le stesse impostazioni è anche possibile modificare la codifica di un file.

![Opzioni di salvataggio avanzate - finestra di dialogo](media/line_endings.png)

> [!NOTE]
> Se il comando **Opzioni di salvataggio avanzate** non è disponibile nel menu **File**, è possibile aggiungerlo. 
> 1. Scegliere **Strumenti**, **Personalizza**, 
> 1. Scegliere la **scheda Comandi,** selezionare il **pulsante di** opzione Barra dei menu e nell'elenco a discesa corrispondente scegliere **File**. Scegliere il **pulsante Aggiungi** comando. 
> 1. Nella finestra di dialogo **Aggiungi comando**, in **Categorie** scegliere **File** e quindi nell'elenco **Comandi** scegliere **Opzioni di salvataggio avanzate**. Scegliere **OK.**
> 1. Usare i **pulsanti Sposta su** e Sposta **giù** per spostare il comando in qualsiasi posizione nel menu. Scegliere **Chiudi** per chiudere la finestra di dialogo **Personalizza**. 
> Per altre informazioni, vedere [Personalizzazione di un menu o di una barra degli strumenti](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#customizing_menu).
>
> In alternativa, è possibile accedere alla finestra di dialogo **Opzioni di** salvataggio avanzate scegliendo Salva **file** con  >  **\<file\> nome**. Nella finestra **di dialogo Salva file** con nome scegliere il triangolo a discesa accanto al pulsante Salva e quindi scegliere Salva con **codifica**. 

## <a name="see-also"></a>Vedi anche

- [Funzionalità dell'editor del codice](../ide/writing-code-in-the-code-and-text-editor.md)
