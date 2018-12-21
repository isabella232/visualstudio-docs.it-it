---
title: Codifica e caratteri di interruzione di riga
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7acf048b112a88b73c614e8c383722c6e2adb051
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/07/2018
ms.locfileid: "53052009"
---
# <a name="encodings-and-line-endings"></a>Codifiche e interruzioni di riga

I caratteri seguenti vengono interpretati come interruzioni di riga in Visual Studio:

- CR LF: Ritorno a capo + avanzamento riga, caratteri Unicode 000D + 000A

- LF: Avanzamento riga, carattere Unicode 000A

- NEL: Riga successiva, carattere Unicode 0085

- LS: Separatore di riga, carattere Unicode 2028

- PS: Separatore di paragrafo, carattere Unicode 2029

Il testo che viene copiato da altre applicazioni mantiene la codifica e i caratteri originali dell'interruzione di riga. Ad esempio, quando il testo viene copiato da Blocco note e incollato in un file di testo in Visual Studio, il testo mantiene le stesse impostazioni che aveva in Blocco note.

Quando si apre un file con caratteri di interruzione di riga diversi, è possibile che venga visualizzata una finestra di dialogo in cui si chiede se normalizzare i caratteri di interruzione di riga incoerenti e quale tipo di interruzione di riga scegliere.

## <a name="advanced-save-options"></a>Opzioni di salvataggio avanzate

È possibile usare la finestra di dialogo **File** > **Opzioni di salvataggio avanzate** per determinare il tipo di caratteri di interruzione di riga desiderati. Con le stesse impostazioni è anche possibile modificare la codifica di un file.

![Finestra di dialogo Opzioni di salvataggio avanzate](media/line_endings.png)

> [!NOTE]
> Se il comando **Opzioni di salvataggio avanzate** non è disponibile nel menu **File**, è possibile aggiungerlo. Scegliere **Strumenti**, **Personalizza** e quindi scegliere la scheda **Comandi**. Nell'elenco a discesa **Barra dei menu** scegliere **File** e quindi scegliere il pulsante **Aggiungi comando**. Nella finestra di dialogo **Aggiungi comando**, in **Categorie** scegliere **File** e quindi nell'elenco **Comandi** scegliere  **Opzioni di salvataggio avanzate**. Scegliere **OK** e quindi scegliere il pulsante **Sposta giù** per spostare il comando in qualsiasi posizione nel menu. Scegliere **Chiudi** per chiudere la finestra di dialogo **Personalizza**. Per altre informazioni, vedere [Personalizzazione di un menu o di una barra degli strumenti](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#customizing_menu).
>
> In alternativa, è possibile accedere alla finestra di dialogo **Opzioni di salvataggio avanzate** scegliendo **File** > **Salva \<file\> con nome**. Nella finestra di dialogo **Salva file con nome** scegliere la freccia a discesa accanto al pulsante **Salva** e scegliere **Salva con codifica**.

## <a name="see-also"></a>Vedere anche

- [Funzionalità dell'editor del codice](../ide/writing-code-in-the-code-and-text-editor.md)