---
title: Codifica e caratteri di interruzione di riga
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8fd37547d8107cf35991aab684313dbff37adda0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650890"
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

È possibile usare la finestra di dialogo **File** > **Opzioni di salvataggio avanzate** per determinare il tipo di caratteri di interruzione di riga desiderati. Con le stesse impostazioni è anche possibile modificare la codifica di un file.

![Finestra di dialogo Opzioni di salvataggio avanzate](media/line_endings.png)

> [!NOTE]
> Se il comando **Opzioni di salvataggio avanzate** non è disponibile nel menu **File**, è possibile aggiungerlo. Scegliere **strumenti**, **Personalizza**, quindi fare clic sulla scheda **comandi** . Nell'elenco a discesa **barra dei menu** scegliere **file**, quindi fare clic sul pulsante **Aggiungi comando** . Nella finestra di dialogo **Aggiungi comando**, in **Categorie** scegliere **File** e quindi nell'elenco **Comandi** scegliere  **Opzioni di salvataggio avanzate**. Scegliere **OK** , quindi scegliere il pulsante **Sposta giù** per spostare il comando in qualsiasi posizione nel menu. Scegliere **Chiudi** per chiudere la finestra di dialogo **Personalizza**. Per altre informazioni, vedere [Personalizzazione di un menu o di una barra degli strumenti](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#customizing_menu).
>
> In alternativa, è possibile accedere alla finestra di dialogo **Opzioni di salvataggio avanzate** scegliendo **File** > **Salva \<file\> con nome**. Nella finestra di dialogo **Salva file con nome** scegliere la freccia a discesa accanto al pulsante **Salva** e scegliere **Salva con codifica**.

## <a name="see-also"></a>Vedere anche

- [Funzionalità dell'editor del codice](../ide/writing-code-in-the-code-and-text-editor.md)